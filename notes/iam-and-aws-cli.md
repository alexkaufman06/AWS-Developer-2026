# IAM & AWS CLI

## Users & Groups

* IAM = Identity and Access Management, Global service
* Root account created by default, shouldn’t be used or shared
* Users are people within your organization, and can be grouped
* Groups only contain users, not other groups
* Users don’t have to belong to a group (though not best practice), and user can belong to multiple groups

## Permissions

* Users or Groups can be assigned JSON documents called policies
* These policies define the permissions of the users
* In AWS you apply the **least privilege principle**: don’t give more permissions than a user needs

**Example policy:**
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

## Policy Inheritance

* Policies at group level apply to each member of group
* A user can also have an inline policy just for them
* IAM Policy Structure
  * JSON with `Version`, `Id`, and `Statement`
    * Version: policy language version
    * Id: an identifier for the policy
    * Statement: one or more individual statements **(required)**
      * Sid: an identifier for the statement (optional)
      * Effect: whether the statement allows or denies access
      * Principal: account/user/role to which this policy is applied to
      * Action: list of actions this policy allows or denies
        * Can use `*` to match multiple actions like `cloudwatch:Get*`
      * Resource: list of resources to which the actions applied to
      * Condition: conditions for when this policy is in effect (optional)

## Password Policy
* Strong passwords = higher security for your account
* In AWS, you can setup a password policy:
  * Set a minimum password length
  * Require specific character types:
    * including uppercase letters
    * lowercase letters
    * numbers
    * non-alphanumeric characters
  * Allow all IAM users to change their own passwords
  * Require users to change their password after some time (password expiration)
  * Prevent password re-use

## Multi Factor Authentication (MFA)

* Users have access to your account and can possibly change
configurations or delete resources in your AWS account
* You want to protect your Root Accounts and IAM users
* MFA = password you know + security device you own
* Main benefit of MFA: if a password is stolen or hacked, the account is not compromised

## MFA device options in AWS

* Virtual MFA device
  * Google Authenticator (phone only)
  * Authy (phone only)
    * Support for multiple tokens on single device
* Universal 2nd Factor (U2F) Security Key
  * YubiKey
    * Support for multiple root and IAM users using a single security key
* Hardware Key Fob MFA Device
  * Gemalto
* Hardware Key Fob MFA Device for AWS GovCloud (US)
  * SurePassID
    
## How can users access AWS?

* To access AWS, you have three options:
  * AWS Management Console (protected by password + MFA)
  * [AWS Command Line Interface (CLI)](https://github.com/aws/aws-cli): protected by access keys
  * AWS Software Developer Kit (SDK) - for code: protected by access keys
    * Language-specific APIs (set of libraries)
    * Enables access/management of AWS ervices programmatically
    * Embedded within your application
    * AWS CLI is built on AWS SDK for Python
* Access Keys are generated through the AWS Console
* Users manage their own access keys
* Access Keys are secret, just like a password. **Don’t share them**
  * Access Key ID is treated like username
  * Secret Access Key is treated like password

## AWS CLI

* `aws --version`
* `aws configure`
  * Requires `Access Key ID` and `Secret Access Key`
* `aws iam list-users`
* Can also be run via `CloudShell` service in console
  * If you create files, they will persist
  * Can download/upload files

## IAM Roles for Services

* Some AWS services will need to perform actions on your behalf
* To do so, we will assign permissions to AWS services with IAM Roles
* Common roles:
  * EC2 Instance Roles
  * Lambda Function Roles
  * Roles for CloudFormation

## IAM Security Tools

* IAM Credentials Report (account-level)
  * A report that lists all your account's users and the status of their various credentials
* IAM Access Advisor (user-level)
  * Access advisor shows the service permissions granted to a user and when those services were last accessed
  * You can use this information to revise your policies
  * Helpful for reviewing usageand seeing what is needed (least priviledge principle)

## IAM Guidelines & Best Practices

* Don’t use the root account except for AWS account setup
* One physical user = One AWS user
* Assign users to groups and assign permissions to groups
* Create a strong password policy
* Use and enforce the use of Multi Factor Authentication (MFA)
* Create and use Roles for giving permissions to AWS services
* Use Access Keys for Programmatic Access (CLI / SDK)
* Audit permissions of your account using IAM Credentials Report & IAM Access Advisor
* **Never share IAM users & Access Keys**

## Shared Responsibility Model for IAM

* AWS
  * Infrastructure (global network security)
  * Configuration and vulnerability analysis
  * Compliance validation
* You
  * Users, Groups, Roles, Policies management and monitoring
  * Enable MFA on all accounts
  * Rotate all your keys often
  * Use IAM tools to apply appropriate permissions
  * Analyze access patterns and review permissions
