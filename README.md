# Local LLM Chat (Ollama + Node.js + Web UI)

This project shows **how to run a Large Language Model (LLM) locally**, expose it via a backend API, and serve a **ChatGPT‑like frontend** that can be accessed **locally or publicly**.

You will learn:

* How to run an LLM locally using **Ollama**
* How to build a **Node.js backend** that talks to the LLM
* How to serve a **modern chat frontend** (desktop + mobile)
* How to expose everything to the public using **ngrok**

---

## 📁 Project Structure

```
LLM_Local/
│
├── backend/
│   ├── server.cjs        # Express backend (API)
│   ├── package.json
│   └── node_modules/
│
├── frontend/
│   └── index.html        # ChatGPT-like frontend
│
└── README.md
```

---

## 🧠 Prerequisites

Install the following before starting:

### 1️⃣ Node.js

* Download from: [https://nodejs.org](https://nodejs.org)
* Recommended: **Node 18+**

Verify:

```bash
node -v
npm -v
```

---

### 2️⃣ Ollama

Ollama is used to run LLMs locally.

Download:
👉 [https://ollama.com](https://ollama.com)

Verify:

```bash
ollama --version
```

---

### 3️⃣ Pull an LLM Model

Example (Llama 3):

```bash
ollama pull llama3
```

Run once to test:

```bash
ollama run llama3
```

Ollama runs by default on:

```
http://localhost:11434
```

---

## 🚀 Backend Setup (Node.js API)

### Step 1: Go to backend folder

```bash
cd backend
```

### Step 2: Install dependencies

```bash
npm install
```

### Step 3: Start the backend server

```bash
node server.cjs
```

You should see:

```
Server running on http://localhost:3000
```

### API Endpoint

```http
POST /api/chat
```

Example request:

```json
{
  "prompt": "Explain AI simply"
}
```

---

## 🎨 Frontend Setup (Chat UI)

### Step 1: Open frontend

Simply open:

```
frontend/index.html
```

in your browser **OR** serve it through backend (recommended).

---

## 💬 Features

* ChatGPT‑style UI
* Desktop & Mobile responsive
* Enter key to send message
* Shift + Enter for new line
* Typing indicator
* New chat reset

---

## 🌍 Serve Publicly using ngrok

### Step 1: Install ngrok

[https://ngrok.com/download](https://ngrok.com/download)

Login:

```bash
ngrok config add-authtoken YOUR_TOKEN
```

---

### Step 2: Expose Backend

If backend runs on **port 3000**:

```bash
ngrok http 3000
```

You will get a public URL like:

```
https://abcd-1234.ngrok-free.app
```

---

### Step 3: Update Frontend API URL (Optional)

In `index.html`, update fetch:

```js
fetch("https://abcd-1234.ngrok-free.app/api/chat", { ... })
```
Or keep it as "http://localhost:3000/api/chat" (Not suggested for production)

 #### **Now anyone can chat with your local LLM from anywhere** 🌎

---

## 🔐 Security Note

This setup is for **learning & demos only**.

If exposing publicly:

* Add rate limiting
* Add authentication
* Avoid exposing powerful models without limits

---

## 🛠 Common Issues

### ❌ Cannot GET /

Backend is API-only. Open `index.html` directly or serve static files.

### ❌ 405 Method Not Allowed

Use **POST**, not GET:

```bash
POST /api/chat
```

### ❌ Ollama not found

Restart terminal or reinstall Ollama.

---

## 📌 Future Improvements

* User authentication
* Chat history storage
* Streaming responses
* Docker deployment
* HTTPS production hosting

---

## 🙌 Credits

Built by **Salman**

Powered by:

* Ollama
* Llama 3
* Node.js
* Express

---

## ⭐ Star the Repo

If this helped you learn **local LLM deployment**, give it a ⭐ on GitHub!

Happy hacking 🚀
