# AWS-VPC
A project-based AWS Virtual Private Cloud demonstrating subnetting, routing and security fundamentals. 

### 1. Creating the VPC
* In AWS dashboard, search for 'VPC'
* Click on 'Create VPC' & choose 'VPC only' option
* Give VPC a name (VPClab01)
* Create a IPv4 CIDR block (10.0.0.0/16) & no IPv6 CIDR for this project
* leave 'tenancy' to default for eligible free tier options



### 2. Creating the public subnet & auto-assigning IPv4 adresses
* In the VPC dashboard, on left hand side, click on 'subnets'
* Click 'create subnet'
* In the VPC ID dropdown, select your VPC (VPClab01)
* Under subnet settings:
  * give it a name (labPublicSubnet01)
  * Availability zone option is personal preference
  * Create a specific IPv4 subnet CIDR block for this subnet (10.0.1.0/24)
* Once back to VPC dashboard:
  * choose recently create subent
  * ON upper right hand corner, click 'actions' > 'edit subnet settings' > enable 'auto-assign public IPv4 address'
  * this allows instance to have a reachable IPv4 address that lives within the recently created subnet (10.0.1.0/24)



### 3. Creating the Internet Gateway & attaching it to VPC
* Back on VPC dashboard, in left hand side, click on 'internet gateway'
* Click 'create internet gateway'
* Give it a name (labIGW01)
* still in 'internet gateway':
  * click on the recently created IGW
  * on upper right hand corner, click on 'actions' > 'attach to VPC' > select your VPC (VPClab01) > 'state' column should appear 'attached'



### 4. Creating the route table & making internet traffic route through the Internet Gateway
* On right hand side, click 'route tables'
* Click 'create route table'
* Give route table a name (labPublicRouteTable01)
* Select your VPC to attach the route table (VPClab01)
* Still in 'route tables':
  * select 'edit routes'
  * add a new route (0.0.0.0/0) meaning all traffic will be routed through internet
  * 'Target' stays as 'local' which is your machine
  * In third option, select recently created internet gateway



### 5. Associating route table with subnet
* Still in 'route table':
  * select 'actions' > 'edit subet associations'
  * choose your public subnet (labPublicSubnet01)



### 6. Creating a Security Group with SSH & HTTP inbound rules
* In search menu, look up 'EC2'
* On right hand side, click on 'security groups' where we will first create security rules for our instance
* Click on 'create security group':
  * give it a name (labSecurityGroup01)
  * add a description of rule (allow SSH & HTTP inbound traffic)
  * connect your VPC to the security group (VPClab01)
  * Under 'inbound rules':
    * in 'type' select 'SSH' which auto configures TPC/22 as protocol and port number
    * 'Source' will be 'my ip' which is the IPv4 from our subnet. Anything else will leave your instance vulnerable to the entire internet.
    * click 'add rule' HTTP will be TCP port 80 and 'source' is still 'my ip'



### 7. Creating instance & Creaing SSH key pair + configuring instance network settings
* Back on EC2 dashboard:
  * click on 'launch instance'
  * give it a name (labLinux01)
  * under 'applications and OS images' choose 'amazon linux' free tier
  * keep everything else to its default settings if using free tier
* Under 'key pair(login)':
  * click on 'create new key pair' > give it a name (labLinux01Key) > RSA encryption is fine > '.pem' if using openSSH or '.ppk' if using PuTTY terminal
  * once key is created it will be downloaded to your machine
  * a key pair login is more secure than username & password for remote logins. All data is encrypted while traversing the network.
* Under 'network settings':
  * click 'edit'
  * 'VPC' is one you've created (VPClab01) same goes for 'subnet' (labPublicSubnet01)
  * 'auto-assign public IP' should be enabled
  * in 'firewall' click 'select existing security group' and choose one you've created (labSecurityGroup01)
  * leave everything else as default
  * click 'launch instance' and wait for initialization to finish
 

### 8. Connecting EC2 instance & verifying it is up and running
* Once initialization is complete, choose your instance (labLinux01) and click 'connect'
* on 'connect to instance':
  * choose 'connect using EC2 instance connect' your public IPv4 address, with default username (ec2-user)
  * click 'connect' and you will be dropped into the AWS cloud hosted machine
* If using a separate machine:
  * open up the terminal/SSH client
  * locate your private key file (labLinux01Key.pem)
  * optionally, run $ chmod 400 "labLinux01Key.pem" to make sure your key is not publicly viewable
  * connect to the EC2 instance using its public IPv4 address - ex: $ ssh -i "labLinux01Key.pem" ec2-user@yourpublicIPv4
