# Design Decisions

This document records the key engineering decisions made throughout the Cloud Security Engineering Lab. Each decision is documented with its associated problem, decision, rationale, trade-offs, and validation evidence to explain why specific implementation choices were made and how they contribute to the overall security architecture.

---

## DD-001: Protect the Root Account with Multi-Factor Authentication

### Problem

The AWS root account has unrestricted access to all AWS resources. Using the root account for routine administrative activities significantly increases the impact of credential compromise.

### Decision

Enable Multi-Factor Authentication (MFA) on the root account immediately after account creation and reserve the root account exclusively for emergency administrative operations.

### Rationale

This approach aligns with AWS security best practices by strengthening authentication for the most privileged account while reducing operational exposure through the use of IAM identities for day-to-day administration.

### Trade-offs

- Requires an additional authentication step for emergency access.
- Introduces minimal administrative overhead in exchange for significantly improved account security.

### Validation

- Root account protected with MFA.
- Successful login verification using MFA.

---

## DD-002: Use IAM for Daily Administration

### Problem

Performing administrative tasks with the AWS root account violates the principle of least privilege and increases operational risk. In addition, privileged IAM identities require strong authentication to reduce the risk of unauthorized access.

### Decision

Create a dedicated IAM Administrator Group and an IAM Administrator User for routine AWS administration. Protect the privileged IAM user with Multi-Factor Authentication (MFA) and reserve the root account exclusively for emergency administrative operations.

### Rationale

Separating emergency access from daily administration improves accountability, supports centralized permission management, and aligns with AWS security best practices. Enabling MFA for privileged IAM users provides an additional layer of protection against credential compromise.

### Trade-offs

- Requires additional initial configuration.
- Introduces a minor authentication step during sign-in.
- Significantly improves the security posture of privileged administrative access.

### Validation

- Administrator Group created.
- Administrator User created.
- Administrator User added to the Administrators group.
- MFA enabled for the Administrator User.
- Administrative access successfully verified.

---

## DD-003: Establish Cost Governance Before Resource Deployment

### Problem

Cloud resources can incur unexpected costs if spending is not monitored from the outset.

### Decision

Configure AWS Budgets before provisioning compute, storage, or networking resources.

### Rationale

Early cost governance provides visibility into cloud spending, enables proactive budget monitoring, and reduces the likelihood of unexpected charges during project development.

### Trade-offs

- Requires a small amount of initial configuration effort.
- Improves financial visibility throughout the project lifecycle.

### Validation

- AWS Budget successfully configured.
- Budget notifications verified.

---

## DD-004: Validate Programmatic Access Using the AWS CLI

### Problem

Cloud automation depends on secure and authenticated programmatic access. Waiting until later phases to validate CLI access can delay automation and troubleshooting.

### Decision

Configure the AWS CLI using IAM credentials and verify authentication using the AWS Security Token Service (STS).

### Rationale

Early validation ensures the local development environment is correctly configured for future automation, Infrastructure as Code (IaC), and scripting activities.

### Trade-offs

- Requires secure management of local IAM credentials.
- Establishes a reliable foundation for future automation workflows.

### Validation

- AWS CLI configured successfully.
- `aws sts get-caller-identity` executed successfully.
- Authenticated IAM identity confirmed.

---

## DD-005: Build a Custom Virtual Private Cloud (VPC)

### Problem

The AWS Default VPC is designed for convenience and rapid experimentation but provides limited control over network architecture, IP address planning, and security segmentation required for enterprise environments.

### Decision

Create a dedicated custom Virtual Private Cloud (VPC) using a private IPv4 CIDR block (`10.0.0.0/16`) instead of deploying resources into the Default VPC.

### Rationale

A custom VPC provides complete control over network design, subnet allocation, routing, and security boundaries. This approach aligns with enterprise cloud architecture practices and establishes a scalable networking foundation for future workloads and security services.

### Trade-offs

- Requires additional networking configuration compared to using the Default VPC.
- Introduces greater implementation complexity.
- Provides significantly improved flexibility, scalability, and security.

### Validation

- Custom VPC successfully created.
- IPv4 CIDR block configured.
- VPC available for subsequent networking components.

---

## DD-006: Separate Public and Private Network Segments

### Problem

Hosting all workloads within a single network segment increases the attack surface and does not support secure multi-tier application architectures.

### Decision

Implement separate Public and Private Subnets within the custom VPC.

### Rationale

Network segmentation enables internet-facing resources to be isolated from internal workloads while supporting future deployment of databases, application servers, and management services within private network segments.

### Trade-offs

- Requires additional subnet planning and routing configuration.
- Slightly increases networking complexity.
- Significantly improves security, scalability, and architectural flexibility.

### Validation

- Public Subnet successfully created.
- Private Subnet successfully created.
- Both subnets validated within the custom VPC.

---

## DD-007: Control Internet Connectivity Through Explicit Routing

### Problem

Internet connectivity should be explicitly controlled rather than implicitly available to all network resources.

### Decision

Attach an Internet Gateway to the custom VPC and configure a dedicated Public Route Table containing a default route (`0.0.0.0/0`) to the Internet Gateway. Associate only the Public Subnet with this Route Table.

### Rationale

Explicit routing ensures that only designated public workloads have internet connectivity while preserving network isolation for private resources. This follows the principle of least privilege and reflects enterprise networking practices.

### Trade-offs

- Requires additional routing configuration.
- Increases deployment complexity compared to the Default VPC.
- Provides precise control over network exposure.

### Validation

- Internet Gateway successfully attached.
- Public Route Table created.
- Default route configured.
- Public Subnet successfully associated with the Public Route Table.

---

## DD-008: Protect Compute Resources Using Dedicated Security Groups

### Problem

Compute instances require network-level access control to limit inbound connectivity and reduce the attack surface.

### Decision

Create a dedicated Security Group for the EC2 instance, permitting only the required inbound traffic while allowing outbound connectivity for system administration and software installation.

### Rationale

Security Groups provide stateful instance-level firewall protection and enable fine-grained access control independent of subnet-level routing. This approach supports least privilege and simplifies future security policy management.

### Trade-offs

- Requires ongoing rule management as services are introduced.
- Improves security by minimizing unnecessary network exposure.

### Validation

- Security Group successfully created.
- SSH and HTTP access validated.
- EC2 instance successfully associated with the Security Group.

---

## DD-009: Validate Infrastructure Through End-to-End Connectivity

### Problem

Successful infrastructure provisioning alone does not verify that networking, routing, security controls, and compute services are functioning together correctly.

### Decision

Deploy an Amazon Linux EC2 instance, install the Apache HTTP Server, and validate end-to-end browser connectivity using the instance's public IP address.

### Rationale

End-to-end validation confirms that the networking architecture, routing configuration, security controls, and compute platform operate together as intended. This provides confidence before introducing additional cloud security services in subsequent labs.

### Trade-offs

- Requires temporary deployment of a publicly accessible workload.
- Provides practical validation of the complete networking implementation.

### Validation

- Amazon Linux EC2 instance successfully deployed.
- Apache HTTP Server installed and started.
- HTTP connectivity successfully validated through a web browser.