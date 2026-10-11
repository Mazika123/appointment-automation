# Appointment Automation

An appointment scheduling automation workflow built with **n8n**. This project demonstrates how to connect form submissions, Google Calendar, Google Sheets, and Gmail to automate appointment management and follow-up tasks.

## Overview

The workflow is designed to reduce manual work involved in receiving appointment requests, checking calendar availability, managing appointment records, and sending email notifications.

It also includes a scheduled workflow for processing records stored in Google Sheets.

## Tech Stack

- **n8n** — Workflow automation and orchestration
- **Google Calendar** — Calendar event lookup and creation
- **Google Sheets** — Appointment data storage and tracking
- **Gmail** — Email notifications
- **JavaScript** — Data transformation and workflow logic

## Workflow Preview

![Appointment Automation Workflow](screenshots/workflow.png)

## Workflow Architecture

### 1. Appointment Request Processing

The main workflow starts when a user submits a form.

1. **On Form Submission** — Receives the submitted appointment information.
2. **Code in JavaScript** — Processes or transforms the incoming data.
3. **Edit Fields** — Organizes the data for subsequent nodes.
4. **IF** — Routes the execution based on a configured condition.
5. **Date & Time** — Prepares date and time information.
6. **Google Calendar: Get Many Events** — Retrieves calendar events for availability checks.
7. **Code in JavaScript** — Applies additional data-processing logic.
8. **IF** — Selects the appropriate branch based on the configured condition.
9. **Google Calendar: Create an Event** — Creates a calendar event on the applicable branch.
10. **Google Sheets: Append or Update Row** — Records or updates appointment information.
11. **Gmail: Send a Message** — Sends an email notification.

The workflow also contains additional branches for handling data and sending email messages.

### 2. Scheduled Follow-up Workflow

A separate workflow runs from a Schedule Trigger.

1. **Schedule Trigger** — Starts the workflow according to its configured schedule.
2. **Google Sheets: Get Row(s)** — Retrieves records from the spreadsheet.
3. **Code in JavaScript** — Processes the retrieved records.
4. **Gmail: Send a Message** — Sends an email based on the workflow's configured logic.
5. **Google Sheets: Update Row** — Updates the corresponding spreadsheet record.

The exact conditions, scheduling frequency, and notification rules depend on the node configurations.

## Key Concepts Demonstrated

- Event-driven workflow automation
- Form-triggered workflows
- Conditional branching with IF nodes
- JavaScript-based data transformation
- Google Calendar integration
- Google Sheets data management
- Automated email notifications
- Scheduled workflow execution
- Connecting multiple services in a single automation

## Prerequisites

Before running the workflow, you will need:

- A working n8n instance
- A Google account
- Access to Google Calendar
- A Google Sheets spreadsheet
- Gmail access
- The required Google service credentials configured in n8n

## Setup Instructions

### 1. Import the Workflow

1. Download `appointment-automation.json` from this repository.
2. Open your n8n instance.
3. Import the JSON file using the workflow import option.
4. Review all imported nodes and their connections.

### 2. Configure Credentials

Create or select the required credentials for Google Calendar, Google Sheets, and Gmail.

Do not upload credentials, access tokens, API keys, or private environment variables to GitHub.

### 3. Configure the Nodes

Review the following settings before testing:

- Form fields and expected input data
- JavaScript code and data mappings
- Date and time handling
- Calendar selection and event lookup criteria
- Google Sheets document, sheet, and column mappings
- Gmail recipients, subject lines, and message content
- Schedule Trigger frequency
- IF node conditions and branch behavior

### 4. Test the Workflow

1. Execute the workflow in test mode.
2. Submit a test appointment request.
3. Verify that the correct branch executes.
4. Check Google Calendar for the expected event.
5. Confirm that the appropriate spreadsheet rows are created or updated.
6. Verify that emails are sent as intended.
7. Test the scheduled workflow separately.

Use test data and verify the behavior of each branch before enabling production execution.

## Repository Structure

```text
appointment-automation/
├── appointment-automation.json
├── README.md
├── .gitignore
└── screenshots/
    └── workflow.png
```

## Security Notes

- Never commit Google OAuth tokens, passwords, API keys, or private credentials.
- Review exported workflow JSON files before publishing them.
- Remove personal email addresses and private spreadsheet identifiers when appropriate.
- Use test accounts and sample data when demonstrating the workflow.
- Keep local n8n configuration and credential files out of the repository.

## Limitations

This repository documents an automation workflow, not a complete appointment-booking application.

Successful execution depends on valid service credentials, correct node configuration, and the availability of the connected Google services. Appointment availability and conflict prevention should be tested against the actual calendar logic.

## Learning Objectives

This project is part of my hands-on learning journey with n8n and workflow automation.

It provides practical experience with workflow orchestration, integrations, conditional logic, data processing, and scheduled tasks.

## License

This project is available for educational and portfolio purposes. No license is granted for reuse unless a license is added to this repository.