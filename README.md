# Personal AI Assistant with Telegram and Google Calendar

An easy to use AI assistant powered by n8n. It connects your Telegram chat with OpenAI, Google Tasks, and Google Calendar. You can send text or voice notes, check your daily tasks, and schedule events without leaving Telegram.

## What This Project Does

This project gives you a personal secretary inside Telegram. It uses two n8n workflow files:

1. Personal Assistant Using Telegram.json
This is the main assistant flow. It receives your messages on Telegram, listens to voice recordings, remembers recent conversations, and sends replies back to you.

2. My Google Calendar Agent Flow.json
This is the calendar helper flow. The main assistant calls this flow whenever you want to see calendar events or create a new event. You can also call it directly using a webhook.

## Main Features

* Voice and Text Support: Send normal text messages or record a quick voice note. The system converts your voice note into text automatically using OpenAI audio transcription.
* Memory of Past Messages: The assistant remembers what you said recently so you can chat naturally.
* Google Tasks Helper: Asks Google Tasks for your to do items and gives you a clean summary.
* Google Calendar Management: Adds new events with start and end times, or looks up your planned schedule.
* Two Workflows Working Together: The Telegram assistant talks directly to the Calendar assistant as a tool.

## How It Works

1. You send a voice note or text message to your Telegram bot.
2. If you sent a voice note, the workflow downloads the audio file and transcribes it into plain text.
3. The AI Agent reads your words using OpenAI.
4. The agent decides what you need:
   * If you ask about tasks, it calls the Google Tasks tool.
   * If you ask about meetings or calendar events, it calls the Google Calendar flow tool.
5. The Google Calendar flow creates the event or retrieves the list of events.
6. The assistant writes a polite, clean answer and sends it right back to your Telegram chat.

## Files Included

* Personal Assistant Using Telegram.json: The main entry workflow for Telegram interactions.
* My Google Calendar Agent Flow.json: The child workflow dedicated to Google Calendar actions.

## Prerequisites

Before setting up, make sure you have:

* An n8n instance installed and running
* A Telegram Bot token from BotFather
* An OpenAI API key
* A Google account connected to n8n with permissions for Google Tasks and Google Calendar

## Setup Instructions

### Step 1: Import Google Calendar Flow

1. Open your n8n workspace.
2. Click Add Workflow, then select Import from File.
3. Choose the file named My Google Calendar Agent Flow.json.
4. Open the OpenAI Chat Model node and select your OpenAI credentials.
5. Open the Google Calendar nodes and connect your Google Calendar account.
6. Save the workflow and switch it to Active.

### Step 2: Import Telegram Assistant Flow

1. In n8n, click Add Workflow, then select Import from File.
2. Choose the file named Personal Assistant Using Telegram.json.
3. Open the Telegram Trigger node and Telegram Send Message node, then connect your Telegram account credentials.
4. Open the Transcribe a recording node and OpenAI Chat Model node, then select your OpenAI credentials.
5. Open the Google Tasks tool node and connect your Google Tasks account.
6. Open the node named Call n8n Workflow Tool. Point it to the Google Calendar workflow you imported in Step 1.
7. Save the workflow and switch it to Active.

## Example Things You Can Say

* What tasks do I have for today?
* Add a meeting with the design team tomorrow at 4 PM.
* What events are planned on my calendar this week?
* Please show my completed tasks.

## Tips

* Keep both workflows set to Active so they can communicate smoothly.
* Make sure your Telegram bot privacy settings allow it to receive messages.
* When asking for meetings, include the day and time so the assistant sets the calendar correctly.
