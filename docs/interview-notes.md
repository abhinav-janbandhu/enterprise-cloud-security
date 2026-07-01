# Interview Notes

This document captures common interview questions and concise answers based on the implementation of the Cloud Security Engineering Lab. The objective is to reinforce technical understanding while building a practical interview preparation guide from real engineering experience.

---

## Lab 31 – AWS Security Foundation

### Q1. Why should the AWS root account not be used for daily administration?

**Answer**

The AWS root account has unrestricted access to all AWS services and resources. Using it for routine administration significantly increases the impact of credential compromise. AWS recommends securing the root account with Multi-Factor Authentication (MFA) and performing day-to-day administrative tasks using IAM identities.

---

### Q2. Why is Multi-Factor Authentication (MFA) important for the root account?

**Answer**

Multi-Factor Authentication (MFA) adds an additional layer of authentication beyond a password, significantly reducing the risk of unauthorized access if credentials are compromised. Because the root account has unrestricted privileges, MFA is considered a critical security control.

---

### Q3. What is the difference between the AWS root user and an IAM user?

**Answer**

The AWS root user is created when an AWS account is established and has unrestricted access to all AWS resources. IAM users are created within the AWS account and receive permissions through IAM policies, allowing access to be managed according to the principle of least privilege.

---

### Q4. Why should AWS Budgets be configured before deploying resources?

**Answer**

Configuring AWS Budgets at the beginning of a project provides visibility into cloud spending and enables early notification of unexpected costs. Establishing cost governance before deploying resources helps maintain financial control as the cloud environment grows.

---

### Q5. Why use the AWS CLI when the AWS Management Console is available?

**Answer**

The AWS Management Console is designed for interactive administration, while the AWS CLI enables automation, scripting, repeatable operations, and integration with Infrastructure as Code (IaC) workflows. Both interfaces complement each other in enterprise cloud environments.

---

### Q6. What does the `aws sts get-caller-identity` command verify?

**Answer**

The `aws sts get-caller-identity` command returns the AWS account ID, IAM user or role ARN, and the unique user identifier associated with the current credentials. It is commonly used to verify that the AWS CLI is correctly configured and authenticating successfully.

---

### Q7. What security principle is demonstrated by creating an IAM Administrator Group?

**Answer**

Creating an IAM Administrator Group supports centralized permission management and the principle of least privilege. Permissions are assigned to the group rather than individual users, simplifying administration, improving consistency, and reducing the risk of permission management errors.

---

### Q8. Should privileged IAM users also use Multi-Factor Authentication (MFA)?

**Answer**

Yes. AWS recommends enabling Multi-Factor Authentication (MFA) for privileged IAM users in addition to the root account. Administrative IAM users have significant permissions, and MFA provides an additional layer of protection against credential compromise. Protecting both the root account and privileged IAM identities strengthens the overall security posture of the AWS environment.

---

## Key Takeaways

- Secure privileged accounts before deploying infrastructure.
- Separate emergency access from operational administration.
- Establish governance early through IAM and AWS Budgets.
- Validate programmatic access before implementing automation.
- Build cloud environments on a security-first foundation.