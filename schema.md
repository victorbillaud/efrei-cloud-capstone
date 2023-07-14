# Architecture diagram for the Infrastructure solution

## Overview

In this architecture diagram, we have implemented a Virtual Private Cloud (VPC) with two subnets: a public subnet and a private subnet. The VPC allows us to isolate and manage our resources securely within the AWS cloud environment.

## Public Subnet

In the public subnet, we have deployed an EC2 instance. The EC2 instance serves as a compute resource and is connected to the internet through the VPC's Internet Gateway. It allows the EC2 instance to communicate with the external world, making it accessible from the internet. The EC2 instance is secured with a specific security group, which defines inbound and outbound traffic rules.

Additionally, the public subnet contains a NAT Gateway. The NAT Gateway acts as a middleman for outbound traffic from the private subnet to the internet. It enables the resources within the private subnet to access the internet securely while keeping them hidden from external entities. The NAT Gateway helps maintain the security and integrity of the private subnet.

## Private Subnet

In the private subnet, we have deployed an RDS instance running SQL Server. The RDS instance provides a managed relational database service, enabling efficient storage and retrieval of data. By placing the RDS instance in the private subnet, we ensure that it is not directly accessible from the internet, adding an extra layer of security.

Similar to the EC2 instance, the RDS instance is also protected by a specific security group. This security group allows only authorized traffic to access the RDS instance and ensures the integrity and confidentiality of the database.

## VPC Router

The VPC Router plays a crucial role in facilitating communication between the public and private subnets. It allows traffic to flow between these subnets while enforcing network security and isolation. The VPC Router ensures that requests from the public subnet are appropriately routed to the NAT Gateway, which then forwards the traffic to the private subnet.

Overall, this architecture diagram demonstrates a secure and scalable setup where the public subnet hosts an EC2 instance accessible from the internet, while the private subnet contains an RDS instance for SQL Server. By leveraging the VPC, security groups, and network routing, we ensure the protection and efficient communication between these resources within the AWS cloud environment.