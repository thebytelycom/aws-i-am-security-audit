# AWS IAM Security Audit & Least-Privilege Implementation

## Project Overview

This project demonstrates the implementation of AWS Identity and Access Management (IAM) security controls using AWS IAM and Amazon S3.

The main objective was to apply the **Principle of Least Privilege**, organize users and permissions using IAM groups, enable Multi-Factor Authentication (MFA), and test both authorized and unauthorized access.

This project was completed as a hands-on cloud security lab using the AWS Management Console.

---

## Objectives

* Create and manage IAM users and groups
* Organize permissions using IAM groups
* Apply AWS managed IAM policies
* Create a custom least-privilege policy
* Restrict S3 access to a specific development bucket
* Enable Multi-Factor Authentication (MFA)
* Test authorized and unauthorized access
* Perform a basic IAM security audit

---

## AWS Services Used

* **AWS IAM** – Identity and access management
* **Amazon S3** – Storage and access-control testing
* **AWS Management Console** – Configuration and security testing

---

## IAM Users

### 1. Security Lab User

**IAM User:** `security-lab-users`

This user was created for the security lab and permission testing.

The user was associated with the `security-lab-users` IAM group and was used to test access to AWS resources according to the assigned permissions.

### 2. Security Auditor

**IAM User:** `security-auditor`

This user was created for security auditing and IAM visibility.

The user was associated with the `Security-Auditors` group.

---

## IAM Groups

### 1. security-lab-users

**IAM Group:** `security-lab-users`

The `security-lab-users` group was used to manage permissions for the security lab user.

Policies associated with the group included:

* `AmazonEC2ReadOnlyAccess`
* `AmazonS3ReadOnlyAccess`
* `Developer-S3-ReadOnly`

These permissions provide read-only access to selected AWS resources.

---

### 2. Security-Auditors

**IAM Group:** `Security-Auditors`

The `Security-Auditors` group was created for security review activities.

Policies attached:

* `IAMReadOnlyAccess`
* `SecurityAudit`

These policies provide visibility into IAM and security-related configuration without granting administrative modification permissions.

---

## Amazon S3 Development Bucket

A dedicated S3 bucket was created for permission testing.

**Bucket:** `iam-security-dev-2026-srishty`

A test file was uploaded to the bucket to verify whether the configured IAM permissions worked as expected.

The S3 bucket was used to demonstrate controlled read access and restricted unauthorized actions.

---

## Custom Least-Privilege Policy

A custom IAM policy named:

`Developer-S3-ReadOnly`

was created to implement the **Principle of Least Privilege**.

The policy allows only the permissions required to read data from the designated development S3 bucket.

### Allowed Actions

* `s3:ListBucket`
* `s3:GetObject`

### Restricted Actions

The policy does not grant permissions to:

* Delete S3 objects
* Modify S3 objects
* Change IAM permissions
* Perform administrative IAM actions

### Policy Structure

```text
security-lab-users
        |
        v
security-lab-users Group
        |
        +---- EC2 Read Only
        |
        +---- S3 Read Only
        |
        +---- Developer-S3-ReadOnly
                    |
                    v
       Development S3 Bucket
       iam-security-dev-2026-srishty
```

---

## Multi-Factor Authentication (MFA)

MFA was enabled for the IAM user as an additional security control.

MFA provides an additional authentication factor during account access and is an important security measure for protecting user identities.

---

## Permission Testing

After configuring the IAM permissions, access was tested using the configured IAM users.

### Testing Performed

| Test                            | Result  |
| ------------------------------- | ------- |
| Access authorized S3 resource   | Allowed |
| Read authorized S3 object       | Allowed |
| Unauthorized S3 action          | Denied  |
| Unauthorized IAM access         | Denied  |
| Security auditor IAM visibility | Allowed |

The tests demonstrated that permissions were being enforced according to the configured IAM policies.

---

## Security Audit

The following IAM security areas were reviewed during the project:

* IAM users
* IAM groups
* Group membership
* Attached IAM policies
* Custom IAM policy
* S3 permissions
* MFA configuration
* Authorized access
* Unauthorized access
* Security auditing permissions

---

## Results

The project demonstrated the practical implementation of several AWS security principles:

* **Least Privilege** – Users receive only the permissions required for their tasks.
* **Access Control** – IAM groups were used to manage permissions.
* **Read-Only Access** – Development-related permissions were restricted to read operations.
* **MFA** – An additional authentication factor was enabled.
* **Permission Testing** – Authorized and unauthorized actions were tested.
* **Security Auditing** – A separate auditor user was configured to review IAM and security information.

---

## Screenshots

The repository contains screenshots documenting the implementation process, including:

1. IAM security overview
2. IAM users
3. Security lab user permissions
4. Security auditor permissions
5. S3 development bucket
6. Custom least-privilege policy
7. IAM group permissions
8. Authorized S3 access
9. Unauthorized access test
10. MFA configuration
11. Security auditor access
12. Final IAM configuration

---

## Key Learning Outcomes

Through this hands-on project, I gained practical exposure to:

* AWS IAM
* IAM Users
* IAM Groups
* IAM Policies
* AWS Managed Policies
* Custom IAM Policies
* JSON-based IAM permissions
* Principle of Least Privilege
* Amazon S3 access control
* Multi-Factor Authentication
* Permission testing
* Basic cloud security auditing

---

## Skills Demonstrated

**AWS IAM | Cloud Security | Identity & Access Management | Access Control | Least Privilege | S3 Security | MFA | IAM Policy Management | Security Auditing**

---

## Project Outcome

This project helped me understand how identity, permissions, authentication, and resource access are controlled in AWS.

It also provided hands-on experience in configuring IAM security controls and validating them through permission testing.

---

## Disclaimer

This project was created as a learning and portfolio project using AWS resources.

No passwords, access keys, secret keys, MFA secrets, or other sensitive credentials are included in this repository.
