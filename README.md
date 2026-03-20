# 🧾 InvoiceIQ

**InvoiceIQ** is a production-ready, full-stack SaaS app for automating invoicing and basic finance workflows.

It turns plain text (emails, chats, notes) into structured invoices, sends AI-generated payment reminders, and shows revenue insights on a clean dashboard — all powered by **Google Gemini**.

> **Note:** This project uses Google Gemini AI for intelligent invoice parsing and payment reminder generation.

**Highlights**

-  Built with the **MERN stack** (MongoDB, Express, React, Node)
-  **AI features** using Google Gemini (`@google/generative-ai`)
-  **JWT authentication** + protected routes
-  **Responsive UI** with modern design
-  **Email reminders** for unpaid invoices




---

## 🖼️ Screenshots

###  Dashboard Overview
![Dashboard](./screenshots/dashboard1.png)

###  Create Invoice
![Create Invoice](./screenshots/createinvoiceai.png)

###  AI-Generated Invoice
![AI Invoice](./screenshots/aigeneratedinvoice.png)

###  AI Payment Reminder Email
![Payment Reminder](./screenshots/reminder.png)

###  Profile Settings
![Profile Settings](./screenshots/profile.png)

---

## 🧠 Overview
InvoiceIQ is aimed at freelancers and small businesses who need simple but smart invoicing.

The app can:

Parse unstructured text into a structured invoice

Generate payment reminder emails with AI

Track paid / unpaid invoices and basic revenue stats

Manage user profile and business details

From a dev perspective, this project demonstrates:

Building a real SaaS-style app with authentication & dashboards

Integrating a modern AI API into an existing backend



---

## 🛠️ Tech Stack

| Layer                  | Technology                                      |
| ---------------------- | ----------------------------------------------- |
| **Frontend**           | React 18 (Vite) + TailwindCSS + Axios           |
| **Backend**            | Node.js + Express.js                            |
| **Database**           | MongoDB Atlas (with Mongoose ODM)               |
| **AI Engine**          | Google Gemini API (@google/genai)               |
| **Authentication**     | JWT + bcryptjs                                  |
| **Testing**            | Jest + Supertest                                |
| **Environment Config** | dotenv                                          |
| **Hosting**            | Vercel (Frontend) + Render (Backend)            |

---

## ✨ Features

### 🔐 Authentication

* Secure signup/login using JWT
* Password hashing with bcrypt

### 🧾 Invoice Management

* Create, edit, delete, and filter invoices
* Auto-filled business details
* Export invoices as PDF

### 🧠 AI-Powered Tools

* **AI Invoice Generator:** Convert text → invoice instantly
* **AI Reminder Emails:** Generate payment reminders
* **AI Dashboard:** Summarize income, due payments, and insights

### 📱 Modern UI

* Responsive React + Tailwind design
* Dark mode ready

---

## 🏗️ Architecture Diagram

![Architecture Diagram](./docs/architecture.svg)

The architecture shows the complete data flow:

1. **User** → Accesses the application via web browser
2. **Vercel CDN** → Serves static React frontend globally
3. **Render Backend** → Express.js API handles all business logic
4. **MongoDB Atlas** → Stores user and invoice data
5. **Google Gemini AI** → Processes AI-powered invoice generation
6. **Email Service** → Sends payment reminder notifications

---

## 📂 Project Structure

```
InvoiceIQ/
│
├── backend/
│   ├── config/
│   │   └── db.js
│   ├── controllers/
│   │   ├── aiController.js
│   │   ├── authController.js
│   │   └── invoiceController.js
│   ├── middlewares/
│   │   └── authMiddleware.js
│   ├── models/
│   │   ├── Invoice.js
│   │   └── User.js
│   ├── routes/
│   │   ├── aiRoutes.js
│   │   ├── authRoutes.js
│   │   └── invoiceRoutes.js
│   ├── tests/
│   │   └── auth.test.js
│   ├── server.js
│   └── .env.example
│
├── frontend/
│   └── invoice-generator/
│       ├── src/
│       │   ├── assets/
│       │   ├── components/
│       │   ├── context/
│       │   ├── pages/
│       │   ├── utils/
│       │   ├── test/
│       │   │   └── fileMock.js
│       │   ├── App.jsx
│       │   ├── index.css
│       │   └── main.jsx
│       ├── public/
│       ├── screenshots/
│       ├── vite.config.js
│       └── jest.config.cjs
│
├── docs/
│   └── architecture.png
│
├── screenshots/
│   ├── dashboard.png
│   ├── create-invoice.png
│   ├── ai-generated.png
│   ├── reminder-email.png
│   └── profile-settings.png
│
├── docker-compose.yml
├── .github/workflows/        # GitHub Actions (optional)
├── .env.example              # root example env, if used
└── README.md

```

---

## ⚙️ Installation & Setup

### 🧩 Clone Repository

```bash
git clone https://github.com/priyanshugupta15/InvoiceIQ
cd InvoiceIQ
```

---

### 🖥️ Backend Setup

```bash
cd backend
npm install
```

Create a `.env` file inside the **backend** folder:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
GEMINI_API_KEY=your_gemini_api_key
GEMINI_MODEL=models/gemini-2.5-flash
PORT=8000
```

Run backend locally:

```bash
npm run dev
```

---

### 💻 Frontend Setup

```bash
cd ../frontend
npm install
npm run dev
```

Visit locally:
👉 [http://localhost:5173](http://localhost:5173)

---

## 🚀 Deployment

### 🌐 Live Demo

- **Frontend (Vercel):** [https://invoiceiq.vercel.app](https://invoiceiq.vercel.app)
- **Backend API (Render):** [https://invoiceiq-backend.onrender.com](https://invoiceiq-backend.onrender.com)

### 📦 Deploy Frontend to Vercel

1. Connect your GitHub repository to [Vercel](https://vercel.com)
2. Set the **Root Directory** to `InvoiceIQ/frontend/invoice-generator`
3. Build command: `npm run build`
4. Output directory: `dist`
5. Add environment variable:
   ```env
   VITE_API_BASE_URL=https://invoiceiq-backend.onrender.com
   ```

### 📦 Deploy Backend to Render

1. Create a new **Web Service** on [Render](https://render.com)
2. Connect your GitHub repository
3. Set **Root Directory** to `InvoiceIQ/backend`
4. Build command: `npm install`
5. Start command: `npm start`
6. Add environment variables:
   ```env
   NODE_ENV=production
   PORT=8000
   MONGODB_URI=your_mongodb_connection_string
   JWT_SECRET=your_strong_secret_key
   GEMINI_API_KEY=your_gemini_api_key
   CORS_ORIGIN=https://invoiceiq.vercel.app
   ```

### 🗄️ Database

The application uses **MongoDB Atlas** for cloud database hosting. Create a free cluster at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) and add the connection string to your backend environment variables.

---

## 🪪 License

This project is open-source under the **MIT License**.

---
