# DentPulse - Dental Practice Management System (MERN Stack)

A complete, modern, responsive, and secure Dental Practice Management System built using the **MERN Stack** (MongoDB, Express.js, React.js, Node.js) with Tailwind CSS, Recharts, and Lucide React.

---

## 🌟 Key Modules & Features

1. **Executive Dashboard**:
   - Live metrics: Total registered patients, today's appointments, active dentists, completed treatments, total revenue collected, outstanding receivables, and low-stock alerts.
   - Interactive charts powered by **Recharts**:
     - 6-Month monthly revenue and collection trends (Area chart)
     - Appointment distribution by status (Pie chart)
   - Today's appointment schedule table with live operatory tracking.
   - Live clinical and financial audit feed.

2. **Patient Management**:
   - Register new patients with auto-generated unique IDs (`PAT-1001`, `PAT-1002`, ...).
   - Maintain comprehensive **Systemic Medical History** (allergies, chronic conditions, diabetes, hypertension, heart diseases, bleeding disorders).
   - Maintain **Dental History** (previous treatments, brushing/flossing frequency, chief complaints).
   - Emergency contact information.
   - Deep-dive Patient Chart page with tabs for Medical History, Appointments, Treatments, Prescriptions, and Invoices.
   - Soft-delete / Archive pattern to preserve clinical records for compliance.

3. **Appointment Management & Conflict Prevention**:
   - Schedule, reschedule, track, and cancel appointments with cancellation reason auditing.
   - **Intelligent Scheduling Conflict Engine**: Prevents double-booking dentists, checks dentist working days, working hours, and time slot overlap before saving.
   - Real-time operatory time slot generation based on dentist configuration.

4. **Dentist & Staff Management**:
   - Manage dentist profiles, specialties, license numbers, qualifications, and consultation fees.
   - Configurable weekly working days, operating hours, and slot durations (e.g., 30 or 45 mins).
   - Operatory / room allocation.

5. **Treatment & Clinical Management**:
   - Record dental examinations, diagnoses, procedures, and clinical operative notes.
   - **Interactive Dental Tooth Chart**: Select involved teeth using standard FDI / ISO notation (11-18, 21-28, 31-38, 41-48).
   - Procedure categories: Preventive, Restorative, Endodontics, Periodontics, Prosthodontics, Oral Surgery, Orthodontics, Cosmetic.
   - Multi-phase treatment planning with progress tracking.

6. **Prescription Management**:
   - Issue clinical medication scripts linked to patient and doctor.
   - Dynamic medication items with drug name, dosage, frequency, duration, and instructions.
   - **Print-ready Dental Prescription Document** with official clinic header and doctor signature line.

7. **Billing, Invoicing & Receipts**:
   - Generate itemized invoices with dynamic procedure line items.
   - Automatic subtotal, discount %, tax %, and balance due calculations.
   - Record full or partial payments across multiple channels: Cash, Credit Card, Debit Card, Bank Transfer, Insurance.
   - **Printable Patient Receipt / Tax Invoice** view.

8. **Dental Inventory Management**:
   - Track clinical supplies, PPE, anesthetic cartridges, restoration composites, surgical burs, and impression materials.
   - **Automated Low-Stock Alerts**: Flags supplies when stock is less than or equal to minimum threshold.
   - Fast Restock workflow with batch/lot numbering and expiration tracking.
   - Supplier / vendor directory.

9. **Reports & Audit Intelligence**:
   - Dynamic timeframe reports: Daily, Weekly, Monthly, and Yearly.
   - Financial summaries, collection channel breakdown, appointment throughput, and new patient intake.
   - **HIPAA-Compliant Audit Trail**: Immutable logging of all clinical, patient, and financial modifications with user, action, and timestamp.

