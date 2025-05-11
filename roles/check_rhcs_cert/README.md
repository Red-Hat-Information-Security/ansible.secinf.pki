# deploy_rhcs_cert
Role for RHCS certificate expiration check.

## Role Variables
**Variable** | **Default** | **Description**
--- | --- | ---
gitlab_base_url | '' | The URL of the GitLab instance
rhcs_certificate_management_repo | '' | The repository URL where certificate information is stored
rhcs_certificate_management_repo_name | "rhcs_certificate_management_repo | split('/') | last" | The repository name where certificate information is stored
rhcs_max_valid_months | '11' | Defines the maximum validity period (in months) for a certificate
rhcs_slack_webhook  | '' | The webhook URL used to send messages to a specific Slack channel
rhcs_slack_message | '' | The text content of the Slack alert message
rhcs_pki_cert_repo_branch | '' | (prod / preprod) branch for the certificate repo
aap_url | '' | The URL of the AAP instance




## Example playbooks

```
- hosts: all
  roles:
     - secinf.pki.check_rhcs_cert
```
