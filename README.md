# N8N Project

This repository contains n8n workflows for automation.

## Project Structure

```
.
├── workflows/          # n8n workflow JSON files
├── credentials/        # Credential templates (no actual credentials!)
└── README.md          # This file
```

## Setup

1. Install n8n:
   ```bash
   npm install -g n8n
   ```

2. Start n8n:
   ```bash
   n8n start
   ```

3. Import workflows:
   - Open n8n in your browser (usually http://localhost:5678)
   - Go to Workflows > Import from File
   - Select the workflow JSON files from the `workflows/` folder

## Workflows

Add descriptions of your workflows here.

## Important Notes

- **Never commit actual credentials** - The `.gitignore` file excludes the credentials folder
- Workflow files are exported from n8n as JSON
- Make sure to export workflows regularly to keep this repository up to date

## Usage

To export a workflow from n8n:
1. Open the workflow in n8n
2. Click the three dots menu (⋮)
3. Select "Download"
4. Save the JSON file to the `workflows/` folder

## Contributing

When adding new workflows:
1. Export the workflow as JSON
2. Save it to the `workflows/` folder
3. Commit and push to this repository
