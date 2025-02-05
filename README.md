# CloudFlare-DDNS

CloudFlare-DDNS is a simple script for updating DNS records in Cloudflare to keep them synced with your dynamic IP address.

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
