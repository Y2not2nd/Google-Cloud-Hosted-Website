### **Website Folder Structure**

When hosting a website on your VM, it's essential to organize your files in a clear and structured way. This helps manage your assets (like images, stylesheets, and scripts) and makes the site easier to maintain and scale.

#### **Example Website Folder Structure:**


## Project Directory Structure

```plaintext
/var/www/html/
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── script.js
└── images/
    └── logo.png

#### **Explanation of Each Folder:**

1. **`/var/www/html/`**
   - This is the root directory where your website files are stored. It’s the default directory that Nginx serves files from. The main `index.html` file usually resides here, and it serves as the homepage of your website.

2. **`index.html`**
   - This is the main HTML file for your website. When users visit your domain (e.g., `http://yourdomain.com`), this file is the first one served by the web server. You can have additional HTML files if your site has multiple pages.

3. **`/css/`**
   - This directory is where you store all your Cascading Style Sheets (CSS) files. CSS files define the styles of your website (e.g., layout, colors, fonts). The main stylesheet might be called `styles.css`, but you can name it anything relevant to your project.

4. **`/js/`**
   - This directory holds your JavaScript (JS) files. JavaScript is used to add interactivity to your website, such as animations, form validations, or dynamic content updates. The file `script.js` might contain custom scripts for your site.

5. **`/images/`**
   - This folder is where you store all images used on your website. You can have subdirectories within the `images` folder if you need to organize the images further (e.g., `/images/products/` for product images). The file `logo.png` is an example of an image you might use in your website’s header.

### **Setting Up SSH Key Pair for Secure File Transfers**

An SSH key pair consists of a public and private key. The private key stays on your local machine, while the public key is added to the server. This setup allows you to authenticate securely without needing a password.

#### **1. Generate SSH Key Pair on Your Local Machine**

1. **Generate the SSH Key Pair:**
   - On your local machine, open a terminal and run:
     ```bash
     ssh-keygen -t ed25519 -C "your_email@example.com"
     ```
   - **Explanation:**
     - `ssh-keygen`: The command to generate a new SSH key.
     - `-t ed25519`: Specifies the type of key to create (ed25519 is a newer, faster option).
     - `-C "your_email@example.com"`: Adds a comment with your email address, useful for identifying the key.

2. **Save the Key Pair:**
   - You will be prompted to save the key:
     - **Default Location:** Press `Enter` to save the key to the default location (`~/.ssh/id_ed25519`).
   - You can also set a passphrase for added security, though it’s optional.

3. **Set Correct Permissions on the Key:**
   - Ensure the private key has the correct permissions:
     ```bash
     chmod 600 ~/.ssh/id_ed25519
     ```
   - This command restricts access to the private key to only you.

#### **2. Manually Add the Public Key to Your VM**

1. **Copy the Public Key to the VM:**
   - SSH into your VM using the Google Cloud Console's browser-based SSH:
     - In the Google Cloud Console, navigate to **Compute Engine** > **VM instances**.
     - Click the **SSH** button next to your VM instance.
   - Once logged in, manually append the public key to the `authorized_keys` file on the VM:
     ```bash
     echo "your-public-key-content" >> ~/.ssh/authorized_keys
     ```

2. **Set Correct Permissions on the VM:**
   - Ensure the `.ssh` directory and `authorized_keys` file on the VM have the correct permissions:
     ```bash
     chmod 700 ~/.ssh
     chmod 600 ~/.ssh/authorized_keys
     ```

3. **Test SSH Access:**
   - From your local machine, test the connection to the VM using the SSH key:
     ```bash
     ssh -i ~/.ssh/id_ed25519 username@your-vm-ip
     ```
   - If successful, you should be logged into your VM without needing to enter a password.

### **Uploading Pictures from Your Local Device to the VM**

Once your SSH key pair is set up, you can securely upload files from your local machine to your VM using the `scp` command.

#### **Steps to Upload Files:**

1. **Prepare Your Files:**
   - On your local machine, ensure that the files you want to upload are organized. For example, place all images you want to upload into a directory like `C:/Users/YourName/Documents/webapp/images/`.

2. **Upload Files Using `scp`:**
   - Use the following command to upload the entire `images` directory to the VM’s `/var/www/html/images/` directory:
     ```bash
     scp -i ~/.ssh/id_ed25519 -r /c/Users/YourName/Documents/webapp/images/ username@your-vm-ip:/var/www/html/
     ```
   - **Explanation:**
     - `scp`: The command to securely copy files.
     - `-i ~/.ssh/id_ed25519`: Specifies the private key to use for authentication.
     - `-r`: Recursively copy entire directories.
     - `/c/Users/YourName/Documents/webapp/images/`: The path to the local directory containing your images.
     - `username@your-vm-ip:/var/www/html/`: The destination path on your VM where the files will be uploaded.

3. **Verify the Upload:**
   - After the upload, SSH into your VM to verify the files were uploaded correctly:
     ```bash
     ssh -i ~/.ssh/id_ed25519 username@your-vm-ip
     ```
   - Check that the files are in the correct directory:
     ```bash
     ls -l /var/www/html/images/
     ```
   - You should see the files listed in the `images` directory.
