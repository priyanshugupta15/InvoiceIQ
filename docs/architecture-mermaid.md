# InvoiceIQ System Architecture

```mermaid
flowchart LR
    subgraph User["👤 User"]
        Browser[Web Browser]
    end

    subgraph Vercel[" Vercel (Frontend Hosting)"]
        ReactApp[React SPA<br/>Vite + TailwindCSS]
        CDN[Vercel CDN]
    end

    subgraph Render["⚡ Render (Backend Hosting)"]
        ExpressAPI[Express.js API<br/>Node.js]
        JWTAuth[JWT Authentication<br/>bcryptjs]
        InvoiceController[Invoice Controller]
        AIController[AI Controller]
        AuthController[Auth Controller]
    end

    subgraph MongoDB["🍃 MongoDB Atlas"]
        UsersDB[(Users Collection)]
        InvoicesDB[(Invoices Collection)]
    end

    subgraph GoogleAI["🤖 Google Gemini AI"]
        GeminiAPI[Google Generative AI<br/>gemini-2.5-flash]
    end

    subgraph Email["📧 Email Service"]
        SMTP[SMTP / SendGrid<br/>Payment Reminders]
    end

    Browser -->|HTTPS| CDN
    CDN -->|Serve Static| ReactApp
    ReactApp -->|API Requests<br/>VITE_API_BASE_URL| ExpressAPI
    ExpressAPI -->|Authenticate| JWTAuth
    JWTAuth --> UsersDB
    ExpressAPI -->|CRUD Operations| InvoiceController
    InvoiceController --> StoreInvoice[Store Invoice]
    StoreInvoice --> InvoicesDB
    ExpressAPI -->|AI Parsing Request| AIController
    AIController -->|Generate/Parse| GeminiAPI
    GeminiAPI -->|Structured Data| AIController
    ExpressAPI -->|Send Reminder| SMTP
    AuthController -->|Register/Login| JWTAuth

    style Vercel fill:#e0e7ff,stroke:#4f46e5,stroke-width:2px
    style Render fill:#fef3c7,stroke:#d97706,stroke-width:2px
    style MongoDB fill:#d1fae5,stroke:#059669,stroke-width:2px
    style GoogleAI fill:#fce7f3,stroke:#db2777,stroke-width:2px
    style Email fill:#e0f2fe,stroke:#0284c7,stroke-width:2px
    style ReactApp fill:#ffffff,stroke:#4f46e5
    style ExpressAPI fill:#ffffff,stroke:#d97706
    style GeminiAPI fill:#ffffff,stroke:#db2777
    style UsersDB fill:#ffffff,stroke:#059669
    style InvoicesDB fill:#ffffff,stroke:#059669
```

## Architecture Components

### Frontend (Vercel)
- **React SPA** - Single Page Application built with Vite
- **TailwindCSS** - Utility-first CSS framework
- **Vercel CDN** - Global content delivery network

### Backend (Render)
- **Express.js API** - RESTful API server
- **JWT Authentication** - Secure token-based auth
- **Controllers** - Business logic handlers

### Database (MongoDB Atlas)
- **Users Collection** - User accounts and credentials
- **Invoices Collection** - Invoice documents

### External Services
- **Google Gemini AI** - AI-powered invoice parsing and generation
- **Email Service** - Payment reminder emails

## Data Flow

1. User accesses the application through Vercel CDN
2. React frontend serves static assets
3. API requests are sent to Render-hosted backend
4. Backend authenticates requests using JWT
5. Invoice data is stored/retrieved from MongoDB Atlas
6. AI requests are processed by Google Gemini API
7. Payment reminders are sent via email service
