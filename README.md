# 🏥 Digital Hospital

## 🚀 Full-Stack Healthcare Management & AI Assistant Platform

**Digital Hospital** is a full-stack healthcare management application designed to bring patients, doctors, administrators, billing, pharmacy, and AI-assisted support together in one platform.

The project combines a **React frontend**, **Node.js + Express backend**, **MongoDB database**, and **Google Gemini AI** to support healthcare workflows such as appointments, patient records, medicines, billing, payments, and administrative analytics.

---

## **1. 📌 Project Overview**

Healthcare operations can become difficult to manage when appointments, patient information, prescriptions, billing, pharmacy inventory, and administrative data are handled separately.

**Digital Hospital** provides a centralized web-based solution for managing these activities through role-based access and REST APIs.

### **The platform focuses on:**

- 👤 Patient account and profile management
- 👨‍⚕️ Doctor and appointment management
- 🗂️ Patient records and clinical notes
- 💊 Medicine and pharmacy inventory management
- 🧾 Billing and payment tracking
- 📊 Administrative analytics
- 🤖 AI-powered healthcare and platform assistance
- 🔐 Authentication, authorization, and API security

---

## **2. 🎯 Project Objectives**

The application is designed to:

- ✅ Simplify appointment booking and management
- ✅ Centralize patient and clinical information
- ✅ Digitize prescriptions, bills, payments, and notes
- ✅ Track medicine inventory and stock availability
- ✅ Provide role-based access to application features
- ✅ Provide administrative dashboards and analytics
- ✅ Provide an AI assistant for platform guidance and general health information
- ✅ Maintain secure and consistent data handling

---

## **3. 🌟 Key Features**

### **👨‍⚕️ Admin & Clinical Management**

- Admin dashboard
- Doctor management
- Doctor availability and appointment handling
- Patient management
- Patient clinical records
- Clinical notes
- Diagnosis and treatment management
- Prescription management
- Room and patient-room assignment management
- Nurse and staff management
- Billing management
- Payment tracking
- Medicine and pharmacy inventory management
- Low-stock medicine handling
- Administrative analytics

### **🩺 Patient Portal**

- Patient registration and login
- JWT-based authentication
- Doctor browsing
- Appointment booking
- Appointment tracking
- Medicine browsing
- Prescription access
- Notes and personal health information
- Bills and payment information
- AI assistant access

### **🤖 AI Healthcare Assistant**

The application integrates the **Google Gemini API** through the backend.

#### **AI capabilities:**

- 💬 Conversational platform assistance
- 📅 Guidance for appointment-related workflows
- 🧾 Guidance for bills and payments
- 💊 Guidance related to medicine and platform features
- 🧭 Navigation and feature guidance
- 🩺 General health information

#### **⚠️ AI Safety Rules**

The AI assistant is configured not to:

- Diagnose diseases
- Prescribe medicines
- Make definitive medical claims

For medical or symptom-related questions, the assistant is configured to recommend consulting a qualified healthcare professional.

When the Gemini API key is unavailable, the backend can return a **demo-mode response** instead of calling the external AI service.

---

## **4. 🛡️ Security & Backend Protection**

The backend includes several security and reliability mechanisms:

- 🔐 JWT authentication
- 👥 Role-based access control
- 🔑 Password hashing with Bcrypt
- 🛡️ HTTP security headers with Helmet
- 🚦 API rate limiting
- 🔒 Authentication endpoint rate limiting
- ✅ Centralized error handling
- ✅ Request/validation error handling
- ✅ Invalid MongoDB ObjectId handling
- ✅ Duplicate-key error handling
- 🌱 Environment-variable based configuration

---

## **5. 💳 Payment & Inventory Transactions**

The backend includes MongoDB transaction handling for operations that need consistent updates across multiple documents.

### **Transaction Flow**

```text
Patient Checkout
      │
      ▼
Start Database Transaction
      │
      ▼
Verify Bill Status
      │
      ▼
Validate Payment Amount
      │
      ▼
Check Medicine Stock
      │
      ▼
Create Payment Record
      │
      ▼
Update Bill Status → Paid
      │
      ▼
Reduce Medicine Stock
      │
      ▼
Commit Transaction
```

When a validation step fails, the transaction can be aborted so that related database changes are rolled back together.

This approach is intended to reduce inconsistencies such as:

- Duplicate or incomplete payment updates
- Incorrect bill settlement states
- Incorrect medicine stock quantities
- Inconsistent concurrent checkout operations

---

## **6. 🏗️ System Architecture**

