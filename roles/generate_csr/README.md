# generate_csr
Role for CSR generation.

## Role Variables
**Variable** | **Default** | **Description**
--- | --- | --- 
rhcs_pki_generate_csr_common_name | '' | CN
rhcs_pki_generate_csr_directory | '/root/certs' | Location for stored certificates on host
rhcs_pki_generate_csr_file_name_stub | "{{ inventory_hostname | split('.') | first }}" | Stub naming for generated files (e.g. `aap` ~> `aap.key` / `aap.csr`)
rhcs_pki_generate_csr_key_curve | 'secp384r1' | Curve for private key
rhcs_pki_generate_csr_force_new_key | false | Force regenerate private key
rhcs_pki_cnames | - | Prompted additional CNAMEs for certificate
rhcs_certificate_management_repo | '' | The repository path where certificate information is stored
rhcs_certificate_management_repo_name | "{{ rhcs_certificate_management_repo | split('/') | last }}" | The repository name where certificate information is stored
rhcs_pki_cert_repo_branch | '' | (prod / preprod) branch for the certificate repo

## Example playbooks

```
- hosts: all
  roles:
     - secinf.pki.generate_csr
```
