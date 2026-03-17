# Weather Notification Workflow

An automated daily weather briefing system built with [n8n](https://n8n.io) —
a no-code/low-code workflow automation platform widely used by SaaS operations
and customer success teams.

## What It Does

This workflow runs on a daily schedule and delivers a personalized weather
summary via notification (SMS, email, or Slack webhook). It demonstrates
the core automation pattern used by SaaS onboarding teams: a scheduled
trigger → API data fetch → conditional logic → formatted notification output.

### Workflow Steps

1. **Schedule Trigger** — Fires at a configured time each morning
2. **HTTP Request Node** — Calls the OpenWeatherMap API for a target location
3. **Conditional Logic** — Evaluates weather conditions (rain, extreme temps, wind)
4. **Notification Node** — Sends a formatted summary via your chosen channel

## Why This Exists

n8n is one of the most common automation tools used by SaaS companies to build
internal onboarding workflows — welcome email sequences, milestone alerts,
health score triggers, and customer lifecycle automations. This project
demonstrates that I can build, read, and modify these workflows, which is
directly relevant to SaaS operations and customer onboarding roles.

If you work in SaaS, you'll recognize this pattern immediately: it's the same
structure as "send a Slack alert when a customer hasn't logged in for 7 days"
or "trigger an onboarding email when a user completes their first integration."

## Workflow Screenshot

> _Screenshot of the n8n workflow canvas — add `workflow-screenshot.png` to
> this repo and uncomment the line below_

<!-- ![Workflow Canvas](workflow-screenshot.png) -->

## Tech Stack

| Component | Technology |
|---|---|
| Workflow engine | n8n (self-hosted or n8n Cloud) |
| Weather data | OpenWeatherMap API (free tier) |
| Notification | Configurable: Email / SMS / Slack webhook |
| Schedule | Cron-based trigger (configurable time) |

## Files

```
workflows/
└── weather-notification.json    # Import this into n8n
README.md
SETUP.md                         # Full setup instructions
```

## Quick Setup

See [SETUP.md](SETUP.md) for full instructions. Short version:

1. Install n8n: `npm install -g n8n`
2. Get a free OpenWeatherMap API key at https://openweathermap.org/api
3. Start n8n: `n8n start`
4. Import `workflows/weather-notification.json`
5. Add your API key and notification credentials in n8n
6. Activate the workflow

## Customization

The workflow JSON is exported from n8n and can be imported into any n8n instance.
To modify it:

1. Import into n8n
2. Edit nodes visually in the canvas
3. Re-export and replace the JSON file in this repo

## Related

- [restaurant-ai-chatbot](https://github.com/Erics38/restaurant-ai-chatbot) —
  Conversational AI ordering system using FastAPI and Docker
