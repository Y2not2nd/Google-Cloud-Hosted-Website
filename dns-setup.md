
# DNS Setup

This section covers the steps to purchase a domain, set up DNS in Google Cloud, and point your domain to your VM.

# Step 1: Purchase a Domain

1. # Choose a Domain Registrar:
   - Select a domain registrar like GoDaddy, Namecheap, or 123Reg.
   - Search for your desired domain name and complete the purchase.

2. # Access Your Domain Management:
   - After purchasing, log in to your domain registrar’s control panel.
   - Find the DNS management section where you can configure DNS records.

# Step 2: Create a DNS Zone in Google Cloud

1. **Log in to Google Cloud Console:**
   - Go to [Google Cloud Console](https://console.cloud.google.com/).

2. # Navigate to Cloud DNS:
   - In the left-hand menu, select **Network services** > **Cloud DNS**.
   - Click **Create Zone**.

3. # Create a New DNS Zone:
   - # Zone Name: Choose a name for your DNS zone (e.g., `mywebsite-zone`).
   - # DNS Name: Enter your domain name (e.g., `example.com`).
   - # DNSSEC: Leave as **Off** for now.
   - Click Create to set up the DNS zone.

4. # Note the Google Cloud Nameservers:**
   - After creating the DNS zone, Google Cloud will provide you with nameservers (e.g., `ns-cloud-a1.googledomains.com`, etc.).
   - You will use these in the next step.

# Step 3: Add Nameserver Records to Your Domain Registrar

1. # Log in to Your Domain Registrar:
   - Go back to your domain registrar’s control panel.

2. # Update Nameserver Records:
   - Find the option to change the nameservers for your domain.
   - Replace the existing nameservers with the Google Cloud nameservers obtained in the previous step.

3. # Save Changes:
   - After updating the nameservers, save the changes.
   - Note that DNS propagation may take some time (up to 48 hours).

# Step 4: Point the A Record to Your VM (because of the free trial limiations you must create a E2 VM in US Cen/East or West)

1. # Get the External IP Address of Your VM:
   - Go to Compute Engine > VM instances in Google Cloud Console.
   - Copy the external IP address of your VM.

2. # Add an A Record in Google Cloud DNS:
   - Go back to Cloud DNS and click on the zone you created.
   - # Click Add Record Set.
   - # Type: `A`
   - # TTL: Use the default value.
   - # IPv4 Address: Enter the external IP address of your VM.
   - Click Create to save the record.

3. # Verify DNS Propagation:
   - Use a tool like [DNSChecker](https://dnschecker.org/) to ensure that the `A` record has propagated globally and points to your VM’s IP (Can take up to 48 hours).


