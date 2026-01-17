# 🚗 GTA Online Weekly Update Bot

An automated Discord bot that monitors r/gtaonline for the latest Weekly Updates. It fetches bonuses, discounts, and podium vehicles and posts them beautifully into your Discord server.

---

## ✨ Features
Automated Scans: Checks for new updates every 60 minutes.

Smart Notifications: Pings a specific role only when a new update is detected.

Manual Query: Use the !weekly command to get the current event details instantly.

Persistence: Remembers the last posted update to prevent duplicate pings after a restart.

---

📋 Prerequisites
Python 3.8+ installed on your Linux system.

A Discord Bot Token (obtainable via the [Discord Developer Portal](https://discord.com/developers/applications)).

Privileged Gateway Intents: Ensure "Message Content Intent" is enabled in your Bot's settings on the Developer Portal.

---
🛠️ Installation
1. Install Required Libraries
Open your terminal or command prompt and run:
```
pip install discord.py aiohttp
```
2. Setup the Bot Script

Create a new folder for the bot.

Create a file named weekly_bot.py and paste the bot code into it.  (Code is in the weekly_bot.py.txt)

Create a file named last_weekly_link.txt in the same folder (leave it empty).

---

⚙️ Setup as a System Service (24/7 Uptime)
To ensure the bot runs 24/7 and restarts automatically after a server reboot, follow these steps to create a Linux Systemd service.

1. Create the Service File
Run the following command to create the service file (replace gta-bot with your preferred name):

```
sudo nano /etc/systemd/system/weekly_bot.service
```

2. Paste the Configuration
Copy and paste the following block into the editor. Adjust the paths to match your server setup:

```
[Unit]
Description=GTA Weekly Update Discord Bot
After=network.target

[Service]
# Replace 'user' with your Linux username
User=user
# Replace with the path to your bot folder
WorkingDirectory=/home/user/weekly_bot
# Replace with the path to your python executable and script
ExecStart=/usr/bin/python3 /home/user/weekly_bot/weekly_bot.py
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

3. Activate the Service
Run these commands to start the bot and enable it on boot:
```
# Reload systemd to recognize the new service
sudo systemctl daemon-reload

# Start the bot
sudo systemctl start weekly_bot

# Enable it to start automatically on boot
sudo systemctl enable weekly_bot
```

4. Useful Service Commands
Check Status: sudo systemctl status gta-bot

Restart Bot: sudo systemctl restart gta-bot

View Logs: journalctl -u weekly_bot -f

---

🕹️ Commands
!weekly - Manually fetches and displays the current Weekly Update.

---

📄 License
This project is open-source and free to use.
