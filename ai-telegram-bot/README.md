# AI Telegram Bot – Text & Image Generator

Automation workflow built with **n8n** that allows users to generate **AI text and images directly in Telegram**.  
The bot can create social media posts, chat responses, and images based on user prompts.

Before publishing generated content, the system includes an **admin approval step** to ensure quality and moderation.

---

## Features

- AI text generation
- AI image generation
- Telegram bot interaction
- Content moderation with **Approve / Decline**
- Automated publishing to Telegram channels
- Prompt processing and validation

---

## Workflow Overview

The automation processes user messages from Telegram, determines the request type (text or image), generates AI content, and sends it for admin approval before publishing.

![Workflow](workflow.png)

---

## Telegram Interaction

Example of interaction with the bot where a user requests content and receives generated responses.

![Telegram Chat](telegram-chat.png)

---

## Image Generation Examples

AI-generated images created from user prompts.

![AI Image](image-generation.png)

![AI City](city-generation.png)

---

## How It Works

1. User sends a message to the Telegram bot.
2. The workflow detects whether the user requests:
   - text generation
   - image generation
3. AI generates the requested content.
4. Generated content is sent to the admin for review.
5. Admin can **Approve** or **Decline** the content.
6. Approved content is automatically published to the channel.

---

## Technologies

- **n8n** – automation workflow engine  
- **Telegram Bot API** – bot interaction  
- **AI APIs** – text and image generation  
- **Webhook triggers** for real-time automation

## Use Cases

This automation can be used for:

- social media content generation
- marketing content automation
- Telegram community management
- AI-powered chat assistants

---

## Author

Automation workflow developed as part of an AI and automation portfolio project.
