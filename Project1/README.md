# Your Name: Ali Squires  

# Part 1: Build a VPC

## Create a VPC  
- Name: Squires-VPC  
- Specify a CIDR block of 192.168.0.0/23

<img width="1626" height="337" alt="image" src="https://github.com/user-attachments/assets/943f3269-f5b0-4848-87fb-31e0a9b0a8ec" />

- Role: The VPC allows you to launch resources to a network you fefine. it serves as the foundation for your cloud network, where you can control things like IP adress ranges, subnets, route tables, internet connectivity, and security settings. It basically defines the networking eviroment in which EC2 instances and otherr AWS resources operate. 

- At any point in the process of creating a VPC and its related resources, additional information may be requested like CIDR block ranges, subnet configuration, route table associations, internet gateway setup , security settings , security groups, network ACLs, and elastic IPs. These ensure that your network is correct, secured, and connected which are the design goals of the VPC.

## Create a Subnet  
- Name: Squires-Subnet  
- Reserve 192.168.0.0 - 192.168.0.255 for use on this subnet

<img width="1636" height="254" alt="image" src="https://github.com/user-attachments/assets/dc66590b-f252-44ed-b189-18a78de9f0c8" />

- Role: This subnet reserves the IP adress range 192.168.0.0 - 192.168.0.255 within my VCP. 

- The subnet uses CIDR block 192.168.0.0/24 which is the IP range 192.168.0.0 - 192.168.0.255, the subnet is created inside the VCP, the avaliablity zone was set to no prefrences, laslty tagging the subnet helps label and organize.

## Create an Internet Gateway
- Name: Squires-gw  
- Attach it to your VPC

<img width="1472" height="363" alt="image" src="https://github.com/user-attachments/assets/812dbafa-a379-4e17-b554-b43adf5182be" />

- Role: The internet gateway allows my VCP to connect to the internet. It enabels communication between resources in the VCP and the internet by routing the traffic from the VCP to everything else. 

- The internet gateway was created and named Squires-gw, it was attached to my VPC to enable communication, and lastly this has to be done befor routing table to allow public internet access. 

## Create Route Table 
- Name: Squires-rt
  
<img width="1625" height="571" alt="image" src="https://github.com/user-attachments/assets/93a5136e-1b2e-4663-b355-0d751e510e59" />

- Role: The route table controls how traffic is routed within the VPC. It allows internal communication between subnets and external traffic to reach the iternet through a gateway.

- The route table is attached to my VPC, is associated with my subnet, and has its defualt route with an addtional one to my internet gateway.

## Create a Security Group   
- Name: Squires-sg  

<img width="1641" height="588" alt="image" src="https://github.com/user-attachments/assets/5361e62d-31f6-4e19-9dbd-d20658444a28" />
- Role: The security gtoup controls inbound traffic to instances tith the my VPC. It is configured to allow SSH access from three specific sources home, wright state, and VPC instance.

- The security group was tagged with the name Squires-sg, inbound rules were configured to allow SSH access from my three sources, the security group is attached to my VPC, no outbound rules were added.

## Modify or create a Network ACL
- Name: Squires-nacl

<img width="1620" height="555" alt="image" src="https://github.com/user-attachments/assets/32e9c8ae-6e6a-4c9e-919b-cea4a5a1b7b8" />
- Role: The network ACL acts as a stateless firewall at the subnet level. It controls inbound and outbound traffic to form allowed or denied, based on protocol, port range, and IP adress. By defualt all traffic is denied so exsplicit rules must be added.

- Confirmed the requirments to allow traffic on all ports for both inbound and outbound, confimed the need to deny outbound connections to wttr.in.


## Identify OR create a Key Pair
Document how the public and private keys of a key pair are stored.
- Squires-Key
The key pair enabels SSH access to EC2 instances. The public key is stored in AWS and the private key was downloaded as a .pem file and saved locally.
- public key: stored when the key was created
- private key: file Squires-Key.pem was downloades and saved securely.
 
<img width="1634" height="308" alt="image" src="https://github.com/user-attachments/assets/40bba763-36e8-4401-8e7c-7234785718ad" />
- Role: The key pair is used to securely connect to EC2 instances using SSH. The public key the public key is stored in AWS, and the private key is downloaded and stored securely by the user. This allows athentication when accessing the instance without using a password. 

- The private key was downladed, the public key is automatically stored in AWS and used when launching EC2 instances, the key pair enabeles secure, encrypted communication between the user and their server.

## Reserve an Elastic IP adress
- Name: Squires-EIP
Document the difference between an Elastic IP and a Public IP.
- Public IP is assigned automatically to an instance at launch and change when the instances is stopped and started.
- Elastic IP is a static IP adress that remains the same and can be reassociated with different instances if needed.

<img width="1626" height="570" alt="image" src="https://github.com/user-attachments/assets/220bcc72-81ba-4432-90a0-b238a7600014" />
- Role: Provides a static public IP adress for consistent access. 
  
- Elastic IPs are ideal when you need a constient adress for services, remote SSH, DNS records, or failover systems.

# Part 2: EC2 Instances Creation

## Create a new instance
An EC2 instance is a virtual machine running AWS that provided capcity in the cloud. It can be used to host applications, perform computions, or run services. To launch an instance the following steps were followed: This is how to luach

- use defualt Aamazon machine image
- use defualt instance type
- select my key pair (Squires-Key)
- attach my security group (Squires-sg)
- leave configure the same
- leave advance defualt
- then launch
- My VPC was already selected and couldnt be changed

## Associate the Elastic IP with your instance
- My EIP Squires-EIP wass associated with the instances to allow constience acess. 

<img width="1625" height="224" alt="image" src="https://github.com/user-attachments/assets/7fd19870-a4b9-4ebe-88b7-ca795033467c" />

# Part 3
I have no clue why but it can not find my Key even being downloaded 
## SSH acess
- ssh -i ~/keys/Squires-key.pem ec2-user@13.222.162.182

## Changing host name
- sudo cp /etc/hostname /etc/hostname.old
- echo "Squires-AMI" | sudo tee /etc/hostname
- sudo hostnamectl set-hostname Squires-AMI
- hostname

  ## Docker installtion
- sudo dnf update -y
- sudo dnf install -y docker
- sudo systemctl start docker
- docker --version


