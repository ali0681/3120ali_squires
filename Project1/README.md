# Your Name: Ali Squires  

# Part 1: Build a VPC

## Create a VPC  
Name: SQUIRES-VPC  
Specify a CIDR block of 192.168.0.0/23

<img width="1626" height="337" alt="image" src="https://github.com/user-attachments/assets/943f3269-f5b0-4848-87fb-31e0a9b0a8ec" />
Role: The VPC allows you to launch resources to a network you fefine. it serves as the foundation for your cloud network, where you can control things like IP adress ranges, subnets, route tables, internet connectivity, and security settings. It basically defines the networking eviroment in which EC2 instances and otherr AWS resources operate. <br>


At any point in the process of creating a VPC and its related resources, additional information may be requested like CIDR block ranges, subnet configuration, route table associations, internet gateway setup , security settings , security groups, network ACLs, and elastic IPs. These ensure that your network is correct, secured, and connected which are the design goals of the VPC.

## Create a Subnet  
Name: SQUIRES-Subnet  
Reserve 192.168.0.0 - 192.168.0.255 for use on this subnet

<img width="1636" height="254" alt="image" src="https://github.com/user-attachments/assets/dc66590b-f252-44ed-b189-18a78de9f0c8" />
Role: This subnet reserves the IP adress range 192.168.0.0 - 192.168.0.255 within my VCP. 


The subnet uses CIDR block 192.168.0.0/24 which is the IP range 192.168.0.0 - 192.168.0.255, the subnet is created inside the VCP, the avaliablity zone was set to no prefrences, laslty tagging the subnet helps label and organize.


## Create an Internet Gateway
Name: SQUIRES-gw  
Attach it to your VPC

<!-- a description of what the resource does (what is its role). responses to additional requests for information in any step. a screenshot that shows the resource has been created according to specification -->

## Create Route Table 
Name: SQUIRES-rt
Attach it to your VPC
Associate it with your subnet
Add a routing table rule that sends traffic to destinations external to your subnet CIDR block to your internet gateway

<!-- a description of what the resource does (what is its role). responses to additional requests for information in any step. a screenshot that shows the resource has been created according to specification -->

## Create a Security Group   
Name: SQUIRES-sg  
Allow SSH for a set of trusted source networks including:
Your home / where you usually connect to your instances from
Wright State (addresses in CIDR block 130.108.0.0/16)
Instances within the VPC
Attach it to your VPC
Make sure screenshot includes content of the Inbound rules

<!-- a description of what the resource does (what is its role). responses to additional requests for information in any step. a screenshot that shows the resource has been created according to specification -->

## Modify or create a Network ACL
Name: Squires-nacl
Affirm association or associate resource with the subnet
Verify that for Inbound & Outbound there is a rule that Allows any IP (v4 only is sufficient) on all ports
If this rule does not exist, you'll need to create it. Created Network ACL's are Deny all traffic on all ports, Inbound and Outbound, by default.
Deny outbound connections to any port on wttr.in

<!-- a description of what the resource does (what is its role). responses to additional requests for information in any step. a screenshot that shows the resource has been created according to specification -->

## Identify OR create a Key Pair
Document how the public and private keys of a key pair are stored.

<!-- a description of what the resource does (what is its role). responses to additional requests for information in any step. a screenshot that shows the resource has been created according to specification -->

## Reserve an Elastic !P adress
Name: Squires-EIP
Document the difference between an Elastic IP and a Public IP.

<!-- a description of what the resource does (what is its role). responses to additional requests for information in any step. a screenshot that shows the resource has been created according to specification -->
