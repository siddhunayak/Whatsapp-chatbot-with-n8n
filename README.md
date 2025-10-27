
# WhatsApp AI Chatbot Setup Guide

This project demonstrates how to build a **WhatsApp AI Assistant** using **n8n**, **Meta’s WhatsApp Cloud API**, and **OpenAI**.
It walks you through creating and connecting your **Facebook Business Account**, **Meta App**, and **WhatsApp API**, then integrating everything with **n8n** for intelligent, real-time chat automation.

---

## 🚀 Features

* WhatsApp Cloud API integration
* Seamless connection with n8n workflow automation
* AI-powered conversational responses using OpenAI
* Real-time message handling (send/receive)
* Memory-based context for short conversations

---

## 🧩 Prerequisites

Before starting, ensure you have:

* A [Facebook account](https://www.facebook.com/)
* A [Facebook Business account](https://business.facebook.com/)
* Access to [Meta Developer Dashboard](https://developers.facebook.com/)
* A verified WhatsApp number
* An [n8n](https://n8n.io/) account
* An [OpenAI API key](https://platform.openai.com/)

---

## ⚙️ Step 1 — Create Facebook Business Account

1. Visit [business.facebook.com](https://business.facebook.com/)
2. Log in and create a **new business portfolio**
3. Enter business name, personal name, and contact email

This acts as the workspace for your app, WhatsApp API, and integrations.

---

## 🧱 Step 2 — Create Meta App

1. Go to [developers.facebook.com](https://developers.facebook.com/)
2. Click **My Apps → Add → Create a New App ID**
3. Choose:

   * **Use case** → *Other*
   * **App type** → *Business*
4. Fill in app name and email, then confirm your Facebook password.

---

## 🔑 Step 3 — Get App Credentials

Navigate to **App Settings → Basic**, and note:

* **App ID**
* **App Secret**

Keep these safe — they’ll be used in n8n.

---

## 💬 Step 4 — Connect WhatsApp to the App

1. In your app dashboard, click **Add Product → WhatsApp → Set Up**
2. Go to the **Quick Start** page and click **Start Using the API**
3. Copy:

   * **WhatsApp Business Account ID**
   * **Phone Number ID**
   * **Temporary Access Token**

---

## 📞 Step 5 — Add and Verify WhatsApp Number

1. Scroll to the **Send a Message** section
2. Add your WhatsApp number and verify it using the received code
3. Generate a new **Access Token**

---

## 🔄 Step 6 — Set Up n8n Workflow

### 1. **Receive Message Node**

* Node: **WhatsApp (On Message)**
* Input:

  * App ID
  * App Secret

This node listens for incoming messages.

### 2. **Send Message Node**

* Node: **WhatsApp (Send Message)**
* Input:

  * Access Token
  * Business Account ID

Click **Test Connection** to confirm — you should see “Connection Successful.”

---

## 🧠 Step 7 — Add OpenAI Node

Place the **OpenAI node** between your WhatsApp receive/send nodes.

### Example prompt:

```
You are an intelligent, friendly, and interactive WhatsApp chatbot.
Your goal is to understand the user's question and respond clearly,
accurately, and conversationally. Keep answers short (2–4 lines),
polite, and natural, just like a real chat.
```

### Example Conversation:

```
User: Hey!
Bot: Hey there 👋 How can I help you today?
```

### Input Message:

Use:

```
{{ $json.messages[0].text.body }}
```

### Add Simple Memory

This allows the bot to “remember” recent chat context (temporary memory).

---

## 🔁 Final Workflow Overview

1. **On Message (WhatsApp)** → receives user text
2. **OpenAI Node** → processes input and generates reply
3. **Send Message (WhatsApp)** → delivers response to the user

---

## ✅ Summary

Congratulations! 🎉
You’ve successfully built your own **AI-powered WhatsApp Chatbot** using:

* **Meta’s WhatsApp Cloud API**
* **n8n automation**
* **OpenAI conversational intelligence**

