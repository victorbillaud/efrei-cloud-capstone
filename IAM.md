# IAM

This part is to make sure you are able to evaluate and apply some policy constraintes.

## Policies evaluation

Please evaluate below IAM policies

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowEC2AndS3",
      "Effect": "Allow",
      "Action": [
        "ec2:RunInstances",
        "ec2:TerminateInstances",
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": [
        "arn:aws:ec2:us-east-1:123456789012:instance/*",
        "arn:aws:s3:::example-bucket/*"
      ]
    }
  ]
}
```

### Question: What actions are allowed for EC2 instances and S3 objects based on this policy? What specific resources are included?

This policy allows the actions `ec2:RunInstances`, `ec2:TerminateInstances`, `s3:GetObject`, and `s3:PutObject` for EC2 instances and S3 objects. The specific resources included are EC2 instances in the `us-east-1` region of account `123456789012` and objects in the `example-bucket` S3 bucket. This means that a user with this policy attached would be able to launch and terminate EC2 instances in the specified region and account, as well as get and put objects in the specified S3 bucket.

## -------------------------------------------- ##


```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowVPCAccess",
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeVpcs",
        "ec2:DescribeSubnets",
        "ec2:DescribeSecurityGroups"
      ],
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "aws:RequestedRegion": "us-west-2"
        }
      }
    }
  ]
}
```

### Question: Under what condition does this policy allow access to VPC-related information? Which AWS region is specified?

This policy allows access to VPC-related information if the condition that the requested region is `us-west-2` is met. The specified AWS region is `us-west-2`.

## -------------------------------------------- ##

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowS3ReadWrite",
      "Effect": "Allow",
      "Action": ["s3:GetObject", "s3:PutObject", "s3:ListBucket"],
      "Resource": [
        "arn:aws:s3:::example-bucket",
        "arn:aws:s3:::example-bucket/*"
      ],
      "Condition": {
        "StringLike": {
          "s3:prefix": ["documents/*", "images/*"]
        }
      }
    }
  ]
}
```

### Question: What actions are allowed on the "example-bucket" and its objects based on this policy? What specific prefixes are specified in the condition?

This policy allows the actions `s3:GetObject`, `s3:PutObject`, and `s3:ListBucket` on the `example-bucket` and its objects, but only if the condition that the object key prefix is either `documents/` or `images/` is met. The specific prefixes specified in the condition are `documents/*` and `images/*`. This means that a user with this policy attached would be able to get, put, and list objects in the specified S3 bucket, but only if the object key starts with either `documents/` or `images/`.

## -------------------------------------------- ##


```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowIAMUserCreation",
      "Effect": "Allow",
      "Action": "iam:CreateUser",
      "Resource": "arn:aws:iam::123456789012:user/${aws:username}"
    },
    {
      "Sid": "AllowIAMUserDeletion",
      "Effect": "Allow",
      "Action": "iam:DeleteUser",
      "Resource": "arn:aws:iam::123456789012:user/${aws:username}"
    }
  ]
}
```

### Question: What actions are allowed for IAM users based on this policy? How are the resource ARNs constructed?

This policy allows the actions `iam:CreateUser` and `iam:DeleteUser` for IAM users. The resource ARNs are constructed using the `${aws:username}` variable, which is replaced with the name of the IAM user being created or deleted. This means that a user with this policy attached would be able to create and delete IAM users in the specified account, and the resource ARNs would be dynamically constructed based on the name of the user being created or deleted.

## -------------------------------------------- ##

```json
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": ["iam:Get*", "iam:List*"],
    "Resource": "*"
  }
}
```

### Questions:

- Which AWS service does this policy grant you access to?
- Does it allow you to create an IAM user, group, policy, or role?
- Go to https://docs.aws.amazon.com/IAM/latest/UserGuide/ and in the left navigation expand Reference > Policy Reference > Actions, Resources, and Condition Keys. Choose Identity And Access Management. Scroll to the Actions Defined by Identity And Access Management list.Name at least three specific actions that the **iam:Get\*** action allows.

This policy grants you access to the IAM service. It allows you to perform actions that start with `iam:Get*` and `iam:List*` on all resources. This means that you can retrieve and list information about IAM resources, but you cannot create, modify, or delete them.

Three specific actions that the `iam:Get*` action allows are `iam:GetAccessKeyLastUsed`, `iam:GetAccountAuthorizationDetails`, and `iam:GetAccountPasswordPolicy`. These actions allow you to retrieve information about when an access key was last used, the details of all IAM users, groups, roles, and policies in your account, and the password policy for your account, respectively.

## -------------------------------------------- ##

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Condition": {
        "StringEquals": {
          "ec2:InstanceType": ["t2.micro", "t2.small"]
        }
      },
      "Resource": "arn:aws:ec2:*:*:instance/*",
      "Action": ["ec2:RunInstances", "ec2:StartInstances"],
      "Effect": "Deny"
    }
  ]
}
```

### Questions:

- What actions does the policy allow?
- Say that the policy included an additional statement object, like this **example:**

```json
{
  "Effect": "Allow",
  "Action": "ec2:*"
}
```

- How would the policy restrict the access granted to you by this additional statement?
- If the policy included both the statement on the left and the statement in question 2, could you terminate an m3.xlarge instance that existed in the account?

This policy does not allow any actions, it only denies the actions `ec2:RunInstances` and `ec2:StartInstances` for EC2 instances of type `t2.micro` or `t2.small`. If an additional statement object was included that allowed all EC2 actions, this policy would still restrict access by denying the ability to run or start instances of type `t2.micro` or `t2.small`. If both statements were included in the policy, you would still be able to terminate an m3.xlarge instance that existed in the account. This is because the `ec2:TerminateInstances` action is not explicitly denied by the policy, and the additional statement allows all EC2 actions.