# Lab M5.10 - CI/CD Best Practices Implementation

**Cloud Engineering Bootcamp - Week 5, Day 5**  
**Module:** Cloud Automation & CI/CD

## Start Here: Fork, Clone, and Submit    

You will complete this lab by working in **your own fork** of the lab repository and submitting a **Pull Request (PR)**.

1. **Fork the lab repository** to your GitHub account.
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/<your-github-username>/ce-lab-cicd-best-practices.git
   cd ce-lab-cicd-best-practices
   ```
3. **Follow all instructions below** and save your work in this repo (files, screenshots, and notes).
4. **When finished, submit your work:**
   - `git add` → `git commit` → `git push`
   - Open a **Pull Request** from your fork back to the original lab repo
   - Copy the **PR URL** and paste it into the **Lab Submission** field in the Student Portal

## 📋 Lab Overview

n this lab, you will implement production-ready CI/CD pipelines using Terraform and GitHub Actions, following industry best practices for:
Infrastructure as code
Automated testing and validation
Security and compliance
Monitoring and auditing
Documentation


## 🎯 Learning Objectives

By the end of this lab, you will be able to:

Implement comprehensive CI/CD pipelines with multi-stage testing
Configure security scanning and compliance checks
Set up monitoring and observability for infrastructure changes
Implement audit logging for all deployments
Document CI/CD processes, runbooks, and architecture
Follow industry best practices for infrastructure management


## 📁 Repository Structure

```
ce-lab-cicd-best-practices/
├── .github/
│   └── workflows/
│       ├── comprehensive-ci.yml
│       ├── security-scan.yml
│       ├── compliance-check.yml
│       └── monitoring.yml
├── docs/
│   ├── PIPELINE.md
│   ├── SECURITY.md
│   └── RUNBOOK.md
├── tests/
├── README.md
└── .gitignore
```

CI/CD Workflows

Workflow	 |. Trigger	| Purpose
CI Pipeline |	PR to main	|Run format checks, validate Terraform, security scan (tfsec), Terraform plan
CD Pipeline| 	Push to main	| Plan + deploy with manual approval in production
Commit Lint |	PR open/edit	| Ensure PR titles follow conventional commit standard
Release Please	|Push to main	| Automated semantic versioning and changelog generation


# Clone your fork
git clone https://github.com/<your-github-username>/ce-lab-cicd-best-practices.git
cd ce-lab-cicd-best-practices

# Initialize Terraform
cd terraform
terraform init

# Preview infrastructure changes
terraform plan

# Apply infrastructure (production approval required for CD)
terraform apply




## Architecture Overview 

This repository manages shared infrastructure resources:
S3 Bucket — Versioned artifact storage with server-side encryption, lifecycle policies, and public access block
DynamoDB Table — Application state store with point-in-time recovery, encryption, and high availability




## Contributing Guide  

This repository follows Conventional Commits:

type: short description

Allowed Commit Types


Type.  |	When to Use	|Example
feat	   | New infrastructure resource	|feat: add CloudWatch alarm for DynamoDB
fix	    |Bug fix or misconfiguration	| fix: correct S3 bucket policy permissions
docs	     |Documentation only	   |docs: update architecture diagram
chore	 |Maintenance, dependencies	| chore: update Terraform provider to 5.30
refactor	  |Code restructuring, no behavior change	  |refactor: extract S3 config into module
ci	     |CI/CD workflow changes	   |ci: add tfsec to PR checks
test	     |Adding or updating tests	| test: add validation for DynamoDB schema


## Pull Request Process

- Create a feature branch: git checkout -b feat/your-feature
- Make changes and commit with conventional messages
- Push and open a PR: feature branch → main
- CI pipeline runs automatically (must pass all checks)
- Obtain at least one reviewer approval
- Squash merge into main
- CD pipeline runs with manual approval in production


## CI Pipeline Checks
Every PR must pass these before merging:

- Terraform Format — terraform fmt -check
- Terraform Validate — terraform validate
- Security Scan — tfsec scans for misconfigurations
- Terraform Plan — outputs posted as PR comment

## Deployment
Merges to main trigger CD pipeline:

- Automatic terraform plan
- Manual approval required in production environment
- terraform apply executes after approval

## Security & Compliance
- Never commit .tfvars files with sensitive values
- Use GitHub Secrets for AWS credentials
-All S3 buckets must have encryption and public access block
- DynamoDB tables must enable encryption and point-in-time recovery
- Pipeline includes vulnerability and secret scanning, license compliance, and 
code quality checks

## Postmortem & Troubleshooting
- Use docs/POSTMORTEM_TEMPLATE.md to document incidents
- Include root cause, impact, timeline, and resolution
- Maintain runbooks for common rollback scenarios (docs/RUNBOOK.md)





## ✅ Submission Requirements

1. **Comprehensive CI/CD Pipeline**
   - Multi-stage testing (unit, integration, e2e)
   - Security scanning (SAST, dependency check)
   - Compliance validation
   - Automated deployment

2. **Security Implementation**
   - Vulnerability scanning
   - Secret scanning
   - Code quality checks
   - License compliance

3. **Monitoring & Observability**
   - Pipeline metrics
   - Deployment notifications
   - Error alerting

4. **Documentation**
   - Pipeline architecture diagram
   - Runbooks and troubleshooting guides
   - Security and compliance documentation

## 🎓 Grading Rubric

| Criteria | Points |
|----------|--------|
| **Pipeline Completeness** | 30 |
| **Security Implementation** | 25 |
| **Monitoring & Alerts** | 20 |
| **Documentation** | 25 |
| **Total** | 100 |

## 💡 Tips

- Start with a working pipeline, then add features
- Implement security checks early
- Document as you build
- Use pipeline templates for consistency
- Monitor pipeline metrics continuously

## 📚 Resources

- [GitHub Actions Security Best Practices](https://docs.github.com/en/actions/security-guides)
- [CI/CD Best Practices](https://about.gitlab.com/topics/ci-cd/ci-cd-best-practices/)
- [OWASP CI/CD Security](https://owasp.org/www-project-devsecops-guideline/)

## 🚀 Submission

Complete the lab as described in the instructions and save your work in this repo (files, screenshots, notes, etc.).

**Reminder:** After pushing your work and opening a PR:
- Copy the **PR URL**
- Paste it into the **Lab Submission** field in the Student Portal

---

**Congratulations!** This is the final lab of Week 5. You've learned comprehensive CI/CD automation practices that are essential for modern cloud engineering. Apply these practices in all your future projects!