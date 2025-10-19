# Setup Guide for Weather Notification Workflow

This guide will help you set up the Weather Notification workflow with your own credentials.

## Prerequisites

1. **n8n installed** - Install globally with `npm install -g n8n`
2. **OpenWeatherMap API Key** - Sign up at https://openweathermap.org/api
3. **Telegram Bot Token** - Create a bot using @BotFather on Telegram

## Step 1: Get OpenWeatherMap API Key

1. Go to https://openweathermap.org/api
2. Sign up for a free account
3. Navigate to API Keys section
4. Generate a new API key
5. Copy the API key (you'll need it later)

## Step 2: Set Up Telegram Bot

1. Open Telegram and search for @BotFather
2. Send `/newbot` and follow the instructions
3. Copy the bot token provided by BotFather
4. Get your Chat ID:
   - Send a message to your bot
   - Visit: `https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getUpdates`
   - Find your chat ID in the response

## Step 3: Configure n8n Workflow

1. Start n8n: `n8n start`
2. Open n8n in your browser (usually http://localhost:5678)
3. Import the workflow:
   - Go to Workflows > Import from File
   - Select `workflows/WeatherNotification.json`

4. **Replace placeholders in HTTP Request nodes:**
   - Find all HTTP Request nodes (4 nodes for different cities)
   - Replace `YOUR_OPENWEATHERMAP_API_KEY` with your actual API key

5. **Configure Telegram credentials:**
   - Click on "Send a text message" node
   - Click "Credentials" > "Create New"
   - Enter your Telegram bot token
   - Save the credential

6. **Update Chat IDs:**
   - In both "Send a text message" nodes
   - Replace `YOUR_TELEGRAM_CHAT_ID_1` and `YOUR_TELEGRAM_CHAT_ID_2` with your actual Telegram chat IDs

7. Save the workflow

## Step 4: Test the Workflow

1. Click "Execute Workflow" in n8n
2. Check if you receive the weather notification on Telegram
3. If successful, activate the workflow to run on schedule

## Important Security Notes

- **NEVER commit your actual API keys or tokens to Git**
- Keep your credentials in n8n's credential manager
- The workflow file in this repository uses placeholders only
- When exporting workflows to share, always sanitize sensitive data first

## Workflow Schedule

The workflow is scheduled to run daily at 10:07 AM (configured in the Schedule Trigger node).
You can modify this schedule in the n8n workflow editor.

## Cities Monitored

- Berlin, Germany
- Seattle, USA
- Tallinn, Estonia
- Kamianets-Podilskyi, Ukraine

You can modify these cities by editing the HTTP Request nodes' URLs.
