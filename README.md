# ansible-3tier-pipeline
Devops pipeline automation sample project
# 3-Tier Web Application Deployment using Ansible + Jenkins

This repo provisions Apache, Flask App, and MariaDB on a single EC2 instance using Ansible and automates it via Jenkins pipeline.

## Structure

- **web**: Apache httpd
- **app**: Flask running on port 5000
- **db**: MariaDB with user `appuser`

## Steps

1. Clone this repo
2. Edit your `inventory/localhost.ini` or use public IP
3. Connect Jenkins to GitHub and run pipeline

## Access

- Web UI: `http://<your-ec2-ip>/`
- Flask App: `http://<your-ec2-ip>:5000`

