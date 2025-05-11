# request_rhcs_cert
Role for RHCS certificate request and retrieval.

## Role Variables
**Variable** | **Default** | **Description**
--- | --- | --- 
rhcs_pki_username | '' | Username for certificate enrollment request
rhcs_pki_password | '' | Password for certificate enrollment request
rhcs_pki_profile | '' | Profile id for certificate enrollment request
rhcs_pki_file_password | '' | Password for PKI client initialization 
rhcs_pki_ca_cert_url | '' | CA certificate url
rhcs_pki_execution_host | '' | Execution host for RHCS request process

## Example playbooks

```
- hosts: all
  roles:
     - secinf.pki.request_rhcs_cert
```
