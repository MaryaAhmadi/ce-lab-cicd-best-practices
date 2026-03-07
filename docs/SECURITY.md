# Security and Compliance

## Policies

- All S3 buckets must have encryption and public access blocks
- DynamoDB tables must enable encryption and point-in-time recovery

## CI Security Checks

- tfsec for infrastructure misconfigurations
- Secret scanning in GitHub Actions
- License compliance checks
- Code quality validation

## Recommendations

- Never commit `.tfvars` with real secrets
- Use GitHub Secrets for AWS credentials
