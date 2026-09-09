# AWS-VPC
A project-based AWS Virtual Private Cloud demonstrating subnetting, routing and security fundamentals. 

### 1. Creating the VPC
* In AWS dashboard, search for 'VPC'
* Click on 'Create VPC' & choose 'VPC only' option
* Give VPC a name (VPClab01)
* Create a IPv4 CIDR block (eg: 10.0.0.0/16) & no IPv6 CIDR for this project.
* leave 'tenancy' to default for eligible free tier options.

### 2. Creating the public subnet & auto-assigning IPv4 adresses
* In the VPC dashboard, on left hand side, click on 'subnets'
* Click 'create subnet'
* In the VPC ID dropdown, select your VPC (VPClab01)
* under subnet settings,
  * give it a name (labPublicSubnet01) Availability zone option is preference
