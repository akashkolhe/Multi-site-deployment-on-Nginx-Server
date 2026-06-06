# NGINX Multi-Site Deployment on Ubuntu

This repository contains a comprehensive guide and configuration examples for deploying multiple websites simultaneously on a single NGINX server using an Ubuntu instance. Each website is configured to run on a unique port, allowing for efficient multi-site hosting on a single server.

## 🚀 Overview

The project demonstrates how to:
- Install and configure NGINX on Ubuntu.
- Set up independent directory structures for multiple websites.
- Configure NGINX server blocks for different ports.
- Manage security group rules for multi-port access.

## 📋 Prerequisites

- An Ubuntu server instance (e.g., AWS EC2, DigitalOcean Droplet).
- Sudo or root access to the server.
- Basic familiarity with the Linux command line.

## 🛠️ Installation & Setup

### 1. Install NGINX
Update your system and install the NGINX web server:
```bash
sudo apt-get update -y
sudo apt-get install nginx -y
```

### 2. Website Directory Setup
Create separate directories for each site under `/var/www/`:
```bash
sudo mkdir -p /var/www/site1 /var/www/site2 /var/www/site3 /var/www/site4 /var/www/site5
```

### 3. Configuration
The NGINX configuration files for each site should be placed in `/etc/nginx/sites-available/`. Each site is assigned a unique port (e.g., 210, 220, 230, etc.).

Example configuration structure:
- `config-1` -> Port 210
- `config-2` -> Port 220
- `config-3` -> Port 230
- `config-4` -> Port 240
- `config-5` -> Port 250

### 4. Enable Sites
Link the configuration files to the `sites-enabled` directory:
```bash
sudo ln -s /etc/nginx/sites-available/config-* /etc/nginx/sites-enabled/
```

### 5. Restart NGINX
Apply the changes by restarting the service:
```bash
sudo systemctl restart nginx
```

## 🔒 Security Considerations

Ensure that your cloud provider's security group or your local firewall (UFW) allows inbound traffic on the custom ports (210-250).

> **Warning:** Avoid using port 110, as it is reserved for the Post Office Protocol (POP3).

## 🌐 Verification

Access your sites via:
- Site 1: `http://your-server-ip:210`
- Site 2: `http://your-server-ip:220`
- ... and so on.

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
