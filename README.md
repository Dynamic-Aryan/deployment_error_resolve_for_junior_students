# ⚛️ React SPA Deployment Guide (with Routing Fixes for Vercel & Netlify)

This project is a **React Single Page Application (SPA)** using client-side routing via **React Router**. This guide explains how to fix the common **404 "Page Not Found" errors** that occur on **Vercel** and **Netlify** when refreshing or directly accessing a route like `/about` or `/dashboard`.

---

## 🧠 Why the 404 Error Happens

React SPAs use **client-side routing**, which means:
- All routes are handled **within the app** (via JavaScript).
- When you refresh a non-root URL (like `/dashboard`), the host tries to load a file from the server that doesn't exist → **404 Error**.

---

## ✅ Fix for Vercel

Vercel uses a file called `vercel.json` for route rewriting.

### 🔧 Step-by-step:

1. **Create a `vercel.json`** file in the **root** of your project (same level as `package.json`).

```json

{
  "rewrites": [
    { "source": "/(.*)", "destination": "/" }
  ]
}

my-app/
├── public/
│   └── index.html
├── src/
│   └── App.js
├── vercel.json       ✅ Add this
├── package.json
└── ...



/*    /index.html   200

my-app/
├── public/
│   ├── index.html
│   └── _redirects     ✅ Add this
├── src/
├── package.json
└── ...


npm run build