```text
┌─────────────────────────────────────────────────────────────┐
│                     FRONTEND / CLIENT                       │
│                                                             │
│        React + Tailwind CSS + Recharts + Axios              │
└────────────────────────────┬────────────────────────────────┘
                             │
                             │ HTTP / HTTPS
                             │ JWT Authorization
                             ▼
┌─────────────────────────────────────────────────────────────┐
│                       BACKEND / API                         │
│                                                             │
│      Node.js + Express REST API                             │
│      Helmet + Rate Limiting + JWT + Error Handling          │
└───────────────┬──────────────────────────┬─────────────────┘
                │                          │
                ▼                          ▼
┌──────────────────────────┐    ┌────────────────────────────┐
│      AI SERVICE          │    │       DATABASE SERVICE      │
│                          │    │                            │
│   Google Gemini API      │    │   MongoDB + Mongoose        │
│   Gemini 2.5 Flash       │    │   Database Transactions    │
└──────────────────────────┘    └────────────────────────────┘
```

---

## **7. 💻 Technology Stack**

### **Frontend**

- ⚛️ React
- 🎨 Tailwind CSS
- 📊 Recharts
- 🌐 Axios
- 🧭 React Router

### **Backend**

- 🟢 Node.js
- 🚂 Express
- 🍃 Mongoose
- 🔐 JSON Web Token (JWT)
- 🔑 Bcrypt
- 🛡️ Helmet
- 🚦 Express Rate Limit
- 📝 Morgan

### **Database & AI**

- 🍃 MongoDB
- 🤖 Google Gemini API

---

## **8. 📂 Project Structure**

```text
NHS hospital agent/
│
├── assets/
│   └── preview.PNG
│
├── backend/
│   ├── config/
│   │   └── db.js
│   │
│   ├── controllers/
│   │   ├── aiController.js
│   │   ├── appointmentController.js
│   │   ├── authController.js
│   │   ├── billController.js
│   │   ├── diagnosisController.js
│   │   ├── doctorController.js
│   │   ├── medicineController.js
│   │   ├── medicinePrescriptionController.js
│   │   ├── noteController.js
│   │   ├── nurseController.js
│   │   ├── patientController.js
│   │   ├── patientRoomAssignmentController.js
│   │   ├── paymentController.js
│   │   ├── recordController.js
│   │   ├── roomController.js
│   │   ├── staffController.js
│   │   └── treatController.js
│   │
│   ├── middleware/
│   │   ├── authMiddleware.js
│   │   ├── errorMiddleware.js
│   │   └── rateLimitMiddleware.js
│   │
│   ├── models/
│   ├── routes/
│   ├── scripts/
│   ├── config/
│   ├── server.js
│   ├── transactions.js
│   └── package.json
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── api/
│   │   ├── assets/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── routes/
│   │   ├── App.js
│   │   ├── App.css
│   │   └── index.js
│   ├── package.json
│   ├── tailwind.config.js
│   └── vercel.json
│
├── .gitignore
└── README.md
```

---

## **9. ⚙️ Environment Variables**

### **Backend**

Create a `.env` file inside the `backend` directory and configure the variables used by the application:

```env
PORT=
NODE_ENV=
MONGO_URI=
JWT_SECRET=
JWT_REFRESH_SECRET=
GEMINI_API_KEY=
FRONTEND_URL=
```

### **Frontend**

The frontend supports the following environment variable for the backend API URL:

```env
REACT_APP_API_URL=
```

When `REACT_APP_API_URL` is not supplied, the current frontend code uses its configured backend fallback URL.

---

## **10. 🚀 Installation & Setup**

### **Step 1: Clone the repository**

```bash
git clone <your-repository-url>
cd "NHS hospital agent"
```

### **Step 2: Install backend dependencies**

```bash
cd backend
npm install
```

### **Step 3: Configure backend environment variables**

Create the backend `.env` file and add the required MongoDB, JWT, Gemini, port, and frontend URL configuration.

### **Step 4: Start the backend**

For development:

```bash
npm run dev
```

Or start normally:

```bash
npm start
```

### **Step 5: Install frontend dependencies**

Open a new terminal:

```bash
cd frontend
npm install
```

### **Step 6: Start the frontend**

```bash
npm start
```

The React development server will start using the configuration defined in the frontend project.

---

## **11. 🔗 Backend Health Check**

The backend exposes a health endpoint:

```text
GET /health
```

A successful response reports the backend status and server timestamp.

The root endpoint also provides a simple backend availability response.

---

## **12. ⚠️ Medical Safety Disclaimer**

**Digital Hospital is an academic/software engineering project.**

The AI assistant provides general information and application guidance only. It is **not a replacement for professional medical advice, diagnosis, or treatment**.

For medical concerns, symptoms, or emergencies, users should consult an appropriately qualified healthcare professional.

---

## **13. 📄 License**

This project is intended for **educational and academic purposes**.

The current backend package specifies the **ISC** license, while the frontend package is marked as **private**.

---

## **14. ❤️ Project Summary**

**Digital Hospital** brings together healthcare management, patient services, administration, pharmacy workflows, billing, payments, and AI-assisted support in a single full-stack application.

### **Built with:**

**React • Node.js • Express • MongoDB • Mongoose • Tailwind CSS • Recharts • Axios • JWT • Bcrypt • Google Gemini AI**
