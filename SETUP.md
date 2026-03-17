# Setup Guide — Weather Notification Workflow

## Prerequisites

| Requirement | Notes |
|---|---|
| n8n | Install via npm, Docker, or use n8n Cloud |
| OpenWeatherMap API key | Free at https://openweathermap.org/api |
| Notification service | Email (SMTP), Twilio (SMS), or Slack webhook URL |

## Step 1: Install n8n

**Option A — npm (simplest):**
```bash
npm install -g n8n
n8n start
```
Access at: http://localhost:5678

**Option B — Docker:**
```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
```

**Option C — n8n Cloud:**
Sign up at https://n8n.io — no installation required.

## Step 2: Get an OpenWeatherMap API Key

1. Go to https://openweathermap.org/api
2. Create a free account
3. Navigate to API Keys in your profile
4. Copy the default key (or create a new one)

The free tier allows 1,000 calls/day — more than enough for a daily workflow.

## Step 3: Import the Workflow

1. Open n8n in your browser (http://localhost:5678)
2. Click **Workflows** in the left sidebar
3. Click **Import from File**
4. Select `workflows/weather-notification.json` from this repository
5. The workflow will open in the canvas editor

## Step 4: Configure Credentials

In n8n, credentials are stored separately from workflows. You'll need to
set up two credentials:

**OpenWeatherMap API:**
1. Click the HTTP Request node in the workflow
2. Click **Add Credential**
3. Select **Header Auth**
4. Name: `OpenWeatherMap`
5. Header Name: `appid`
6. Header Value: `[your API key]`

**Notification Credential (choose one):**

*Slack:*
1. Create an Incoming Webhook at https://api.slack.com/messaging/webhooks
2. In n8n, click the notification node
3. Add a Slack credential with your webhook URL

*Email (SMTP):*
1. Click the notification node
2. Add an SMTP credential with your email provider settings

## Step 5: Configure Your Location

In the workflow, find the HTTP Request node that calls the OpenWeatherMap API.
Update the URL parameter `q` to your city:

```
https://api.openweathermap.org/data/2.5/weather?q=Seattle,US&units=imperial
```

## Step 6: Set the Schedule

Click the Schedule Trigger node and set your preferred time.
Default: 7:00 AM daily.

## Step 7: Activate the Workflow

1. Click the toggle in the top-right corner of the canvas
2. Status should change to **Active**
3. The workflow will now run on schedule

## Verifying It Works

To test without waiting for the schedule:
1. Click the Schedule Trigger node
2. Click **Execute Node**
3. Follow the execution through each subsequent node

Check **Executions** in the left sidebar to see run history and any errors.

## Troubleshooting

**API returns 401:**
Your OpenWeatherMap key is invalid or not yet activated (new keys take ~2 hours).

**City not found:**
Use the format `CityName,CountryCode` — e.g., `Seattle,US` or `London,GB`.

**Notifications not sending:**
Check the credential configuration in the notification node. Test credentials
using the **Test** button in the credential setup modal.
