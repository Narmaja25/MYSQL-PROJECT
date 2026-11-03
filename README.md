# 🏥 Cardiology Hospital Management System (CHMS)

An enterprise-grade relational database ecosystem designed to streamline workflows, manage critical clinical operations, and automate tracking within a specialized cardiology department. 

This project models complex healthcare relationships—connecting patients, specialized cardiologists, clinical appointments, high-fidelity diagnostic testing, and multi-tier pharmaceutical prescriptions—into a highly optimized, clean database design.

---

## 💎 Repository Architecture & Core Highlights
* **Normalized Relational Architecture:** 7 fully normalized (`3NF`) tables built to eliminate data redundancy and ensure data integrity.
* **Idempotent Deployment Pipeline:** Zero-fail initialization script leveraging conditional schema resets and isolated integrity controls (`SET Foreign_key_Checks`).
* **Advanced Operational Inserts:** Data seed layering executed via robust configurations to prevent runtime exceptions and allow dynamic updates.
* **Production-Grade Analytics:** Designed to cover advanced multi-table dependencies, aggregate calculations, localized sorting operations, and grouped filters.

---

## 🛠️ Technology Stack & Ecosystem
* **Core RDBMS Engine:** MySQL v8.0+
* **Storage Engine Architecture:** `InnoDB` (Enforcing full `ACID` compliance and declarative cascade constraints)
* **Development Workspace:** VS Code Server Terminal & MySQL Workbench
* **Database Namespace:** `cardiology_db`

---

## 📐 Entity-Relationship Blueprint

The database ecosystem organizes critical healthcare entities into clear structural logical layers:

```text
       ┌───────────┐               ┌──────────────┐
       │  PATIENTS │<─────────────>│ APPOINTMENTS │
       └─────┬─────┘               └──────┬───────┘
             │                            │
             │<───────┐          ┌────────┘
             │        │          │
             ▼        ▼          ▼
   ┌───────────┐   ┌────────────────┐               ┌───────────┐
   │ MED_TESTS │   │  PRESCRIPTIONS │<─────────────>│  DOCTORS  │
   └───────────┘   └───────┬────────┘               └───────────┘
                           │
                           ▼
               ┌──────────────────────┐             ┌───────────┐
               │  PRESCRIPTION_ITEMS  │<───────────>│ MEDICINES │
               └──────────────────────┘             └───────────┘
```

### Table Metadata & Constraints Matrix

| Table Name | Operational Scope | Architectural Constraints |
| :--- | :--- | :--- |
| **`patients`** | Logs demographics & tracking info for incoming clinical cases. | `patient_id` (Primary Key, Auto-Increment) |
| **`doctors`** | Stores clinical profiles, cardiology sub-specialties, and experience tiers. | `doctor_id` (PK), `UNIQUE KEY(phone)` |
| **`appointments`** | Schedules consultations, tracks timetables, and visit statuses. | `appointment_id` (PK), `FK(patient_id)`, `FK(doctor_id)` |
| **`medical_tests`**| Tracks cardiac diagnostics (ECG, Echo, Lipids) along with specific results and costs. | `test_id` (PK), `FK(patient_id)` |
| **`prescriptions`**| Links clinical diagnostic decisions directly from doctor to patient. | `prescription_id` (PK), `FK(patient_id)`, `FK(doctor_id)` |
| **`medicines`** | Central repository for global pharmaceutical pricing and supply channels. | `medicine_id` (PK) |
| **`prescription_items`** | Intermediary operational matrix mapping active medication quantities and specific dosages. | `Composite PK(prescription_id, medicine_id)` |

---

## 📂 Repository Blueprint
```directory/
├── database/
│   └── cardiology_schema.sql  # Database system installation script
└── README.md                  # Comprehensive portfolio documentation
```

---

## ⚡ Quick Deployment Guide

To deploy this database cluster locally on your machine, launch your terminal engine and pipe the script directly into your active RDBMS instance:

1. Access your local MySQL Server terminal instance using your credentials.
2. Initialize the database container and execute the entire setup from the compiled schema file path.
3. Run the tracking checks to verify that all seven structural tables are rendering appropriately in the workspace layout.

---
*“Optimized data architectures drive precision engineering in modern digital healthcare systems.”*
