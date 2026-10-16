# 🤖 Enterprise Meeting Productivity AI Agent

An AI-powered productivity assistant built using **n8n, OpenAI, Telegram, Gmail, Google Calendar, and Fireflies.ai** to automate meeting scheduling, email communication, and meeting transcript retrieval.

## 🚀 Project Overview

Managing workplace productivity often requires switching between calendars, email inboxes, meeting transcripts, and messaging applications.

This project demonstrates how an AI agent can connect these services into a unified workflow. Users can send natural-language requests through Telegram, and the agent can use configured tools to perform tasks such as scheduling meetings, sending emails, and retrieving meeting transcript information.

The objective is to simplify routine administrative tasks through AI-powered workflow automation.

## ✨ Features

- **Telegram Interface:** Accepts user requests through a Telegram bot.
- **AI Agent:** Interprets natural-language instructions and selects the appropriate connected tools.
- **Meeting Scheduling:** Uses Google Calendar to create calendar events.
- **Meeting Links:** Supports Google Meet link generation when configured.
- **Email Automation:** Uses Gmail to send meeting details and other requested messages.
- **Meeting Transcript Retrieval:** Connects to Fireflies.ai through its GraphQL API.
- **Dynamic Tool Inputs:** Supports AI-provided parameters for tool calls, such as transcript IDs.
- **Workflow Orchestration:** Connects multiple services through n8n.
- **Automated Notifications:** Reports task outcomes to the user through Telegram.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| n8n | Workflow orchestration and automation |
| OpenAI | Natural-language understanding and AI agent reasoning |
| Telegram Bot API | User interaction and notifications |
| Google Calendar API | Meeting scheduling |
| Gmail API | Email communication |
| Fireflies.ai GraphQL API | Meeting transcript retrieval |
| Google Meet | Online meeting links, when configured |

## ⚙️ How It Works

1. **User Request:** The user sends an instruction through Telegram.
2. **AI Processing:** The n8n AI Agent interprets the request and determines which tools are required.
3. **Tool Selection:** The agent uses connected services such as Google Calendar, Gmail, or Fireflies.ai.
4. **Action Execution:** The relevant workflow executes the requested operation.
5. **Result Collection:** The workflow collects the outcome from the connected service.
6. **Telegram Response:** The agent or workflow reports the result to the user.

## 🔄 Workflow Architecture

```text
           User
             |
             v
       Telegram Bot
             |
             v
        n8n AI Agent
             |
      +------+------+ 
      |      |      |
      v      v      v
 Google    Gmail  Fireflies.ai
 Calendar   API   GraphQL API
      |      |      |
      v      v      v
  Meetings Emails Transcripts
      |      |      |
      +------+------+
             |
             v
      Telegram Response
```

*This diagram represents the logical architecture. Actual tool connections depend on the implemented n8n workflows.*

## 💬 Example Use Cases

### 1. Schedule a Meeting

**User request:**

"Schedule a meeting with Rahul tomorrow at 3 PM and email him the meeting details."

**Workflow:**

1. The agent extracts the meeting details.
2. Google Calendar creates the event if the request is valid and the operation succeeds.
3. A Google Meet link is attached if the integration is configured.
4. Gmail sends the meeting details to the intended recipient.
5. Telegram reports the result to the user.

The agent should verify the date, timezone, recipient, and operation outcome before reporting success.

### 2. Retrieve Meeting Transcripts

The user requests information from a previous meeting.

**Workflow:**

1. The agent receives the transcript request.
2. The workflow obtains the relevant transcript ID.
3. A Fireflies.ai GraphQL request retrieves the transcript information.
4. The returned content can be used to answer the user's question, where supported.

### 3. Send Emails

The user requests an email through Telegram.

The agent identifies the recipient, subject, and message, then uses the configured Gmail integration to send it. Any necessary clarification or confirmation should happen before the email is sent.

### 4. Productivity Notifications

The workflow can send Telegram notifications about completed actions, meeting details, and other supported tasks.

## 🔧 Setup and Configuration

### Prerequisites

- An [n8n](https://n8n.io/) account or self-hosted instance
- An [OpenAI Platform](https://platform.openai.com/) account
- A Telegram bot created through [BotFather](https://t.me/BotFather)
- A Google account with the required Gmail and Google Calendar access
- A [Fireflies.ai](https://fireflies.ai/) account and API access, if using transcript retrieval

### Step 1: Configure Telegram

1. Create a bot using Telegram's BotFather.
2. Obtain the bot token.
3. Configure the Telegram trigger or integration in n8n.
4. Store the token securely in n8n credentials.

### Step 2: Configure the AI Agent

1. Create an n8n workflow with a Telegram trigger.
2. Add an AI Agent node.
3. Connect the OpenAI model.
4. Configure the system prompt to define the agent's role, tool usage, and response rules.

### Step 3: Connect Google Calendar and Gmail

1. Configure the required Google OAuth credentials.
2. Enable the relevant Google APIs if required.
3. Connect Google Calendar tools for creating and managing events.
4. Connect Gmail
