# AI Chatbot (local)

This small demo runs a frontend that sends user messages to a local Node backend. The backend is configured to forward messages to a Jemin-compatible API when `JEMIN_API_URL` is set. If no Jemin URL is configured the server responds with a local mock reply so the UI still works.

How to run

1. Open a terminal and change directory to the `JS` folder:

```powershell
cd "c:\Users\Alok\OneDrive\Desktop\Ai chatbot 1\JS"
npm install
npm start
```

2. Open `Index.html` in your browser (double-click or serve it). The frontend will POST to `http://localhost:3000/chat`.

Environment

Create `JS/.env` (or set environment variables) with the following values when you want to use a real Jemin service:

```
JEMIN_API_URL=https://your-jemin-endpoint.example.com/v1/respond
JEMIN_API_KEY=your_secret_key_here
```

Notes & assumptions

- The repo originally used OpenAI; this server now supports a generic Jemin endpoint. The server expects the remote to accept POST { message } and return JSON with a `reply` (or `message`) field. If the remote returns OpenAI-like choices we try to extract a reply.
- If no `JEMIN_API_URL` is configured, the server returns a mock reply for local testing.
- The server exposes both `/chat` and `/api/chat` for compatibility.

If you'd like, I can:
- Add a small static file server so `Index.html` can be served from the same process.
- Implement a specific adapter if you provide Jemin's API contract (URL + request/response example).
