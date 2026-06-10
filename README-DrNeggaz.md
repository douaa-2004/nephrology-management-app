# Dr.Neggaz — Web Application for Managing a Nephrology Medical Practice

![React](https://img.shields.io/badge/Frontend-React%20%2F%20Redux-61dafb.svg?style=flat&logo=react)
![Express](https://img.shields.io/badge/Backend-Node.js%20%2F%20Express-339933.svg?style=flat&logo=node.js)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-336791.svg?style=flat&logo=postgresql)
![UML](https://img.shields.io/badge/Design-UML-blue.svg)

---

## Project Description

Dr.Neggaz is a specialized web application dedicated to the complete management of a nephrology medical practice. It centralizes patient data, automates the generation of medical documents (prescriptions, exam requests, reports) and facilitates coordination between the doctor, the medical assistant and the patient.

This project addresses a real need identified at a nephrology specialist's practice (Dr. NEGGAZ, Oran), who initially managed patient files manually on paper.

---

## Academic Context

| Field | Detail |
|---|---|
| Author | Bourezg Douaa |
| Institution | Oran 1 University — Faculty of Exact and Applied Sciences |
| Degree | Bachelor's Degree in Computer Science — Information Systems Track |
| Academic Year | 2024/2025 |

---

## Main Features

### Doctor Interface

- Creation and update of the patient's clinical record
- Patient follow-up: lab results, recommended actions, complete history
- Writing medical prescriptions with PDF export
- Requesting biological and radiological exams with PDF generation
- Reviewing and validating medical reports requested by patients
- Creating accounts for medical assistants

### Medical Assistant Interface

- Creating patient files with automatic generation of a patient account
- Entering lab results with automatic detection of critical values
- Managing patient queue order with a priority system

### Patient Interface

- Requesting a medical report online
- Viewing and downloading the report once validated by the doctor
- Access to the list of prescribed medical exams

---

## Tech Stack

### Frontend

| Technology | Usage |
|---|---|
| React.js | User interface, reusable components, virtual DOM |
| React Router | Navigation between application pages |
| Redux + redux-persist | Global state management, persistence after reload |
| jsPDF + html2canvas | Generating and exporting medical documents as PDF |

### Backend

| Technology | Usage |
|---|---|
| Node.js | Server-side JavaScript runtime |
| Express.js | REST API framework, route and middleware handling |
| pg (node-postgres) | Connection and queries to the PostgreSQL database |

### Database

| Technology | Usage |
|---|---|
| PostgreSQL | Relational DBMS, ACID transactions, referential integrity |
| SQL | Creating, inserting, updating and querying data |

---

## Database Architecture

The database is organized around the central table `dossier_patient`, identified by `numcart` (national ID card number). All related tables use this foreign key, ensuring data consistency and cascading deletion.

| Table | Description |
|---|---|
| `dossier_patient` | Patient's personal and administrative information (central table) |
| `bilan_patient` | Lab results: Hb, WBC, Platelets, Urea, Creatinine, Na+, K+, PTH... |
| `fiche_clinique` | Medical, surgical, family history, clinical examination |
| `conduite_patient` | Recommendations and medical decisions after consultation |
| `exam_links` | Links to PDF files of prescribed exams |
| `rapport_links` | Links to generated and validated medical reports |
| `utilisateur` | Doctor / assistant / patient accounts with roles and access rights |

---

## Project Structure

```
drneggaz-nephro/
├── frontend/
│   └── src/
│       ├── component/
│       │   ├── medecin/        # exambiolo, examradiolo, ficheclinique, ordonnance...
│       │   ├── assistant/      # dossier, bilan, queue order
│       │   └── patient/        # rapport, examens
│       └── redux/              # store.js, userSlice.js
├── backend/
│   ├── controllers/            # Business logic per resource
│   ├── routes/                 # Express REST API endpoints
│   ├── db.js                   # PostgreSQL connection configuration
│   └── server.js               # Server entry point
└── README.md
```

---

## Installation and Setup

### Backend

```bash
git clone https://github.com/your-username/drneggaz-nephro.git
cd drneggaz-nephro/backend
npm install
```

Create a `.env` file:

```
DB_HOST=localhost
DB_PORT=5432
DB_USER=your_user
DB_PASSWORD=your_password
DB_NAME=cabinet_nephro
```

```bash
node server.js
```

### Frontend

```bash
cd ../frontend
npm install
npm start
```

The application will be available at `http://localhost:3000`.

---

## Future Improvements

### Short term

- Secure deletion of patient files with confirmation window and selective options
- Comment and rating system for patients on the homepage

### Long term

- Patient queue display on TV screen with real-time updates
- Appointment management with calendar, confirmations and email/SMS reminders
- Dashboard with medical and practice activity statistics
- Mobile application for patients (reports, appointments, comments)

---

Copyright 2025 — Bourezg Douaa — Oran 1 University
