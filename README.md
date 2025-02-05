# CloudFlare-DDNS

CloudFlare-DDNS is a lightweight and simple script designed to keep your Cloudflare DNS records up-to-date with your dynamic IP address. This project is particularly useful for users who have a dynamic IP (such as most home internet connections) and need to update their Cloudflare DNS entries automatically whenever their IP address changes.

Key Features:
Automatic IP updates: The script periodically checks your current public IP address and updates the corresponding DNS records on Cloudflare.
Simple setup: The script is easy to install and configure, requiring minimal setup.
Cron integration: It can be scheduled to run at regular intervals (e.g., every 5 minutes) using cron jobs to ensure your DNS records are always in sync with your dynamic IP.
Cloudflare API: The script leverages Cloudflare's API to update DNS records securely using API tokens.

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

### 4. Schedule the script to run periodically

Add the script to crontab to run it at regular intervals (e.g., every 5 minutes):
```bash
crontab -e
```

```bash
*/5 * * * * /opt/CloudFlare-DDNS/cloudflare-ddns.sh
```
