# PharmaTech Showcase

Public showcase repository for the **PharmaTech** project.

## At A Glance

**PharmaTech** is a full-stack pharmaceutical equipment platform that combines product showcase, quotation workflow, online purchasing, service request handling, recruitment management, and admin analytics in one system.

- Project type: Team-based academic eProject / semester 3 showcase
- My role: Full-stack contributor focused on feature integration, customer-facing flows, admin modules, deployment support, and production/demo issue fixing
- Main stack: Angular, NestJS, MongoDB, Socket.IO, Stripe, OCR, AI integration
- Live demo: [http://103.153.72.209:4201/](http://103.153.72.209:4201/)
- Demo video: [YouTube walkthrough](https://www.youtube.com/watch?v=Zsyu2Iy9UbY)
- Recognition: [Featured by Aptech Vietnam](https://aptechvietnam.com.vn/san-pham-hoc-vien/do-an-pharmaceutical-giai-phap-chuyen-doi-so-cho-nganh-thiet-bi-duoc-pham/)

## Quick Links

- [Overview](#overview)
- [My Contributions](#my-contributions)
- [What Makes This Project Notable](#what-makes-this-project-notable)
- [Live Links](#live-links)
- [Highlights](#highlights)
- [Tech Stack](#tech-stack)
- [Deployment Workflow](#deployment-workflow)
- [Recognition](#recognition)
- [Screenshots](#screenshots)
- [System Flow](#system-flow)
- [Repository Structure](#repository-structure)
- [Private Source Code Note](#private-source-code-note)
- [Supporting Documents](#supporting-documents)

## Overview

PharmaTech was built to help a pharmaceutical equipment business present its machines, receive customer inquiries, manage purchase and service workflows, and support recruitment activities through a unified digital platform.

The system combines both a customer-facing website and an admin-facing back office:

- Customers can browse capsules, tablets, liquid-filling machines, and related industrial equipment.
- Users can submit quote requests, add products to cart or wishlist, place orders, upload payment proof, and track order progress.
- Job seekers can create accounts, update profile and resume data, save jobs, and apply for open roles.
- Admin users can manage products, categories, stock, orders, returns, recruitment, contact content, support channels, and analytics dashboards.

This public repository is designed for recruiters, interviewers, and reviewers who want to quickly understand the project without being given access to the private production source code.

## My Contributions

- Built and refined major customer-facing pages, including home, shop, product detail, service, career, contact, and account flows
- Worked on admin-side modules related to products, orders, stock, quote management, content management, and recruitment workflows
- Supported frontend/backend integration across product, order, quote, service, career, and chat modules
- Handled deployment-related setup, GitHub Actions CI/CD flow, server publishing, and post-deploy issue fixing
- Investigated and fixed production/demo issues related to assets, environment config, APIs, and online deployment behavior
- Organized recruiter-facing documentation and showcase materials for easier project presentation

## What Makes This Project Notable

- Product catalog focused on pharmaceutical manufacturing equipment instead of generic e-commerce products
- Combined commercial workflow: quote, order, deposit, Stripe payment, payment proof upload, admin approval, and return handling
- Recruitment workflow with candidate profile, resume upload, application tracking, and analytics dashboard
- Admin operations for products, stock, orders, content, contact, quote, support, and service pages
- AI chat and OCR-assisted admin capabilities integrated into the backend
- Real-time communication using WebSocket / Socket.IO
- CI/CD deployment pipeline using GitHub Actions, PM2, and Nginx on a cloud VPS

## Live Links

- Live Demo: [http://103.153.72.209:4201/](http://103.153.72.209:4201/)
- Project Demo Video: [https://www.youtube.com/watch?v=Zsyu2Iy9UbY](https://www.youtube.com/watch?v=Zsyu2Iy9UbY)
- Featured Project Article: [https://aptechvietnam.com.vn/san-pham-hoc-vien/do-an-pharmaceutical-giai-phap-chuyen-doi-so-cho-nganh-thiet-bi-duoc-pham/](https://aptechvietnam.com.vn/san-pham-hoc-vien/do-an-pharmaceutical-giai-phap-chuyen-doi-so-cho-nganh-thiet-bi-duoc-pham/)

## Highlights

- Customer storefront with dynamic product listing, product detail pages, category browsing, wishlist, and cart
- Quote request system with admin review and reply workflow
- Service and purchase request pages for consulting, support, upgrade, maintenance, and B2B process presentation
- Checkout, deposit handling, Stripe payment, payment proof upload, and order approval flow
- Order history, order details, return request, and approval tracking
- Product stock management, QR support, and Excel export workflows on the admin side
- Recruitment dashboard with charts for applications, age range, gender distribution, and top skills
- Admin content management for About, Contact, Homepage, Hotline, Banner, and service/purchase pages
- OCR endpoint and AI chat endpoint integrated into the backend

## Tech Stack

- Frontend: Angular, TypeScript, PrimeNG, Chart.js, Highcharts, Socket.IO client, ngx-quill
- Backend: NestJS, TypeScript, MongoDB, Mongoose, JWT, Passport, Socket.IO, Stripe, Nodemailer
- AI / OCR: OpenAI integration, OCR processing workflow
- Tooling: npm, Git, GitHub, GitHub Actions
- Deployment: Nginx, PM2, VPS server
- Database: MongoDB Atlas / MongoDB Community during development

More detail: [docs/deployment/tech-stack.md](docs/deployment/tech-stack.md)

## Deployment Workflow

- The project uses GitHub Actions for deployment automation
- On push to the `main` branch, the workflow builds both frontend and backend artifacts
- The frontend Angular build is packaged and uploaded to the server for Nginx publishing
- The backend NestJS source is packaged, deployed to the VPS, installed, rebuilt, and restarted with PM2
- The deployment flow keeps the live demo updated without exposing the full private source repository

## Recognition

- PharmaTech was featured by Aptech Vietnam as a representative student pharmaceutical digital transformation project
- Public article: [Dự án Pharmaceutical - giải pháp chuyển đổi số cho ngành thiết bị dược phẩm](https://aptechvietnam.com.vn/san-pham-hoc-vien/do-an-pharmaceutical-giai-phap-chuyen-doi-so-cho-nganh-thiet-bi-duoc-pham/)

## Screenshots

### Home Hero

![Home Hero](docs/screenshots/home-hero.png)

### About Page

![About Page](docs/screenshots/about-page.png)

### Product Detail

![Product Detail](docs/screenshots/product-detail.png)

### Service Page

![Service Page](docs/screenshots/service-page.png)

### Quote Management

![Quote Management](docs/screenshots/quote-management.png)

### Admin Order History

![Admin Order History](docs/screenshots/order-history-admin.png)

### Recruitment Analytics Dashboard

![Career Dashboard](docs/screenshots/career-dashboard.png)

## System Flow

The full interactive system flow is available in:

- [system-flow.html](system-flow.html)

GitHub can also render the Mermaid diagrams directly in this README.

### Authentication Flow

```mermaid
flowchart LR
    A([Visitor opens site]) --> B{"Has account?"}
    B -- No --> REG[Register page]
    B -- Yes --> LOGIN[Login page]

    REG --> REGFORM["Fill in name / email / password"]
    REGFORM --> RVAL{"Validate input"}
    RVAL -- Invalid --> REG
    RVAL -- Valid --> CREATEACC["Create account
bcrypt hash password
role = user"]
    CREATEACC --> USERDASH([User dashboard])

    LOGIN --> CRED["Submit credentials"]
    CRED --> LOCKCHECK{"Account locked?"}
    LOCKCHECK -- "Yes (5 min)" --> LOCKMSG["Show lock message
& remaining time"]
    LOCKCHECK -- No --> AUTHCHECK{"Verify password
bcrypt compare"}
    AUTHCHECK -- Fail --> FAILCOUNT["Increment failedAttempts"]
    FAILCOUNT --> LIMIT{"failedAttempts >= 5?"}
    LIMIT -- Yes --> LOCK["Lock account 5 min
lockedUntil = now + 5m"]
    LIMIT -- No --> LOGIN
    AUTHCHECK -- Success --> RESET["Reset failedAttempts = 0"]
    RESET --> ROLE{"Check role"}
    ROLE -- user --> USERDASH
    ROLE -- admin --> ADMINDASH([Admin dashboard])

    LOGIN --> FORGOT["Forgot password?"]
    FORGOT --> OTP["Send OTP to email"]
    OTP --> VERIFY["Verify OTP code"]
    VERIFY -- Invalid --> OTP
    VERIFY -- Valid --> NEWPW["Set new password"]
    NEWPW --> LOGIN
```

### Customer Shopping Flow

```mermaid
flowchart TD
    HOME([Home page]) --> BANNER["Hero banner
& featured categories"]
    HOME --> SHOP[Browse shop]
    HOME --> ABOUT[About us]
    HOME --> SERVICE[Services]
    HOME --> CAREER[Careers]
    HOME --> CONTACT[Contact]

    SHOP --> FILTER["Filter by category"]
    FILTER --> LIST["Product list"]
    LIST --> DETAIL["Product detail
specs / price / stock / gallery"]
    DETAIL --> WISH["Add to wishlist"]
    DETAIL --> CART["Add to cart"]
    DETAIL --> QUOTE["Request a quote
Submit inquiry form"]

    CART --> CARTVIEW["Cart page
review items & quantities"]
    CARTVIEW --> UPDATE["Update quantity
or remove item"]
    CARTVIEW --> CHECKOUT["Proceed to checkout
Enter contact info"]

    CHECKOUT --> DEPOSITCALC["Calculate deposit
% configured by admin"]
    DEPOSITCALC --> STRIPEUI["Stripe checkout
pay deposit amount"]
    STRIPEUI --> WEBHOOK{"Stripe webhook
response"}
    WEBHOOK -- "Success" --> ORDERCREATE["Create order
status = Deposit Paid"]
    WEBHOOK -- "Cancelled" --> CHECKOUTFAIL["Payment cancelled
Return to cart"]

    ORDERCREATE --> PROOFUP["Upload payment proof
for remaining balance"]
    PROOFUP --> APPROVAL{"Admin review
approval_status"}
    APPROVAL -- "Approved" --> PAIDFULL["status = Paid in Full"]
    APPROVAL -- "Rejected" --> REUPLOAD["Re-upload proof"]
    PAIDFULL --> COMPLETE["Admin marks Completed"]

    ORDERCREATE --> HISTORY["Order history
& status tracking"]
    HISTORY --> RETURNREQ["Submit return request"]
```

### Order Lifecycle

```mermaid
stateDiagram-v2
    [*] --> Pending : Order placed (Stripe deposit paid)

    Pending --> DepositApproved : Admin approves payment proof
    Pending --> DepositRejected : Admin rejects payment proof
    Pending --> Cancelled : Customer or admin cancels

    DepositRejected --> Pending : Customer re-uploads proof

    DepositApproved --> PaidInFull : Remaining payment completed & approved

    PaidInFull --> Completed : Admin marks as fulfilled
    Completed --> [*]

    Cancelled --> DepositLost : No refund issued
    Cancelled --> DepositRefunded : Admin issues refund
    DepositLost --> [*]
    DepositRefunded --> [*]

    DepositApproved --> ReturnRequested : Customer raises return issue
    PaidInFull --> ReturnRequested : Customer raises return issue
    Completed --> ReturnRequested : Customer raises return issue
    ReturnRequested --> ReturnResolved : Admin resolves
    ReturnResolved --> [*]
```

### Recruitment And Career Flow

```mermaid
flowchart TD
    SEEKER([Job seeker]) --> JOBLIST["Browse job openings
(title / department / area / type)"]
    JOBLIST --> SAVE["Save job to watchlist"]
    JOBLIST --> JOBDETAIL["Job detail
requirements / benefits / deadline"]
    JOBDETAIL --> APPLY["Submit application
(profile auto-fills from account)"]

    APPLY --> PROFILECHECK{"Profile
complete?"}
    PROFILECHECK -- No --> EDITPROFILE["Fill in education
experience / skills / CV"]
    EDITPROFILE --> APPLY
    PROFILECHECK -- Yes --> APPDB[("application
collection")]

    APPDB --> ADMVIEW["Admin reviews
application list"]
    ADMVIEW --> FILTER["Filter by career / status"]
    FILTER --> SETSTAT["Update application status
applied / reviewed / accepted / rejected"]
    SETSTAT --> EMAILNOTIF["Send email notification
to candidate via Nodemailer"]
    EMAILNOTIF --> CANDNOTIF([Candidate receives email])

    ADMVIEW --> ANALYTICS["Career analytics dashboard"]
    ANALYTICS --> CHARTS["Charts: applicant count
gender / age / top skills / funnel"]
```

### B2B Purchase Workflow

```mermaid
flowchart LR
    START([Customer interested
in equipment]) --> INTAKE["Step 1: Customer Intake
Submit project requirements"]
    INTAKE --> CONSULT["Step 2: Technical Consulting
Engineer assessment & proposal"]
    CONSULT --> URS["Step 3: URS Development
User Requirements Specification"]
    URS --> CONTRACT["Step 4: Contract Signing
Finalize terms & payment schedule"]
    CONTRACT --> DELIVERY["Equipment delivery
& installation"]
    DELIVERY --> END([Project complete])

    ADMIN([Admin]) --> MANAGE["Manage each step's
banner & content via CMS"]
    MANAGE --> INTAKE
    MANAGE --> CONSULT
    MANAGE --> URS
    MANAGE --> CONTRACT
```

### Admin Management Overview

```mermaid
flowchart TD
    DASH([Admin Dashboard]) --> ACCT["Account Management
view / lock / unlock users
create admin accounts"]
    DASH --> PROD["Product Management
CRUD / main image / gallery
soft delete / recycle bin"]
    DASH --> CAT["Category Management
CRUD / assign to products"]
    DASH --> STOCK["Stock Management
QR code scan / update qty
export Excel"]
    DASH --> ORDM["Order Management
approve / reject proofs
mark completed
view all orders"]
    DASH --> RETM["Return Management
review return requests
resolve & close"]
    DASH --> CARM["Career Management
post / edit job listings
set deadlines & requirements"]
    DASH --> APMM["Application Management
review CVs / update status
send email feedback"]
    DASH --> QUOTM["Quote Management
read inquiries
reply by email"]
    DASH --> SUPP["Support Chat
real-time chat with customers
AI assistant for auto-reply"]
    DASH --> CONT["Content Management
About / Contact / Banner
Hotline / Home categories"]
    DASH --> SRVM["Service Pages CMS
Consulting / Support / Upgrade
Maintenance content"]
    DASH --> SETT["System Settings
deposit % configuration"]

    PROD --> EXPXL["Export product list
to Excel (.xlsx)"]
    STOCK --> QR["Generate QR code per product
scan to update inventory"]
    ORDM --> OCR["OCR scan payment proof
auto-extract amount & date"]
    SUPP --> AI["OpenAI chatbot
context-aware responses"]
    APMM --> CARANALYTICS["Analytics dashboard
applicant funnel / skills / demographics"]
```

### Real-Time Communication And AI

```mermaid
flowchart LR
    USER([Customer]) --> CHATUI["Chat widget
(Angular component)"]
    CHATUI --> SIO_CLIENT["Socket.IO client
emit: send_message"]
    SIO_CLIENT --> GATEWAY["NestJS Order / Chat Gateway
@WebSocketGateway"]
    GATEWAY --> MSGDB[("ChatThreadMessage
collection
userId / fromRole / msg")]
    GATEWAY --> ADMINUI["Admin support dashboard
receives message in real-time"]
    ADMINUI --> ADMREPLY["Admin types reply
emit: admin_reply"]
    ADMREPLY --> GATEWAY
    GATEWAY --> SIO_CLIENT

    USER2([Customer]) --> AI_WIDGET["AI chat bubble"]
    AI_WIDGET --> APISVC["POST /api/ai/chat"]
    APISVC --> OPENAI["OpenAI API
GPT model
Context: PharmaTech products & services"]
    OPENAI --> AIRESP["AI response
returned to user"]

    ORDEREVT["Order status changes"] --> ORDGW["Order WebSocket Gateway
broadcast: order_updated"]
    ORDGW --> USERALERT["User sees live
status notification"]
```

### Payment Flow

```mermaid
flowchart TD
    CHECKOUT([Checkout]) --> DEPSET["Fetch deposit setting
GET /api/deposit-setting"]
    DEPSET --> CALC["depositAmount = totalAmount * depositPercent / 100"]
    CALC --> PI["POST /api/stripe/create-payment-intent
stripeSecretKey, amount, currency"]
    PI --> STRIPE_SDK["Stripe Checkout Session
(redirected to Stripe hosted page)"]
    STRIPE_SDK --> PAY{"Customer pays"}
    PAY -- Success --> WEBHK["Stripe webhook
POST /api/stripe/webhook
event: payment_intent.succeeded"]
    PAY -- Cancel --> CANCEL_URL["Redirect to /payment/cancel
Order remains Pending"]
    WEBHK --> ORDERUPD["Update order
status = Deposit Paid
payment_id = Stripe ID"]
    ORDERUPD --> EMAILCONF["Send order confirmation email
Nodemailer + Handlebars template"]
    EMAILCONF --> CUST([Customer inbox])

    ORDERUPD --> UPLOADPROOF["Customer uploads remaining
payment proof image
POST /api/order/upload-proof/:id"]
    UPLOADPROOF --> OCRAPI["Admin triggers OCR scan
POST /api/ocr/read
(Hugging Face / vision model)"]
    OCRAPI --> EXTRACTED["Extracted: amount, date, bank"]
    EXTRACTED --> ADMAPPROVE{"Admin decision"}
    ADMAPPROVE -- Approve --> PAID["status = Paid in Full
approval_status = Approved"]
    ADMAPPROVE -- Reject --> REJNOTIF["Notify customer
Re-upload required"]
```

### Database Relationships

```mermaid
erDiagram
    Account {
        ObjectId _id PK
        string name
        string email
        string password
        string roles
        boolean is_active
        int failedAttempts
        date lockedUntil
        string resume
        array skills
        array experience
        array education
    }
    Product {
        ObjectId _id PK
        string name
        string model
        string description
        string photo
        array gallery
        number price
        number stock_quantity
        string stock_status
        array category_ids
        boolean is_delete
    }
    Category {
        ObjectId _id PK
        string name
        string description
        string photo
        boolean is_delete
    }
    Order {
        ObjectId _id PK
        ObjectId user_id FK
        object user_info
        number total_amount
        number deposit_percent
        number deposit_amount
        number remaining_payment_amount
        string status
        string approval_status
        string payment_proof_url
        string payment_id
    }
    OrderDetails {
        ObjectId _id PK
        ObjectId order_id FK
        ObjectId product_id FK
        number quantity
        number price
        number total_price
    }
    Cart {
        ObjectId _id PK
        ObjectId user_id FK
        ObjectId product_id FK
        number quantity
        number price
    }
    Wishlist {
        ObjectId _id PK
        ObjectId user_id FK
        ObjectId product_id FK
    }
    Career {
        ObjectId _id PK
        string title
        string department
        string location
        date expiration_date
        array skills
        array benefits
        boolean is_active
    }
    Application {
        ObjectId _id PK
        ObjectId career_id FK
        ObjectId user_id FK
        string status
    }
    SavedJob {
        ObjectId _id PK
        ObjectId user_id FK
        ObjectId career_id FK
    }
    Quote {
        ObjectId _id PK
        string firstName
        string email
        string message
        string status
        string replyMessage
    }
    ChatThreadMessage {
        ObjectId _id PK
        ObjectId userId FK
        string fromRole
        string msg
        date createdAt
    }
    DepositSetting {
        ObjectId _id PK
        number deposit_percent
    }
    Banner {
        ObjectId _id PK
        string title
        string imageUrl
        boolean is_active
    }

    Account ||--o{ Order : "places"
    Account ||--o{ Cart : "has"
    Account ||--o{ Wishlist : "saves"
    Account ||--o{ Application : "submits"
    Account ||--o{ SavedJob : "bookmarks"
    Account ||--o{ ChatThreadMessage : "sends"
    Order ||--o{ OrderDetails : "contains"
    Product ||--o{ OrderDetails : "referenced in"
    Product ||--o{ Cart : "added to"
    Product ||--o{ Wishlist : "saved in"
    Product }o--o{ Category : "belongs to (category_ids)"
    Career ||--o{ Application : "receives"
    Career ||--o{ SavedJob : "bookmarked via"
```

### CI/CD Deployment Flow

```mermaid
flowchart LR
    DEV([Developer]) --> |"git push main"| GH["GitHub
main branch"]
    GH --> |"trigger"| GHA["GitHub Actions
.github/workflows/deploy.yml"]

    GHA --> BUILD_BE["Build backend
npm run build (NestJS → dist/)"]
    GHA --> BUILD_FE["Build frontend
ng build (Angular → dist/)"]

    BUILD_BE --> ARCHIVE_BE["Create backend archive
pharmatech-source.tar.gz"]
    BUILD_FE --> ARCHIVE_FE["Create frontend archive
pharmatech-frontend.tar.gz"]

    ARCHIVE_BE --> RSYNC["rsync archives
to VPS via SSH"]
    ARCHIVE_FE --> RSYNC

    RSYNC --> SCRIPT["Run deploy_server.sh
on production VPS"]
    SCRIPT --> EXTRACT["Extract archives
to /var/www/pharmatech/"]
    EXTRACT --> INSTALL["npm install
(backend dependencies)"]
    INSTALL --> PM2["PM2 restart backend
process: pharmatech-api
port 3000"]
    EXTRACT --> NGINX["Copy Angular build
to Nginx web root
/var/www/html/"]
    NGINX --> RELOAD["nginx -s reload"]
    PM2 --> LIVE([Live site
VPS 103.153.72.209])
    RELOAD --> LIVE
```

## Repository Structure

- `system-flow.html`: full interactive system flow documentation
- `docs/screenshots`: UI screenshots used in this showcase
- `docs/features`: feature summaries for client, admin, recruitment, and service workflows
- `docs/api`: public-facing route and API notes
- `docs/demo`: links for live demo and video demo
- `docs/deployment`: stack and deployment notes
- `docs/diagrams`: ERD image and diagram notes
- `portfolio`: project summary, responsibilities, and technical reflections

## Private Source Code Note

The original PharmaTech source repository is intentionally kept **private** to avoid exposing the complete production codebase, internal configuration, and deployment-sensitive implementation details.

This showcase repository exists to provide:

- project overview
- feature documentation
- screenshots and diagrams
- live demo references
- recruiter-friendly explanation of scope and responsibilities

If needed during an interview, I can walk through selected implementation details live.

## Supporting Documents

- Feature overview: [docs/features/client-features.md](docs/features/client-features.md)
- Admin capabilities: [docs/features/admin-features.md](docs/features/admin-features.md)
- Recruitment capabilities: [docs/features/recruitment-features.md](docs/features/recruitment-features.md)
- Service and purchase flows: [docs/features/service-and-purchase.md](docs/features/service-and-purchase.md)
- Live demo notes: [docs/demo/demo-link.md](docs/demo/demo-link.md)
- Demo video: [docs/demo/video-link.md](docs/demo/video-link.md)
- API sample endpoints: [docs/api/sample-endpoints.md](docs/api/sample-endpoints.md)
- Deployment and stack notes: [docs/deployment/tech-stack.md](docs/deployment/tech-stack.md)
- Screenshots guide: [docs/screenshots/README.md](docs/screenshots/README.md)
- Diagram notes: [docs/diagrams/README.md](docs/diagrams/README.md)
- Project summary: [portfolio/project-summary.md](portfolio/project-summary.md)
- Responsibilities: [portfolio/responsibilities.md](portfolio/responsibilities.md)
- Challenges and solutions: [portfolio/challenges-and-solutions.md](portfolio/challenges-and-solutions.md)