10. **Role-Based Access Control (RBAC)**:
    - **Administrator**: Full system access, staff & user management, inventory, reports, and settings.
    - **Receptionist**: Patient intake, demographic updates, and appointment scheduling.
    - **Dentist**: Patient charts, diagnoses, procedures, treatments, and prescriptions.
    - **Cashier**: Invoicing, payment collection, receipt generation, and receivables tracking.
    - Server-side token validation and role checks on all protected API routes.

---

## 🛠️ Technology Stack

### Frontend
- **React.js 18** (Vite bundler)
- **Tailwind CSS 3** (Custom healthcare palette)
- **React Router DOM v6** (Nested routes & ProtectedRoute authorization)
- **Axios** (With request and response interceptors for JWT tokens)
- **Recharts** (Area charts, Pie charts, Bar charts)
- **Lucide React** (Clean medical and healthcare iconography)

### Backend
- **Node.js & Express.js** (REST API architecture)
- **MongoDB & Mongoose ODM** (11 schemas with indexes, virtuals, and hooks)
- **JWT (JSON Web Tokens)** & **bcryptjs** (Password hashing)
- **Helmet**, **CORS**, **Morgan**, & **express-rate-limit** (API security & DDoS mitigation)
- **Node.js Native Test Runner** (`node --test`) for unit testing

---

## 🗄️ Database Models

1. `User` - System users, roles (`admin`, `receptionist`, `dentist`, `cashier`), hashed passwords.
2. `Dentist` - Practitioner credentials, specialties, working hours, and slot durations.
3. `Patient` - Patient demographics, unique `patientId`, medical & dental history.
4. `Appointment` - Scheduled encounters, timestamps, status, operatory assignment.
5. `Treatment` - Clinical diagnoses, procedure names, tooth numbers, costs, treatment plans.
6. `Prescription` - Medication scripts, dosages, frequencies, and directions.
7. `Invoice` - Line items, subtotals, taxes, discounts, totals, balances, and payment statuses.
8. `Payment` - Financial transaction receipts, payment methods, transaction references.
9. `InventoryItem` - Dental supplies, quantities, minimum thresholds, status, batch numbers.
10. `Supplier` - Dental supply vendor contact details and categories.
11. `AuditLog` - Compliance trail tracking action, module, user, record ID, and description.

---

## 🚀 Getting Started

### Prerequisites
- **Node.js** (v18.x or v20.x+ recommended; tested on v24)
- **npm** (v9+ or v11+)
- **MongoDB** running locally on default port `27017` (e.g. `mongodb://127.0.0.1:27017`) or a MongoDB Atlas URI.

---

### Step 1: Backend Setup & Seed Data

1. Navigate to the backend directory:
   ```bash
   cd backend
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Check `.env` configuration (pre-configured with defaults):
   ```env
   PORT=5000
   NODE_ENV=development
   MONGO_URI=mongodb://127.0.0.1:27017/dental_management_db
   JWT_SECRET=super_secret_dental_clinic_jwt_key_2026_secure
   JWT_EXPIRE=30d
   CLIENT_URL=http://localhost:5173
   ```
4. Seed the database with realistic development data:
   ```bash
   npm run seed
   ```
5. Run unit tests to verify business logic and billing calculations:
   ```bash
   npm test
   ```
6. Start the backend API server:
   ```bash
   npm start
   # Or for development with auto-reload:
   npm run dev
   ```
   *The backend will be live at `http://localhost:5000`.*

---

### Step 2: Frontend Setup

1. Open a new terminal and navigate to the frontend directory:
   ```bash
   cd frontend
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the Vite development server:
   ```bash
   npm run dev
   ```
   *The frontend will be live at `http://localhost:5173`.*

---

## 🔐 Default Demo Login Credentials

You can test any role instantly using the fast one-click demo buttons on the login screen or by entering these credentials:

