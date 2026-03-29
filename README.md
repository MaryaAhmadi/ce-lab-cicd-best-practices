# Lab M5.10 - CI/CD Best Practices Implementation

https://github.com/MaryaAhmadi/ce-lab-cicd-best-practices.git


**Cloud Engineering Bootcamp - Week 5, Day 5**  
**Module:** Cloud Automation & CI/CD

---

## 📋 Overview

This repository demonstrates a **production-grade CI/CD pipeline** for Infrastructure as Code using Terraform.

It provisions and manages shared cloud infrastructure resources while enforcing best practices such as:

- ✅ Automated testing and validation
- 🔐 Security scanning
- 📦 Semantic versioning and automated releases
- 🚦 CI/CD pipelines with approval gates
- 📖 Documentation and team conventions

---

## 🏗️ Architecture

This project manages the following AWS resources:

### 🔹 S3 Bucket (Artifacts Storage)
- Versioning enabled
- Server-side encryption (AES256)
- Lifecycle rules for cost optimization
- Public access blocked

### 🔹 DynamoDB Table (Application State)
- PAY_PER_REQUEST billing
- Point-in-time recovery enabled
- Server-side encryption enabled
- Composite primary key (PK, SK)

---

## ⚙️ CI/CD Workflows

| Workflow | Trigger | Purpose |
|----------|--------|--------|
| **CI Pipeline** | Pull Request → `main` | Format, validate, security scan, plan |
| **CD Pipeline** | Push → `main` | Plan + deploy with manual approval |
| **Commit Lint** | PR open/edit | Enforce conventional commits |
| **Release Please** | Push → `main` | Automated versioning and changelog |

---

## 🔍 CI Pipeline Stages

The CI pipeline ensures code quality before deployment:

1. **Terraform Format**
   - Enforces consistent formatting

2. **Terraform Validate**
   - Checks syntax and configuration correctness

3. **Security Scan (tfsec)**
   - Detects misconfigurations and vulnerabilities

4. **Terraform Plan**
   - Shows infrastructure changes before deployment
   - Automatically posted as a PR comment

---

## 🚀 CD Pipeline

- Triggered after merge to `main`
- Runs Terraform plan
- Requires **manual approval** via GitHub Environment (`production`)
- Executes Terraform apply after approval

---

## 🔐 Security Practices

- No secrets stored in repository
- AWS credentials managed via GitHub Secrets
- S3 buckets:
  - Encryption enabled
  - Public access blocked
- DynamoDB:
  - Encryption enabled
  - Point-in-time recovery enabled
- tfsec used for static security analysis

---

## 📦 Versioning & Releases

This repository uses:

- **Conventional Commits**
- **release-please**

Features:
- Automatic version bumping
- Changelog generation
- GitHub release creation

Example:

feat: add DynamoDB TTL support


---

## 🧪 Local Development

Run Terraform locally:

```bash
cd terraform
terraform init
terraform plan
terraform apply

## Contributing
See CONTRIBUTING.md for:
Commit message conventions
Pull request process
CI/CD guidelines

## 📄 Incident Management
In case of deployment failures, use:
👉 docs/POSTMORTEM_TEMPLATE.md
This ensures:
Root cause analysis
Timeline tracking
Continuous improvement

## 📊 Repository Structure
.
├── .github/workflows/     # CI/CD pipelines
├── terraform/             # Infrastructure as Code
├── docs/                  # Documentation & postmortems
├── CONTRIBUTING.md        # Team conventions
├── README.md              # Project documentation
├── CHANGELOG.md           # Auto-generated releases
└── version.txt            # Version tracking


## 🎯 Key Takeaways
CI pipelines prevent broken infrastructure changes
CD pipelines with approval gates reduce risk
Conventional commits enable automation
Documentation improves team collaboration
Security should be integrated from day one


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
