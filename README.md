Ansible collection for automated certificates management

## User guide

## Features

- CSR generation 
- Request and retrieve certificates from RHCS
- Deploy renewed certificates to custom destinations
- Monitoring of certificate expiration
- Slack integration for expiration alerts
- Modular roles and playbooks for easy integration with existing automation
- Built to run on Ansible Automation Platform

### Short overview 
This collectioin includes the following roles:
  1.  generate_csr role to create a new CSR.
  2.  request_rhcs_cert role to request a new certificate from RHCS.
  3.  deploy_rhcs_cert role to deploy the new certificate and key.
  4.  save_rhcs_pki_vars role to save survey vars to the inventory.
  5.  check_rhcs_cert role to check expiried certificates.

### Collection requirements
- ansible.posix
- secinf.utils

## Code Quality and Linting

This project uses `ansible-lint` for static analysis of Ansible playbooks and roles to enforce best practices and identify potential issues.

To run the linter locally, you can use the following commands from the root of the repository:
```bash
ansible-lint .
```
Or, to lint specific roles:
```bash
ansible-lint roles/
```

**Note:** For full validation of tasks using custom modules from the `secinf.utils` collection (e.g., `secinf.utils.git_acp`), ensure this collection is installed and accessible in your Ansible environment. The linter may show warnings if it cannot find this collection, which could prevent it from fully validating tasks that depend on these custom modules.

## Testing

An attempt was made to set up role-level testing using Molecule with the Docker driver for the `generate_csr` role as an initial example.

However, this effort was blocked by persistent and critical inconsistencies in the file system representation as perceived by the execution environment's tools. These issues prevented the reliable creation and modification of necessary Molecule configuration files (e.g., `molecule.yml`, `converge.yml`).

Further investigation into the execution environment's behavior with file system operations would be required to implement a full Molecule testing suite. Without a stable environment for file manipulation, comprehensive automated testing for the roles could not be established during this phase.

## Performance Review Summary

A general review of the Ansible roles within this collection was conducted to identify common Ansible performance anti-patterns and suggest improvements. The primary goal was to enhance efficiency, idempotency, and maintainability.

The most common recommendation across multiple roles is to **replace generic `command` or `shell` module calls with specific, idempotent Ansible modules where available.** This practice generally leads to more reliable, readable, and maintainable automation.

Summary of roles reviewed:
-   `generate_csr`: Several opportunities identified to use specific crypto and file modules instead of `command` module calls for OpenSSL operations and file manipulation.
-   `check_rhcs_cert`: Opportunities noted to replace `command`/`shell` modules (used for `cat`, `rm -rf`, and Python date calculations) with dedicated Ansible modules like `slurp`, `file`, and potentially Ansible/Jinja2 filters for date logic.
-   `deploy_rhcs_cert`: Opportunities identified to replace `command` modules (used for `cat`, `mkdir -p`, `ls`, `restorecon`) with specific modules such as `slurp`, `file`, and SELinux context management features in other modules.
-   `request_rhcs_cert`: Showed heavy reliance on the `command` module for interacting with the `pki` command-line tool. If dedicated Ansible modules for this PKI system exist, they would be preferable. Also, use of `command` for `cat` and `lookup('pipe', 'date')` were noted.
-   `save_rhcs_pki_vars`: Found to be generally well-structured, using appropriate modules for most operations, with only minor suggestions (e.g., replacing `lookup('pipe', 'date')` for timestamps).
