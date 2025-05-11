# deploy_rhcs_cert
Role for RHCS certificate deployment to host.

## Role Variables
**Variable** | **Default** | **Description**
--- | --- | ---
rhcs_pki_generate_csr_directory | "/root/certs" | | Location for stored certificates on host
rhcs_pki_deploy_cert_directory | "" | Certificate deployment directory (e.g. `/etc/pki/nginx`)
rhcs_pki_deploy_key_directory | "" | Key deployment directory (e.g. `/etc/pki/tls/private`), if different from cert dir
rhcs_pki_deploy_cert_ca_chain_file | 'ca_chain' | Deploy rhcs certificate ca chain file
rhcs_pki_services_to_restart | - | | Prompted services to restart (e.g. `nginx` / `httpd`)
rhcs_pki_cert_extension | 'pem' | Certificate extension (e.g. 'crt'), pem is default

## Example playbooks

```
- hosts: all
  roles:
     - secinf.pki.deploy_rhcs_cert
```
