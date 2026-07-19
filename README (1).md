# AWS Server Commander — Cloud Computing Project

## Overview
This project simulates a real-world DevOps/SysAdmin task: provisioning a virtual server in the cloud, securing it, and deploying a live web service — entirely through command-line administration (no managed services).

Built as part of a Cloud Computing (AWS/Azure) internship track, this represents the "provisioning phase" of infrastructure work — going from raw compute to a live, publicly accessible web asset.

## Scenario
A startup needed a dedicated server environment with full control over the OS, to install custom software and security patches — rather than a managed/serverless solution.

## What Was Built
- Provisioned a **Linux virtual machine** (Amazon Linux 2023) on **AWS EC2**
- Secured the server using **SSH key-pair authentication** (RSA, `.pem`)
- Configured a **firewall (Security Group)** with least-privilege access:
  - Port 22 (SSH) restricted to a single IP
  - Ports 80 (HTTP) and 443 (HTTPS) open for public web traffic
- Connected to the instance remotely via **SSH**
- Installed and configured **Nginx** as the web server via the command line
- Deployed a custom, live landing page for freelance creative/web services

## Tech Stack / Tools
| Component | Tool |
|---|---|
| Cloud Provider | AWS (EC2) |
| OS | Amazon Linux 2023 |
| Web Server | Nginx |
| Access | SSH (key-based auth) |
| Region | Europe (Stockholm) — eu-north-1 |

## Architecture / Shared Responsibility
- **AWS is responsible for:** physical data centers, hardware, virtualization layer (Nitro hypervisor)
- **I (the operator) am responsible for:** guest OS & patching, firewall rules (Security Groups), IAM access, and everything running on top of the VM

## Steps Performed
1. **Provisioning** — Launched a `t3.micro` EC2 instance (Free Tier eligible) with a new key pair
2. **Securing the Perimeter** — Created a custom Security Group allowing SSH (restricted), HTTP, and HTTPS
3. **The Handshake** — Set correct file permissions on the private key and connected via SSH from a Windows terminal
4. **Deploying the Payload** — Updated packages and installed Nginx:
   ```bash
   sudo dnf update -y
   sudo dnf install nginx -y
   sudo systemctl start nginx
   sudo systemctl enable nginx
   ```
5. **Customizing the Asset** — Replaced the default Nginx page with a custom HTML landing page (`index.html`, included in this repo) at `/usr/share/nginx/html/index.html`
6. **Verification** — Confirmed the page was live and publicly reachable over HTTP

## Live Demo
The project was deployed and verified live at the instance's public IP address (Note: EC2 public IPs are dynamic and change on instance stop/restart unless an Elastic IP is attached).

## Key Concepts Demonstrated
- Infrastructure as a Service (IaaS)
- Virtualization & hypervisor logic
- Public/private key cryptography for secure access
- Network security (firewall/Security Group rules, least-privilege access)
- Linux command-line system administration
- Web server installation & configuration

## Files in This Repo
- `index.html` — the custom webpage deployed on the live server

## Author
**Naren Palani**
📧 narestheace@gmail.com
💬 WhatsApp: [@NarenPalani](https://wa.me/NarenPalani)

Freelance services: Web Design · Video Editing · Image Editing · Banners · Logos
