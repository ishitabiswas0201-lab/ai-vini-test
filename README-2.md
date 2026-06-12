# AI Vini – Multi-Model AI Chat Template

A minimal, self-contained HTML chat interface that connects to multiple AI providers using your own API keys. No servers, no subscriptions, no vendor lock-in.

---

## What this is

A single HTML file you can open in any browser or host anywhere. It is a **frontend template**, not an AI service. You bring your own API keys; the providers charge you directly for usage.

**This template does not include AI API access.** Users must provide their own API keys and are responsible for any charges from their chosen providers.

---

## Supported providers

| Provider | Browser use | Notes |
|---|---|---|
| **Groq** | ✅ Fine | Fast inference, generous free tier. Good default choice. |
| **Google Gemini** | ✅ Fine with setup | Set an HTTP referrer restriction in Google Cloud Console to limit where your key works. |
| **Cohere** | ✅ Fine | Key is visible in DevTools. Set a spending limit on your Cohere dashboard. |
| **Mistral** | ✅ Fine | Key is visible in DevTools. Set a spending limit on your Mistral dashboard. |
| **OpenAI** | ⚠️ Advanced only | OpenAI recommends keys be used from a backend server, not directly from a browser. Use only with a restricted key and a hard spending cap. For serious projects, set up a proxy. |

---

## Getting started

### 1. Get API keys

Sign up at one or more of the providers above and create an API key. Free tiers are available at Groq and Gemini — good starting points with no cost.

- Groq: https://console.groq.com
- Google Gemini: https://aistudio.google.com/apikey
- Cohere: https://dashboard.cohere.com
- Mistral: https://console.mistral.ai
- OpenAI: https://platform.openai.com/api-keys

**Set a spending limit on every key before use.**

### 2. Open the template

Open `ai-vini.html` in any modern browser. No build step, no install, no server required.

### 3. Add your keys

Click **⚙ Keys** in the top right. Enter your API key for each provider you want to use, choose a model, and toggle it on. Click **Save & Close**.

Keys are stored in your browser's `localStorage`. They are not sent to any server other than the AI provider you are calling. They are stored unencrypted — only use this on devices you personally control.

### 4. Start chatting

Type a question and press Enter or click Send. If you have multiple providers enabled, they all respond in parallel and the result is synthesized into a single answer. Turn off **Smart Synthesis** in settings to skip that step and save API credits.

---

## Security — please read

This template makes API calls directly from your browser. This means:

- Your API key is visible in browser DevTools (Network tab).
- Any browser extension running on the page can read it.
- `localStorage` is not encrypted.

**This is acceptable for personal use on your own device.** It is not suitable for:

- Shared computers
- Public-facing deployments where other people use the interface
- Production commercial applications

For those use cases, you need a backend proxy that holds the API keys server-side and forwards requests. The template is designed to make that swap easy — just change the fetch URLs to point at your proxy.

---

## Hosting

Because it's a single HTML file, you can host it anywhere static files are served:

- Drag into **Netlify Drop** (netlify.com/drop) for instant hosting
- Push to a repo and enable **GitHub Pages**
- Upload to any web host or S3 bucket
- Open locally from your filesystem — no server needed

---

## Customisation

The system prompt that shapes the AI's personality lives in the `synthesize()` function near the bottom of the script. Change it to whatever tone fits your use case — professional assistant, customer support agent, coding helper, etc.

```js
const systemPrompt = 'You are AI Vini. Brutally honest, zero fluff...';
```

---

## What this is not

- Not a SaaS product — there is no backend, no user accounts, no billing system.
- Not a secure key vault — keys live in the browser.
- Not a managed AI service — you pay your providers directly.

It is a **BYOK (Bring Your Own Keys) chat UI template**. Market it as exactly that.

---

## License

You may use, modify, and redistribute this template. The author provides the interface only and is not responsible for third-party API costs, usage policies, or misuse of user-provided API keys.
