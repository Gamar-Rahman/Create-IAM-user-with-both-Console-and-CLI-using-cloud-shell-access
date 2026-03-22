# Create-IAM-user-with-both-Console-and-CLI-using-cloud-shell-access
### Create IAM User with Console & CLI (CloudShell) Access
### Overview

This project demonstrates how to securely create and manage IAM users in AWS with:

Console access
CLI access via CloudShell
Controlled permissions using IAM policies
### Key Concepts
🔹 What is Amazon EC2?

Amazon EC2 provides scalable virtual servers used to host applications and services in AWS.

🔹 What is IAM (Identity and Access Management)?

IAM is a service that enables you to securely control access to AWS resources by defining:

Who can access resources (Authentication)
What actions they can perform (Authorization)

Key IAM components:

Users
Groups
Roles
Policies

### Problem Statement

Using the AWS root account for daily operations is risky and violates security best practices.

### The challenge:
How do we securely grant users access to AWS resources without exposing full administrative privileges?

### Solution

We implemented:

IAM user with least privilege access
Console login credentials
CLI access using AWS CloudShell
Permission policies for controlled access

### Implementation Steps

🔹 Step 1: Create S3 Bucket
Used for testing IAM permissions
🔹 Step 2: Create IAM User (Console)
Enable console access
Assign password
Attach permissions
🔹 Step 3: Test IAM User
Login using IAM credentials
Validate access scope
🔹 Step 4: CloudShell Setup
Launch AWS CloudShell
Configure environment
🔹 Step 5: Create IAM User via CLI
aws iam create-user --user-name demo-user
🔹 Step 6: Attach Policy
aws iam attach-user-policy \
  --user-name demo-user \
  --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
  
### Security Controls Implemented
✅ Least privilege access
✅ Separation of root and IAM users
✅ Controlled access via policies
✅ CLI and Console access auditing

### Testing
| Test Case                 | Result     |
| ------------------------- | ---------- |
| IAM Console Login         | Success ✅ |
| CLI Access via CloudShell | Success ✅ |
| Unauthorized action       | Blocked ❌ |

### Security Insight

### Never use the root account for daily operations.

IAM enables:

Granular access control
Reduced attack surface
Strong identity governance

### Future Improvements
Enable MFA for IAM users
Use IAM roles instead of long-term credentials
Integrate with AWS Organizations
Enable CloudTrail logging
