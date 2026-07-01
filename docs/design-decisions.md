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