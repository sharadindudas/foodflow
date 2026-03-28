# FoodFlow

A modern food ordering web application built with React — delivering a seamless experience with real-time restaurant data, cart management, authentication, and payments.

**Live Demo → [https://foodflow-remo.vercel.app](https://foodflow-remo.vercel.app)**

---

## Overview

FoodFlow is a frontend-focused project that demonstrates production-grade architecture — including a custom BFF API Gateway for handling external API communication, Firebase-based authentication, and Razorpay payment integration.

```
Frontend (React + Redux)
        ↓
API Gateway BFF (Express Proxy)
        ↓
External Food APIs (Swiggy)
```

---

## Features

- **Authentication** — Google login via Firebase Authentication
- **Real-Time Data** — Live restaurant listings and menus fetched through a custom BFF proxy
- **Cart System** — Add, update, and remove items with Redux state management
- **Checkout Flow** — Clean order summary and checkout experience
- **Payment Integration** — Razorpay frontend integration for smooth transactions

---

## Tech Stack

- React.js
- Redux Toolkit
- Tailwind CSS
- ShadCN UI
- Firebase Authentication
- Razorpay
- Bun

---

## Getting Started

### Prerequisites

- Node.js & Bun
- Firebase project with Google Auth enabled
- Razorpay account
- FoodFlow API Gateway running locally or deployed

### Installation

```bash
git clone https://github.com/sharadindudas/foodflow.git
cd foodflow
bun install
```

### Environment Variables

Create a `.env` file in the root:

```env
VITE_FIREBASE_API=your_key
VITE_FIREBASE_AUTHDOMAIN=your_domain
VITE_PROJECT_ID=your_project
VITE_STORAGE_BUCKET=your_bucket
VITE_MESS_SEND_ID=your_sender_id
VITE_APP_ID=your_app_id

VITE_RAZORPAY_KEY_ID=your_key
VITE_RAZORPAY_KEY_SECRET=your_secret

VITE_BASE_URL=http://localhost:3001/
```

### Run

```bash
bun run dev
```

Open → [http://localhost:5173](http://localhost:5173)

---

## API Gateway (BFF)

FoodFlow routes all external API calls through a custom **Backend-for-Frontend (BFF) API Gateway** to bypass browser CORS restrictions.

**Gateway Repository → [foodflow-api-gateway](https://github.com/sharadindudas/foodflow-api-gateway)**

### Running the Gateway Locally

```bash
git clone https://github.com/sharadindudas/foodflow-api-gateway.git
cd foodflow-api-gateway
npm install
npm run dev
```

Gateway runs at `http://localhost:3001`

### Why This Architecture?

```js
// Blocked by CORS — fails in browser
fetch("https://www.swiggy.com/dapi/restaurants/list/v5");

// Routed through BFF — works
fetch("http://localhost:3001/api/proxy/swiggy/dapi/restaurants/list/v5");
```

The BFF layer handles path rewriting, header transformation, and CORS — keeping the frontend clean and decoupled from API internals.

---

## Production Setup

Update `.env` to point to your deployed gateway:

```env
VITE_BASE_URL=https://your-deployed-gateway.railway.app/
```

---

## License

MIT License

---

## Author

**Sharadindu Das** — [GitHub](https://github.com/sharadindudas) · [sharadindudas774@gmail.com](mailto:sharadindudas774@gmail.com)
