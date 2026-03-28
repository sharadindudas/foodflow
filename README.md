# 🌶️ **FoodFlow 🚀**

> A modern **food ordering web application** delivering a seamless, real-time user experience with authentication, payments, and scalable architecture.

---

## ✨ Features

- 🔐 **Authentication**
  Secure Google login powered by Firebase Authentication

- 🍽️ **Real-Time Data Integration**
  Fetch and display live restaurant menus and listings

- 🛒 **Smart Cart System**
  Add, update, and remove items dynamically

- ✅ **Checkout Experience**
  Clean and intuitive order summary & checkout flow

- 💳 **Payment Integration**
  Razorpay frontend integration for smooth transactions

- 🌐 **API Gateway Integration**
  Uses a custom Backend-for-Frontend (BFF) proxy to handle API communication and CORS

---

## 🏗️ Architecture Overview

```
Frontend (React + Redux)
        ↓
API Gateway BFF (Express Proxy)
        ↓
External Food APIs (Swiggy)
```

---

## 🛠️ Tech Stack

### Frontend

- ⚛️ React.js
- 📦 Redux
- 🎨 ShadCN UI
- 🌈 Tailwind CSS

### Backend Integration

- 🌐 Custom API Gateway (BFF Layer)
- 🔁 Reverse Proxy Middleware

### Authentication

- 🔑 Firebase Authentication

### Payments

- 💸 Razorpay (Frontend Integration)

---

## 🚀 Live Demo

👉 [https://spicy-pricey.vercel.app](https://spicy-pricey.vercel.app)

---

## 📋 Getting Started

### 🔧 Prerequisites

- Node.js & npm / Bun
- Firebase project (Google Auth enabled)
- Razorpay account

---

### ⚙️ Installation

```bash
git clone https://github.com/sharadindudas/foodflow.git
cd foodflow
bun install
```

---

### 📝 Environment Variables

Create a `.env` file:

```env
VITE_FIREBASE_API=your_key
VITE_FIREBASE_AUTHDOMAIN=your_domain
VITE_PROJECT_ID=your_project
VITE_STORAGE_BUCKET=your_bucket
VITE_MESS_SEND_ID=your_sender_id
VITE_APP_ID=your_app_id

VITE_RAZORPAY_KEY_ID=your_key
VITE_RAZORPAY_KEY_SECRET=your_secret

VITE_BASE_URL=your_api_gateway_url
```

---

### ▶️ Run App

```bash
bun run dev
```

Open → [http://localhost:5173](http://localhost:5173)

---

# 🌐 API Gateway (BFF Integration)

This application uses a custom **Backend-for-Frontend (BFF) API Gateway** to handle all external API communication.

👉 **Backend Repository:**
[https://github.com/sharadindudas/api-gateway-bff](https://github.com/sharadindudas/api-gateway-bff)

---

## 🧠 Why This Exists

Browsers enforce strict CORS policies, which block direct API calls:

```js
// ❌ Blocked by CORS
fetch("https://www.swiggy.com/dapi/restaurants/list/v5");
```

To solve this, FoodFlow routes all requests through a **BFF proxy layer**.

---

## 🔁 How It Works

```
React App (FoodFlow)
        ↓
API Gateway BFF (Express Server)
        ↓
Swiggy APIs
```

---

## ⚙️ What the BFF Does

- 🔁 Proxies API requests to external services
- 🌐 Handles CORS restrictions
- 🕵️ Modifies headers to mimic browser requests
- 🔀 Supports dynamic routing (no need to define endpoints manually)

---

## 🔌 Example API Flow

### ✅ Frontend Request

```js
fetch(`${import.meta.env.VITE_BASE_URL}/api/proxy/swiggy/dapi/restaurants/list/v5?lat=22.518&lng=88.3832`);
```

---

### 🔁 Behind the Scenes

```
Frontend calls:
http://localhost:3001/api/proxy/swiggy/...

BFF forwards to:
https://www.swiggy.com/...
```

---

## 📦 Running Backend Locally

```bash
git clone https://github.com/sharadindudas/api-gateway-bff.git
cd api-gateway-bff
npm install
npm run dev
```

Server runs at:

```
http://localhost:3001
```

---

## ⚙️ Frontend Configuration

Set in `.env`:

```env
VITE_BASE_URL=http://localhost:3001/
```

---

## 🚀 Production Setup

```env
VITE_BASE_URL=https://your-api-gateway.onrender.com/
```

---

## 💡 Why This Matters

This project demonstrates:

- ✅ Real-world **BFF architecture pattern**
- ✅ Scalable frontend-backend separation
- ✅ Secure API communication
- ✅ Industry-level system design

---

## 🤝 Contributing

```bash
git checkout -b feature-name
git commit -m "Add feature"
git push origin feature-name
```

---

## 📜 License

MIT License

---

## 🧑‍💻 Author

**Sharadindu Das**

- GitHub: [https://github.com/sharadindudas](https://github.com/sharadindudas)
- Email: [sharadindudas774@gmail.com](mailto:sharadindudas774@gmail.com)

---

## ⭐ Final Note

> FoodFlow is not just a frontend project — it showcases a **production-grade architecture** using a custom API Gateway (BFF), similar to how large-scale applications handle third-party integrations.
