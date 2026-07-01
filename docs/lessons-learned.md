# Lessons Learned

This document captures the key technical and operational lessons learned throughout the Cloud Security Engineering Lab. These lessons summarize practical insights gained during implementation and help guide future engineering decisions, security practices, and cloud deployments.

---

## LL-001: Secure the Root Account First

The AWS root account is the most privileged identity within an AWS environment and should be secured immediately after account creation. Enabling Multi-Factor Authentication (MFA) before performing any additional configuration significantly reduces the risk of unauthorized access.

---

## LL-002: Protect All Privileged Identities

Securing the root account alone is not sufficient. Privileged IAM users should also be protected with Multi-Factor Authentication (MFA). Combining IAM-based administration with MFA strengthens identity security while maintaining a clear separation between emergency and operational access.

---

## LL-003: Establish Cost Governance Early

Implementing AWS Budgets before deploying cloud resources provides immediate visibility into spending and reduces the likelihood of unexpected costs as the environment grows. Early financial governance is an important component of secure cloud operations.

---

## LL-004: Validate Programmatic Access Early

Configuring and validating the AWS CLI at the beginning of the project ensures that future automation, scripting, and Infrastructure as Code (IaC) workflows can be implemented without interruption.

---

## LL-005: Build Security Before Infrastructure

Security controls should be established before deploying workloads. Identity management, privileged access protection, governance, and secure administrative access form the foundation upon which all future cloud services should be built.

---

## LL-006: Design Network Architecture Before Deploying Resources

A well-planned Virtual Private Cloud (VPC) provides the foundation for secure cloud networking. Defining IP address ranges, subnet structure, and routing before deploying resources simplifies future expansion and reduces the need for disruptive network redesigns.

---

## LL-007: Use Network Segmentation to Reduce Risk

Separating workloads into public and private subnets minimizes the attack surface by restricting direct internet exposure. Network segmentation is a fundamental security practice that supports defense-in-depth and limits the impact of potential compromises.

---

## LL-008: Understand How Traffic Flows Through a VPC

Resources become publicly accessible only when multiple networking components work together, including subnets, route tables, and an Internet Gateway. Understanding how these components interact is essential for troubleshooting connectivity issues and preventing unintended exposure.

---

## LL-009: Apply Multiple Layers of Network Security

AWS networking uses multiple security controls that complement one another. Security Groups provide instance-level traffic filtering, while Network ACLs provide subnet-level filtering. Using both appropriately strengthens the overall security posture of the environment.

---

## LL-010: Plan IP Addressing for Future Growth

Careful CIDR planning prevents overlapping IP address ranges and supports future scalability, hybrid connectivity, and multi-VPC architectures. Investing time in network planning early reduces operational complexity as cloud environments expand.