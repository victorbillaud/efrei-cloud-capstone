# IAM Questions

## Which statement describes AWS Identity and Access Management (IAM) users ?

- [x] **IAM users are used to control access to a specific AWS resource**
- [ ] IAM user names can represent a collection of individuals
- [ ] Every IAM user for an account must have a unique name
- [ ] Every IAM user name is unique across all AWS accounts

## How can you grant the same level of permissions to multiple users within an account ?

- [x] **Apply an AWS Identity and Access Management (IAM) policy to an IAM group**
- [ ] Apply an AWS Identity and Access Management (IAM) policy to an IAM role
- [ ] Create a resource-based policy
- [ ] Create an organization in AWS Organizations

## Which statements describe AWS Identity and Access Management (IAM) roles ? (Select TWO)

- [ ] They are uniquely associated to an individual
- [ ] They can only be used by accounts associated to the person who created the role
- [x] **They can be assumed by individuals, applications and services**
- [x] **They provide temporary security credentials**
- [ ] They provide permanent security credentials

## Which statement describes a resource-based policy ?

- [x] **It can be applied to any AWS resource**
- [ ] It can be an AWS managed policy
- [ ] It is attached to a user or group
- [ ] It is always an inline policy

## How does AWS Identify and Access Management (IAM) evaluate a policy ?

- [ ] It checks for explicit allow statements before it checks for explicit deny statements
- [x] **It checks for explicit deny statements before it checks for explicit allow statements**
- [ ] It there is no explicit deny statement or explicit allow statement, users will haver access by default
- [ ] An explicit deny statement does not override an explicit allow statement

## A team of developers needs access to several services and resources in a virtual private cloud (VPC) for 9 months. How can you use AWS Identity and Access Management (IAM) to enable access for them?

- [ ] Create a single IAM user for the developer team and attach the required IAM policies.
- [ ] Create an IAM user for each developer, and attach the required IAM policies to each IAM user.
- [x] **Create an IAM user for each developer, put them all in an lAM group, and attach the required IAM policies to the IAM group.**
- [ ] Create a single IAM user for the developer team, place it in an IAM group, and attach the required IAM policies to the IAM group.

## How does identity federation increase security for an application that is built in Amazon Web Services (AWS)?

- [x] **Users can use single sign-on (SSO) to access the application through an existing authenticated identity.**
- [ ] The application can synchronize users' user names and passwords in AWS Identity and Access Management (IAM) with their social media accounts.
- [ ] The browser can establish a trust relationship with the application to bypass the need for multi-factor authentication (MFA).
- [ ] Users can use their AWS Identity and Access Management (IAM) accounts to log in to on premises systems.




# Network questions

## Which definition describes a virtual private cloud

- [ ] A virtual private network (VPN) in the AWS Cloud
- [ ] An extension of an on-premises network into Amazon Web Services (AWS)
- [x] **A logically isolated virtual network that you define in the AWS Cloud**
- [ ] A fully managed service that extends the AWS Cloud to customer premises

## A company's VPC has the CIDR block 172.16.0.0/21 (2048 addresses). It has two subnets (A and B). Each subnet must support 100 usable addresses now, but this number is expected to rise to at most 254 usable addresses soon. Which subnet addressing scheme meets the requirements and follows AWS best practices?

- [ ] Subnet A: 172.16.0.0/25 (128 addresses) Subnet B: 172.16.0.128/25 (1024 addresses)
- [ ] Subnet A: 172.16.0.0/25 (128 addresses) Subnet B: 172.16.0.128/25 (128 addresses)
- [x] **Subnet A: 172.16.0.0/23 (512 addresses) Subnet B: 172.16.2.0/23 (512 addresses)**
- [ ] Subnet A: 172.16.0.0/22 (1024 addresses) Subnet B: 172.16.4.0/22 (128 addresses)

## Which combination of actions enables direct internet access for IPv4 hosts in a virtual private cloud (VPC)? (Select THREE.)

- [x] **Creating a route for 0.0.0.0/0 that points to the internet gateway**
- [ ] Enabling Domain Name System (DNS) resolution for the VPC
- [x] **Configuring hosts to have or obtain an internet-routable address**
- [ ] Configuring the VPC domain name in a Dynamic Host Configuration Protocol (DHCP) options set
- [ ] Creating a default route that points to the virtual private gateway
- [x] **Configuring security groups and network access control lists (network ACLs) to permit internet traffic**

## Several EC2 instances launch in a virtual private cloud (VPC) that has internet access. These instances should not be accessible from the internet, but they must be able to download updates from the internet. How should the instances launch?

- [ ] With Elastic IP addresses, in a subnet with a default route to an internet gateway
- [ ] With public IP addresses, in a subnet with a default route to an internet
- [ ] Without public IP addresses, in a subnet with a default route to an internet gateway
- [x] **Without public IP addresses, in a subnet with a default route to a network address translation (NAT) gateway**

