✅ Step-by-Step Resource Flow
1️⃣ VPC Creation
CIDR: 10.0.0.0/16

2️⃣ Subnet Creation
Public Subnet (e.g., 10.0.1.0/24)

Enable: Auto-assign public IPv4 address

3️⃣ Internet Gateway (IGW)
Create IGW

Attach IGW to the VPC

4️⃣ Route Table
Create Route Table in VPC

Add Route: 0.0.0.0/0 → IGW

Associate it with the Public Subnet

5️⃣ Security Group
Allow:

SSH (22) from your IP

HTTP (80) from Anywhere

6️⃣ EC2 Launch
AMI: Amazon Linux 2

Instance Type: t2.micro

Network: Select custom VPC

Subnet: Choose public subnet

Enable auto-assign public IP (if not set on subnet)

Assign Security Group

7️⃣ Test
SSH into EC2

Install NGINX

Visit public IP in browser

Day 1 AWS VPC Setup Recap
🔹 VPC & Networking
Resource	Configuration
VPC	10.0.0.0/16
Public Subnet	10.0.1.0/24
Internet Gateway (IGW)	Attached to VPC
Route Table	0.0.0.0/0 → IGW (for internet access)
Auto-assign Public IP	Enabled for subnet

🔹 Compute (EC2)
Component	Configuration
EC2 Instance	t2.micro (Amazon Linux 2)
Key Pair	Your existing .pem key
Subnet	Public Subnet
Public IP	Auto-assigned
Security Group	
→ SSH (22)	From your IP only
→ HTTP (80)	From Anywhere

🔹 NGINX Setup
bash
Copy
Edit
sudo amazon-linux-extras enable nginx1
sudo yum clean metadata
sudo yum install -y nginx
sudo systemctl start nginx
curl localhost  # to verify
Visit http://<your-ec2-public-ip> to view the default NGINX page.

✅ What’s Working
Custom VPC with internet access

EC2 running and reachable via SSH + HTTP

Web server successfully responding

