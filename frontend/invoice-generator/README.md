# InvoiceIQ Frontend

InvoiceIQ is an AI-powered invoice generation and management application built with React 18 and Vite.

## Features

- 🧾 AI-powered invoice creation with Google Gemini
- 📊 Interactive dashboard with revenue insights
- 📧 Automated payment reminder generation
- 🔐 Secure JWT authentication
- 📱 Responsive design with TailwindCSS

---

# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.
---

##  Frontend Tests

This project uses **Jest** and **React Testing Library** for unit testing.

### Run all tests

```bash
cd frontend/invoice-generator
npm test