| Role | Email | Password | Allowed Capabilities |
| :--- | :--- | :--- | :--- |
| **Administrator** | `admin@dentalpulse.com` | `Admin@1234` | Full system access, User management, Inventory, Reports |
| **Receptionist** | `receptionist@dentalpulse.com` | `Recep@1234` | Patient intake, Directory, Conflict-free Appointment booking |
| **Dentist** | `dr.sarah@dentalpulse.com` | `Dentist@1234` | Clinical treatments, Tooth mapping, Prescriptions |
| **Cashier** | `cashier@dentalpulse.com` | `Cashier@1234` | Invoicing, Payment collection, Printable Receipts, Reports |

---

## 📡 REST API Reference

### Authentication (`/api/auth`)
- `POST /api/auth/login` - User sign-in (rate-limited)
- `GET /api/auth/me` - Current authenticated user
- `PUT /api/auth/updatepassword` - Change password
- `POST /api/auth/logout` - Logout & audit record

### Dashboard (`/api/dashboard`)
- `GET /api/dashboard/stats` - Overall metric cards and today's schedule
- `GET /api/dashboard/charts` - 6-month revenue trends and status distributions

### Patients (`/api/patients`)
- `GET /api/patients` - Search and list patients (paginated)
- `GET /api/patients/:id` - Full patient profile with treatment and invoice history
- `POST /api/patients` - Register a new patient
- `PUT /api/patients/:id` - Update medical/dental chart
- `DELETE /api/patients/:id` - Archive patient record

### Appointments (`/api/appointments`)
- `GET /api/appointments` - Filter by date, dentist, patient, and status
- `POST /api/appointments` - Book appointment with conflict detection
- `PUT /api/appointments/:id` - Update/reschedule appointment
- `PUT /api/appointments/:id/cancel` - Cancel appointment with reason

### Dentists (`/api/dentists`)
- `GET /api/dentists` - Directory of dentists
- `GET /api/dentists/:id` - Single dentist profile
- `GET /api/dentists/:id/slots?date=YYYY-MM-DD` - Available operatory time slots
- `POST /api/dentists` - Add dentist profile (Admin)
- `PUT /api/dentists/:id` - Update dentist schedule and fees

### Treatments (`/api/treatments`)
- `GET /api/treatments` - List procedures and treatments
- `POST /api/treatments` - Record diagnosis, procedure, and tooth numbers
- `PUT /api/treatments/:id` - Update treatment status / completion
- `DELETE /api/treatments/:id` - Archive treatment record

### Prescriptions (`/api/prescriptions`)
- `GET /api/prescriptions` - List prescriptions
- `POST /api/prescriptions` - Issue new prescription with medication line items
- `GET /api/prescriptions/:id` - Fetch prescription document

### Billing & Payments (`/api/billing`)
- `GET /api/billing/invoices` - List invoices and balances
- `GET /api/billing/invoices/:id` - Invoice detail with payment breakdown
- `POST /api/billing/invoices` - Generate new invoice with tax/discount
- `POST /api/billing/payments` - Record payment against invoice
- `GET /api/billing/payments` - Payment receipts ledger

### Inventory (`/api/inventory`)
- `GET /api/inventory/items` - Inventory items and low-stock count
- `POST /api/inventory/items` - Add supply item
- `PUT /api/inventory/items/:id` - Update item details
- `POST /api/inventory/items/:id/restock` - Restock quantity and batch
- `GET /api/inventory/suppliers` - List approved suppliers
- `POST /api/inventory/suppliers` - Create new supplier

### Reports & Compliance (`/api/reports`)
- `GET /api/reports/summary?timeframe=monthly` - Aggregate reporting
- `GET /api/reports/audit-logs` - System audit logs (Admin)

---

## 🛡️ Security Implementation
- **JWT Authentication**: Secure Bearer tokens with 30-day expiry.
- **Server-Side RBAC**: Authorization middleware enforced on every sensitive endpoint.
- **Password Protection**: bcryptjs salt hashing with pre-save hooks.
- **Rate Limiting**: `express-rate-limit` protect endpoints against brute force attempts.
- **Data Protection**: Archiving strategy ensures historical clinical notes and financial ledgers are preserved.
