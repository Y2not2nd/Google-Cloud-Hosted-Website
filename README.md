# Cloud-Hosted Website Project

This project documents the process of setting up a simple website hosted on a Google Cloud VM with a custom domain. 

## Table of Contents

1. [DNS Purchase and Transfer](#dns-purchase-and-transfer)
2. [Google Cloud VM Creation](#google-cloud-vm-creation)
3. [A Record Configuration](#a-record-configuration)
4. [VM Setup and Nginx Configuration](#vm-setup-and-nginx-configuration)
5. [Website Folder Structure](#website-folder-structure)
6. [SSH Key Pair for Uploading Files](#ssh-key-pair-for-uploading-files)

---

### 1. DNS Purchase and Transfer

[See the full documentation here](dns-config/dns-setup.md).

- Purchase a domain from a registrar (e.g., GoDaddy, Namecheap).
- Transfer the domain to Google Domains (if applicable).
- Set up DNS records to point to your VM's IP.

### 2. Google Cloud VM Creation

[See the full documentation here](vm-setup/google-cloud-vm.md).

- Create a new VM on Google Cloud.
- Choose the appropriate OS and specs.
- Configure firewall settings to allow HTTP/HTTPS traffic.

### 3. A Record Configuration

- Point your domain’s A record to the external IP address of the VM.
- Verify DNS propagation using tools like DNSChecker.

### 4. VM Setup and Nginx Configuration

- Install Nginx on the VM.
- Configure Nginx to serve the website on your domain.

### 5. Website Folder Structure

- Organize your website files into a structure like the following:
  ```plaintext
  /var/www/html/
  ├── index.html
  ├── css/
  │   └── styles.css
  ├── js/
  │   └── script.js
  └── images/
      └── logo.png