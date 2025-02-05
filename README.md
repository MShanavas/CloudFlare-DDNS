# CloudFlare-DDNS

CloudFlare-DDNS is a lightweight and simple script designed to keep your Cloudflare DNS records up-to-date with your dynamic IP address. This project is particularly useful for users who have a dynamic IP (such as most home internet connections) and need to update their Cloudflare DNS entries automatically whenever their IP address changes.

Key Features:
Automatic IP updates: The script periodically checks your current public IP address and updates the corresponding DNS records on Cloudflare.
Simple setup: The script is easy to install and configure, requiring minimal setup.
Cron integration: It can be scheduled to run at regular intervals (e.g., every 5 minutes) using cron jobs to ensure your DNS records are always in sync with your dynamic IP.
Cloudflare API: The script leverages Cloudflare's API to update DNS records securely using API tokens.

# CloudFlare-DDNS Setup

## Step 1: Create a Cloudflare API Token

To allow the script to update DNS records on your behalf, you need to create an API token in your Cloudflare account. Here's how to do it:

### Steps to Create API Token:

1. **Log in to Cloudflare**:
   Go to [Cloudflare's login page](https://dash.cloudflare.com/login) and log in to your account.

2. **Navigate to the API Tokens page**:
   - Click on your **profile icon** (top right corner).
   - Select **My Profile**.
   - On the left sidebar, click on **API Tokens**.

3. **Create an API Token**:
   - Click on **Create Token**.
   - Select the **"Edit DNS"** template to grant the script permissions to modify your DNS records.

4. **Configure Token Permissions**:
   - Ensure that the permissions are set to allow **DNS Edit** and **Zone Edit** for your domains.
   - Follow the instructions to create the token.
   - **Copy the API Token**—this will be needed in the script.

### Token Permissions Example:


## Step 2: Obtain Cloudflare Zone ID

The **Zone ID** is the unique identifier for your Cloudflare domain, and it’s required for the script to know which DNS zone to update.

### Steps to Obtain the Zone ID:

1. **Log in to Cloudflare**:
   Go to [Cloudflare's dashboard](https://dash.cloudflare.com/login) and log in.

2. **Select Your Website**:
   From the dashboard, select the website you want to update.

3. **Find the Zone ID**:
   - In the top-right corner of the site dashboard, click on the **Overview** tab.
   - Scroll down to the **API** section.
   - Your **Zone ID** will be listed there.

4. **Copy the Zone ID**:
   - Copy the **Zone ID** (this will be needed in the script configuration).



## Installation

Follow these steps to set up the script on your server:

### 1. Download the script

Clone the repository to the `/opt/` directory:
```bash
cd /opt/
sudo git clone https://github.com/MShanavas/CloudFlare-DDNS.git
```
### 2. Make the script executable
```bash
cd /opt/CloudFlare-DDNS
sudo chmod +x cloudflare-ddns.sh
```
### 3. Configure the script

Before running the script, you'll need to configure it with your Cloudflare credentials. Follow the instructions in the script or read the configuration section in the repository.
Now that you have the **API Token** and **Zone ID**, you can configure the `cloudflare-ddns.sh` script.

### Example Configuration in `cloudflare-ddns.sh`:

```bash
# Cloudflare API Token
CF_API_TOKEN="your-cloudflare-api-token"

# Cloudflare Zone ID
CF_ZONE_ID="your-cloudflare-zone-id"

# DNS Record to Update
CF_RECORD_NAME="example.com"
```
### 4. Schedule the script to run periodically

Add the script to crontab to run it at regular intervals (e.g., every 5 minutes):
```bash
crontab -e
```

```bash
*/5 * * * * /opt/CloudFlare-DDNS/cloudflare-ddns.sh
```
