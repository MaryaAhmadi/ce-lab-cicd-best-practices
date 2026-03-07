# Pipeline Documentation

## CI Pipeline

- **Trigger:** Pull Request to `main`
- **Steps:**
  1. Terraform format check
  2. Terraform validate
  3. Security scan (tfsec)
  4. Terraform plan (commented in PR)

## CD Pipeline

- **Trigger:** Push to `main`
- **Steps:**
  1. Terraform plan
  2. Manual approval in production environment
  3. Terraform apply after approval

## Release Automation

- Managed by [release-please](https://github.com/googleapis/release-please)
- Generates release PRs and tags
- Updates `version.txt` automatically
