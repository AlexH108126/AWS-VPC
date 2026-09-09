## VPC Build Walkthrough With Screenshots

### 1. Creating the VPC
![VPC Created] <img width="1920" height="1080" alt="create vpc 1" src="https://github.com/user-attachments/assets/9fc4064f-00d0-4e6d-80aa-90f7182d3e6a" />
<img width="1920" height="1080" alt="create vpc 2" src="https://github.com/user-attachments/assets/4d8bb49e-f526-4ef7-9688-30509a575dae" />

### 2. Creating the public subnet & auto-assigning IPv4 adresses
![Public subnet] <img width="1920" height="1020" alt="create subnet" src="https://github.com/user-attachments/assets/c0b09f0a-7dea-40b8-a724-2f01fb10d23b" />
![Allow auto-assign IPv4] <img width="1920" height="1020" alt="auto-assign public IPv4" src="https://github.com/user-attachments/assets/4542a18c-b450-43eb-98de-f4418f1bd6ca" />


### 3. Creating the Internet Gateway & attaching it to VPC
![Internet gateway] <img width="1920" height="1020" alt="create IGW" src="https://github.com/user-attachments/assets/bb9c48eb-c804-4b49-b4ac-8b0ca39a2960" />
![IGW attached] <img width="1920" height="1020" alt="attach IGW to VPC" src="https://github.com/user-attachments/assets/ee4d11db-6335-4dd1-acc1-8d8b1d3f4cbc" />


### 4. Creating the route table & making internet traffic route through the Internet Gateway
![Route table] <img width="1920" height="1020" alt="create route table" src="https://github.com/user-attachments/assets/5047c5c3-923a-4727-8b73-ed5f168e1bbc" />
![Default outgoing traffic route] <img width="1920" height="1020" alt="create route for IGW" src="https://github.com/user-attachments/assets/4773bfd4-c5e4-4359-973f-d14f8ab191c8" />

### 5. Associating route table with subnet
![Route table associated w/subnet] <img width="1920" height="1020" alt="associate IGW route table w subnet" src="https://github.com/user-attachments/assets/9363630c-427f-42d1-83b6-bf4ae502f3f4" />

### 6. Creating a Security Group with SSH & HTTP inbound rules
![Security Group] <img width="792" height="825" alt="create SG with inbound SSH   HTTP rules" src="https://github.com/user-attachments/assets/545dd54f-9526-4785-969f-8147100787e0" />

### 7. Creating instance & Creaing SSH key pair + configuring instance network settings
![VPC Instance] <img width="1920" height="1020" alt="create instance" src="https://github.com/user-attachments/assets/18bc872b-ac6c-478f-adb8-3922af3a74c3" />
![Key pair + network settings] <img width="1920" height="1020" alt="generate SSH key pair   config instance network settings" src="https://github.com/user-attachments/assets/f56a1ecc-8feb-4221-ad6c-c73506783562" />

### 8. Connecting EC2 instance & verifying it is up and running
![Instance connect] <img width="1920" height="1020" alt="make connection to ec2 instance (linux VM)" src="https://github.com/user-attachments/assets/522b7dda-f0d2-4740-a4b3-3842ffaa60bb" />
![SSH into EC2 instance] <img width="1920" height="1020" alt="SSH into EC2 instance using generated key pair" src="https://github.com/user-attachments/assets/23c5cd1b-ca47-44bf-989d-52d5efc40645" />






