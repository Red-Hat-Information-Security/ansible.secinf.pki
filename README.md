
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
## Contribution guide
1. Clone.
3. Make desired additional changes.
4. Elevate version in **galaxy.yml**.
5. Create a changelog fragment with changes.
6. `antsibull-changelog release`
9. Commit changes to git.
