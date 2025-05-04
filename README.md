# Creating a Virtual Machine on Azure and Hosting a Static Website

This guide walks you through the process of creating a Virtual Machine (VM) on Microsoft Azure and hosting a static website on it. This is useful for deploying simple web pages without relying on complex backend infrastructure.

#### SEE FULLREPORT.pdf FOR A DETAILED WALKTHROUGH #####

## Prerequisites

- An active Microsoft Azure account
- Basic knowledge of Azure Portal or Azure CLI
- A static website ready to be hosted (HTML, CSS, JS files)

## Steps

### 1. Create a Virtual Machine on Azure

1. Log in to the [Azure Portal](https://portal.azure.com).
2. Navigate to **Virtual Machines** and click **Create** > **Azure virtual machine**.
3. Fill in the required details:
   - Subscription and Resource Group
   - Virtual machine name
   - Region
   - Image (choose a lightweight Linux distro like Ubuntu Server)
   - Size (choose based on your needs)
4. Configure Administrator account (SSH public key or password).
5. Under **Inbound port rules**, allow HTTP (port 80) and SSH (port 22).
6. Review and create the VM.

### 2. Connect to the Virtual Machine

- Use SSH to connect to your VM:
  ```bash
  ssh username@your_vm_public_ip

### 3. Install a Web Server
Update package lists and install Nginx:
 - sudo apt update
 - sudo apt install nginx -y

Start and enable Nginx:
 - sudo systemctl start nginx
 - sudo systemctl enable nginx
   
### 4. Deploy Your Static Website
    Upload your static website files to the VM. You can use scp or any SFTP client:
  - scp -r /path/to/your/static-site/* username@your_vm_public_ip:/var/www/html/

    Ensure the files have the correct permissions:
    - sudo chown -R www-data:www-data /var/www/html
    - sudo chmod -R 755 /var/www/html

### 5. Verify your website
    - Open a browser and navigate to http://your_vm_public_ip.
    - You should see your static website served by Nginx.

