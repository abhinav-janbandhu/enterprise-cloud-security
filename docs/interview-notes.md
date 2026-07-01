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

## Lab 32 – AWS Networking Fundamentals

### Q1. What is an Amazon VPC?

**Answer**

An Amazon Virtual Private Cloud (VPC) is a logically isolated virtual network within AWS where cloud resources are deployed. It allows organizations to define their own IP address ranges, create subnets, configure routing, and apply network security controls while remaining isolated from other AWS customers.

---

### Q2. Why are subnets used within a VPC?

**Answer**

Subnets divide a VPC into smaller network segments. They allow resources with different security requirements to be separated, improve network organization, and enable controlled routing between application tiers such as web, application, and database servers.

---

### Q3. What is the difference between a public subnet and a private subnet?

**Answer**

A public subnet has a route to an Internet Gateway, allowing resources such as web servers to receive internet traffic. A private subnet has no direct internet route and is typically used for databases, internal applications, and sensitive workloads that should not be directly accessible from the internet.

---

### Q4. What is an Internet Gateway (IGW)?

**Answer**

An Internet Gateway is a highly available AWS-managed component that enables communication between resources in a VPC and the public internet. A subnet becomes public only when its route table includes a route to the Internet Gateway.

---

### Q5. What is a Route Table?

**Answer**

A Route Table contains rules that determine where network traffic is directed. Each subnet is associated with a route table that specifies whether traffic should remain within the VPC or be forwarded to destinations such as an Internet Gateway, NAT Gateway, or Virtual Private Gateway.

---

### Q6. What is the purpose of a Security Group?

**Answer**

A Security Group acts as a virtual firewall attached to AWS resources such as EC2 instances. It controls inbound and outbound traffic using allow rules and is stateful, meaning return traffic for permitted connections is automatically allowed.

---

### Q7. What is the difference between a Security Group and a Network ACL?

**Answer**

Security Groups operate at the instance level, are stateful, and support only allow rules. Network ACLs operate at the subnet level, are stateless, and support both allow and deny rules, providing an additional layer of network security.

---

### Q8. Why is CIDR notation important in AWS networking?

**Answer**

CIDR notation defines IP address ranges used by VPCs and subnets. Proper CIDR planning prevents overlapping networks, supports future expansion, and enables effective routing between AWS environments and on-premises networks.

---

### Q9. Why should databases typically be placed in private subnets?

**Answer**

Databases generally do not require direct internet access. Placing them in private subnets reduces the attack surface, limits exposure to external threats, and supports defense-in-depth by requiring application servers to communicate with the database internally.

---

### Q10. How does network segmentation improve cloud security?

**Answer**

Network segmentation isolates workloads based on their function and security requirements. By separating public-facing services from internal applications and databases, organizations reduce lateral movement opportunities for attackers and enforce least-privilege network access.

---

## Key Takeaways

### Lab 31 – AWS Security Foundation

- Secure privileged accounts before deploying infrastructure.
- Separate emergency access from operational administration.
- Establish governance early through IAM and AWS Budgets.
- Validate programmatic access before implementing automation.
- Build cloud environments on a security-first foundation.

---

### Lab 32 – AWS Networking Fundamentals

- Design VPCs with future scalability in mind.
- Separate workloads using public and private subnets.
- Control traffic using route tables and Internet Gateways.
- Apply defense-in-depth using Security Groups and Network ACLs.
- Plan CIDR ranges carefully to avoid future networking conflicts.
- Network segmentation is a foundational cloud security control.