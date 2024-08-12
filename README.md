# Cloud-Hosted Website Project

This project documents the process of setting up a simple website hosted on a Google Cloud VM with a custom domain. 

## Table of Contents 

1. [DNS Purchase and Transfer]
2. [Google Cloud VM Creation]
3. [VM Setup and Nginx Configuration]
4. [Website Folder Structure]
5. [Creating the Website]
   
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
- Point your domain’s A record to the external IP address of the VM.
- Verify DNS propagation using tools like DNSChecker.

### 3. VM Setup and Nginx SSL Configuration

- Install Nginx on the VM.
- Configure Nginx to serve the website on your domain.
- Obtain SSL Certification (Optional)

### 4. Website Folder Structure 

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
 ### 5. Creating Website 
- Create the project folders
- Copy code into Folders
- Use SCP command to copy over images from local device
- Test!
