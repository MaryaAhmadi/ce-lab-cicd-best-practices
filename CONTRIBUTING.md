# Contributing Guide

## Commit Conventions

This repository uses Conventional Commits. All PR titles must follow this format:

type: short description

### Allowed Types

| Type | When to Use | Example |
|------|------------|---------|
| feat | New infrastructure resource | feat: add CloudWatch alarm |
| fix | Bug fix | fix: correct S3 bucket policy |
| docs | Documentation only | docs: update README |
| chore | Maintenance | chore: update provider |
| refactor | Code restructure | refactor: extract module |
| ci | CI/CD changes | ci: add tfsec |
| test | Tests | test: add validation |

## Pull Request Process

1. Create a branch from main
2. Commit with conventional messages
3. Open PR with proper title
4. Ensure CI passes
5. Get approval
6. Squash merge to main

## CI Pipeline Checks

- Terraform Format
- Terraform Validate
- Security Scan (tfsec)
- Terraform Plan

## Deployment

- Push to main triggers CD
- Requires manual approval
- Then terraform apply runs

## Security

- Never commit tfvars with secrets
- Use GitHub Secrets for AWS credentials
