
### Identity and Access Management

* IAM(Identity and Access Management), it is a Global service
* Root account created by default, shouldn’t be used or shared
* Users are people within your organization, and can be grouped
* Groups only contain users, not other groups
* Users don’t have to belong to a group, and user can belong to multiple groups
  
![[ctops-aim-user.png]](Images/ctops-aim-user.png)


## IAM Permissions means 

* Users or Groups can be assigned JSON documents called policies, these policies defines the permissions of the groups or users 
* In AWS you apply the **least privilege principle** don’t give more permissions than a single user needs

Example:  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "ec2:Describe*",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "elasticloadbalancing:Describe*",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "cloudwatch:ListMetrics",
                "cloudwatch:GetMetricStatistics",
                "cloudwatch:Describe*"
            ],
            "Resource": "*"
        }
    ]
}
```

### IAM Policies Structure

**Policies Consist of** 

* **Version:** Policy language version, always include “2012-10-17”
* **ID:** identifier for the policy (optional)
* **Statement:** one or more individual statements (required)

**Statements consists of**

* **Sid:** an identifier for the statement (optional)
* **Effect: **whether the statement allows or denies access (Allow, Deny)
* **Principal: **account/user/role to which this policy applied to
* **Action: **list of actions this policy allows or denies
* **Resource: **list of resources to which the actions applied to
* **Condition: **conditions for when this policy is in effect (optional)


![[ctops-iam-polices-structure.png]](Images/ctops-iam-polices-structure.png)

### MFA  

Users have access to your account and can possibly change configurations or delete resources in your AWS account, we need to protect our AWS Root account & IAM users 

**MFA = password you know + security device you own**

Note: if a password is stolen or hacked, the account is not compromised if you setup MFA

### How can ways users access AWS

To access AWS resources, we have a three options:
* AWS Management Console (protected by password + MFA)
* AWS Command Line Interface (CLI): protected by access keys
* AWS Software Developer Kit (SDK) - for code: protected by access keys
Access Keys are generated through the AWS Console

**Note:** Access Keys are secret, just like a password. Don’t share them

### IAM Security Tools

* IAM Credentials Report (account-level) --> lists all your account's users and the status of their various credentials
* IAM Access Advisor (user-level) ---> Access advisor shows the service permissions granted to a user and when those services were last accessed. we can use this information to revise our policies.

### IAM Best Practices

1. Don’t use the root account except for AWS account setup
2. One physical user = One AWS user
3. Assign users to groups and assign permissions to groups
4. Create a strong password policy
5. Use and enforce the use of Multi Factor Authentication (MFA)
6. Create and use Roles for giving permissions to AWS services
7. Use Access Keys for Programmatic Access (CLI / SDK)
8. Audit permissions of your account using IAM Credentials Report & IAMAccess Advisor
9. Never share IAM users & Access Keys

### IAM Section – Summary
* Users: mapped to a physical user, has a password for AWS Console
* Groups: contains users only
* Policies: JSON document that outlines permissions for users or groups
* Roles: for EC2 instances or AWS services
* Security: MFA + Password Policy
* AWS CLI: manage your AWS services using the command-line
* AWS SDK: manage your AWS services using a programming language
* Access Keys: access AWS using the CLI or SDK
* Audit: IAM Credential Reports & IAM Access Advisor
