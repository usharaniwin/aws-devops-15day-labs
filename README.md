# aws-devops-15day-labs
# ☁️ Day 1: AWS VPC + EC2 Manual Setup

This guide covers setting up a custom VPC, subnet, internet gateway, route table, and launching an EC2 instance to host a web server (NGINX) from scratch using AWS Console.

---

## 🔹 VPC Setup

| Component       | Details                |
|----------------|------------------------|
| VPC CIDR       | `10.0.0.0/16`          |
| Subnet CIDR    | `10.0.1.0/24` (public) |
| IGW            | `day1-igw`             |
| Route Table    | `public-rt`            |
| Subnet Routes  | `0.0.0.0/0 → IGW`      |
| Auto-assign IP | Enabled for public-subnet |

---

## 🔹 EC2 Instance Setup

| Component          | Value                    |
|--------------------|--------------------------|
| AMI                | Amazon Linux 2           |
| Instance Type      | `t2.micro`               |
| Key Pair           | `<your-key>.pem`         |
| Security Group     | SSH (22 from My IP), HTTP (80 from Anywhere) |
| Public IP          | Auto-assigned            |

---

## 🔹 Install NGINX on EC2

```bash
# Enable NGINX and install
sudo amazon-linux-extras enable nginx1
sudo yum clean metadata
sudo yum install -y nginx

# Start service and test
sudo systemctl start nginx
curl localhost
