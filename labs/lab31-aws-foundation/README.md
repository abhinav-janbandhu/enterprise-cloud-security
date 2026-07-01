# Lab 31 – AWS Security Foundation

## Overview

This lab establishes the foundational security controls for the Cloud Security Engineering Lab by securing a newly created AWS account and implementing identity, governance, and authenticated administrative access.

Rather than provisioning workloads immediately, the lab focuses on building a secure operational baseline that aligns with AWS security best practices. These foundational controls provide the platform on which all subsequent cloud security capabilities will be implemented.

---

## Objectives

- Secure the AWS root account using Multi-Factor Authentication (MFA).
- Implement IAM-based administration following the principle of least privilege.
- Configure AWS Budgets for proactive cost governance.
- Establish secure programmatic access using the AWS CLI.
- Validate all implemented controls through AWS console configuration and AWS CLI verification.

---

## Implemented Components

- AWS Account
- Root Account Protection (Multi-Factor Authentication)
- AWS Identity and Access Management (IAM)
  - Administrator Group
  - Administrator User
- AWS Budgets
- AWS CLI
- AWS Security Token Service (STS)

---

## Implementation Summary

| Component | Purpose | Status |
|-----------|---------|:------:|
| AWS Account | Establish the cloud environment | ✅ |
| Root MFA | Protect the most privileged account | ✅ |
| IAM Administration | Enable least-privilege administrative access | ✅ |
| AWS Budgets | Establish cost governance | ✅ |
| AWS CLI | Enable authenticated programmatic administration | ✅ |
| AWS STS Validation | Verify authenticated CLI access | ✅ |

---

## Validation Evidence

Implementation was validated using the following evidence:

- AWS Management Console configuration
- Root account MFA verification
- IAM Administrator Group and User configuration
- AWS Budgets configuration
- Successful execution of `aws sts get-caller-identity`

Supporting screenshots are available in:

```text
screenshots/
├── 01-account-foundation/
├── 02-identity-access-management/
├── 03-cost-governance/
└── 04-aws-cli/
```

---

## Key Engineering Decisions

The following engineering decisions were established during this lab:

- Protect privileged identities before deploying cloud resources.
- Perform routine administration using IAM identities instead of the root account.
- Establish governance before provisioning infrastructure.
- Validate programmatic access early to support future automation.

Detailed design rationale is available in:

- `docs/design-decisions.md`

---

## Documentation

Additional documentation for this implementation is available in:

- `docs/architecture.md`
- `docs/design-decisions.md`
- `docs/interview-notes.md`
- `docs/lessons-learned.md`

---

## Outcome

Lab 31 establishes the secure foundation for the Cloud Security Engineering Lab. With identity management, governance, and authenticated administrative access in place, the environment is prepared for the implementation of secure networking, logging, monitoring, detection engineering, Infrastructure as Code, and security automation in subsequent labs.