# Cloud Security Engineering Lab

An enterprise-style cloud security engineering project that designs, implements, and validates a secure AWS environment using security-first engineering principles.

This repository demonstrates the work of a cloud security engineer responsible for designing, securing, and continuously improving an AWS environment. Every implementation is driven by a defined security objective, supported by documented architectural decisions, and validated through reproducible evidence.

Rather than treating AWS as a collection of isolated services or tutorials, the project develops a secure cloud environment through successive engineering capabilities. Beginning with identity and account security, it progressively expands to networking, governance, monitoring, logging, detection engineering, infrastructure as code, and security automation. Each capability includes its design rationale, implementation approach, security benefits, and validation evidence.

The result is a living engineering project that reflects how secure cloud environments are designed, implemented, validated, and continuously improved using enterprise security practices.

---

# Security Problem Statement

Cloud providers deliver secure building blocks, but secure cloud environments are not created by default. Misconfigured identities, excessive permissions, weak governance, insecure network configurations, and limited operational visibility remain among the leading causes of cloud security incidents.

This project addresses those challenges by designing a secure AWS environment from first principles. Every security control is intentionally implemented to reduce risk, enforce least privilege, improve governance, and establish a scalable security foundation. Each implementation is treated as an engineering decision rather than a configuration task, with documented design choices and validation evidence demonstrating that the controls operate as intended.

---

# Project Objectives

The objective of this project is to build and continuously evolve a secure AWS environment using enterprise cloud security engineering practices. Each implementation contributes to a production-style security foundation rather than an isolated technical exercise.

The project is guided by the following engineering objectives:

- Design secure cloud infrastructure using security-first architectural principles.
- Implement identity, governance, access control, and network security that reduce operational risk.
- Build security controls that are measurable, repeatable, and automated where appropriate.
- Validate every implementation using AWS CLI output, configuration artifacts, architecture diagrams, and supporting evidence.
- Document not only what was implemented, but why each design decision was made and how it strengthens the overall security posture.
- Continuously expand the environment with compute security, monitoring, logging, detection engineering, infrastructure as code, and security automation.

---

# Architecture Overview

The project is built as a secure AWS environment that evolves through incremental implementation of enterprise cloud security capabilities. Each new capability extends the existing architecture while preserving a security-first design.

The current implementation establishes the security and networking foundation of the AWS environment. It includes identity management, Multi-Factor Authentication (MFA), cost governance, authenticated programmatic access through the AWS CLI, and a custom Amazon Virtual Private Cloud (VPC) with segmented public and private subnets, controlled internet connectivity, and layered network security.

These foundational capabilities provide the baseline required before introducing compute resources, centralized logging, monitoring, compliance, threat detection, infrastructure as code, and security automation.

## High-Level Architecture

The diagram below illustrates the current AWS security and networking foundation implemented in this repository.

**Current Implementation (Labs 31–32 – Security & Networking Foundation)**

<p align="center">
  <img src="diagrams/cloud-security-architecture.png" alt="Cloud Security Engineering Architecture" width="900">
</p>

*Figure 1. Current architecture showing the security and networking foundation established through Labs 31–32. Future labs will extend this environment with secure compute, centralized logging, monitoring, compliance, threat detection, infrastructure as code, and security automation.*

---

# Implemented Security Capabilities

The following security capabilities establish the current security foundation of the AWS environment. Each capability addresses a specific security objective and is validated through documented configuration, AWS CLI output, architecture artifacts, or supporting implementation evidence.

| Security Capability | Security Objective | Status | Validation |
|---------------------|--------------------|:------:|------------|
| AWS Account Security Foundation | Establish a secure AWS environment for cloud security engineering. | ✅ Complete | AWS Account Configuration Verified |
| Root Account Protection | Protect the privileged root account using Multi-Factor Authentication (MFA). | ✅ Complete | MFA Enabled & Verified |
| Identity & Access Management | Enforce least-privilege administration through dedicated IAM identities protected with Multi-Factor Authentication (MFA). | ✅ Complete | IAM Console & AWS CLI Verified |
| Cost Governance | Monitor and control cloud spending using AWS Budgets. | ✅ Complete | Budget Alerts Configured |
| Authenticated AWS CLI Access | Enable secure, authenticated programmatic access using IAM credentials. | ✅ Complete | Successful Authenticated AWS CLI API Call |
| AWS Network Security Foundation | Build a secure, segmented cloud network using Amazon VPC, public and private subnets, route tables, and controlled internet connectivity. | ✅ Complete | VPC Topology Validated |

---

# Repository Structure

The repository is organized to separate architecture, implementation, automation, validation evidence, and supporting documentation. This structure keeps the project maintainable as new cloud security capabilities are introduced while ensuring that engineering decisions, implementation artifacts, and validation evidence remain organized and easy to navigate.

```text
cloud-security-engineering-lab/
├── assets/         # Repository assets used by the documentation
├── diagrams/       # Cloud architecture and design diagrams
├── docs/           # Engineering documentation and design decisions
├── labs/           # Lab implementations and configuration guides
├── screenshots/    # Validation evidence for implemented security controls
├── scripts/        # Automation and utility scripts
├── templates/      # Reusable configuration and documentation templates
└── README.md       # Project overview and repository navigation
```