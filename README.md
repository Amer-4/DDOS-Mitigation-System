DDoS Protection System for Cloud Infrastructure

 Overview

This project implements a real-time, cost-effective, multi-layered defense system against Distributed Denial-of-Service (DDoS) attacks, specifically targeting application-layer (Layer 7) HTTP floods. The system leverages Amazon Web Services (AWS), Nginx, and Python to detect and mitigate attacks while maintaining service availability for legitimate users.


 Setup & Deployment

1️. Deploy the Web Server

Launch EC2 instances (Ubuntu 20.04)

Install Nginx and configure rate limiting:

sudo apt update && sudo apt install nginx -y
sudo nano /etc/nginx/nginx.conf

2️. Configure AWS ALB & ACL

Set up an Application Load Balancer

Add ACL rules to limit requests per IP and enforce CAPTCHA when threshold exceeded

3️. Deploy Mitigation Script

Copy mitigation.py to EC2 instances

Set up a cron job to run the script every minute:

crontab -e
* * * * * python3 /path/to/mitigation.py

4️. Test the System

Use ddos_attack.py to simulate botnet attacks:

python3 ddos_attack.py --url http://your-load-balancer-dns




