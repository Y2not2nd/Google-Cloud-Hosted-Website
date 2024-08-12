# Google Cloud VM Creation

This section details how to create a Virtual Machine (VM) in Google Cloud, including considerations for free trial limitations.

## Step 1: Create a New VM

1. **Log in to Google Cloud Console:**
   - Visit [Google Cloud Console](https://console.cloud.google.com/) and log in with your account.

2. **Navigate to VM Instances:**
   - In the left-hand menu, select **Compute Engine** > **VM instances**.
   - Click **Create Instance** to start the setup process.

3. **Choose the Region:**
   - To stay within the free trial limits, select one of the following regions for your VM:
     - **Oregon:** `us-west1`
     - **Iowa:** `us-central1`
     - **South Carolina:** `us-east1`
   - These regions are eligible for the free trial.

4. **Select the Machine Type:**
   - Choose the **e2-micro** machine type. This is included in the free trial and provides:
     - 1 non-preemptible e2-micro VM instance per month.

5. **Configure Storage:**
   - You are allowed **30 GB-months of standard persistent disk** storage. Configure the boot disk accordingly.
   - The default disk size is 10 GB, but you can adjust it as needed, keeping in mind the 30 GB limit.

6. **Networking and Firewalls:**
   - Ensure that you allow HTTP and HTTPS traffic by checking the appropriate boxes under the "Firewall" section.

## Step 2: Understanding Free Trial Limitations

As part of the Google Cloud Free Trial, you are limited to:

- **1 Non-preemptible e2-micro VM instance** per month in the eligible regions (Oregon `us-west1`, Iowa `us-central1`, South Carolina `us-east1`).
- **30 GB-months of standard persistent disk storage**.
- **1 GB of outbound data transfer** from North America to all region destinations (excluding China and Australia) per month.

Make sure to stay within these limits to avoid any unexpected charges.

## Step 3: SSH into the VM

1. **Access the VM via SSH:**
   - Once the VM is created, you can SSH into it directly from the Google Cloud Console by clicking the **SSH** button next to your instance.

2. **Configure the VM:**
   - Once logged in, you can proceed with installing necessary software like Nginx, configuring firewall settings, and uploading your website files.

