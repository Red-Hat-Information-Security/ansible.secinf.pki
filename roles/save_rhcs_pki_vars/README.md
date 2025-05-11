# deploy_rhcs_cert
Role for saving rhcs pki vars to an inventory.

## Role Variables
**Variable** | **Default** | **Description**
--- | --- | ---
rhcs_certificate_management_repo | '' | The repository path where certificate information is stored
rhcs_certificate_management_repo_name | rhcs_certificate_management_repo | split('/')  | last | The repository name where certificate information is stored
rhcs_inventory_repo | '' | The inventory path where pki vars will be stored


## Example playbooks

```
- hosts: all
  roles:
     - secinf.pki.save_rhcs_pki_vars
```
