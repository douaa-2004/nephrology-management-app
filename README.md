# Dr.Neggaz — Application Web de Gestion d'un Cabinet Medical de Nephrologie

![React](https://img.shields.io/badge/Frontend-React%20%2F%20Redux-61dafb.svg?style=flat&logo=react)
![Express](https://img.shields.io/badge/Backend-Node.js%20%2F%20Express-339933.svg?style=flat&logo=node.js)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-336791.svg?style=flat&logo=postgresql)
![UML](https://img.shields.io/badge/Design-UML-blue.svg)

---

## Description du projet

**Dr.Neggaz** est une application web specialisee dediee a la gestion complete d'un cabinet medical de nephrologie. Elle centralise les donnees des patients, automatise la generation de documents medicaux (ordonnances, demandes d'examens, rapports) et facilite la coordination entre le medecin, l'assistant medical et le patient.

Ce projet repond a un besoin reel identifie chez un medecin specialiste en nephrologie (Dr. NEGGAZ, Oran) qui gerait initialement ses dossiers de maniere manuelle sur papier.

---

## Contexte Academique

| Champ | Detail |
|---|---|
| **Auteure** | Bourezg Douaa |
| **Encadrante** | Mme. TOUATI IMENE SOUMAYA |
| **Examinateur** | M. CHERIF HAMZA F. |
| **Etablissement** | Universite Oran 1 — Faculte des Sciences Exactes et Appliquees |
| **Diplome** | Licence Informatique — Option Systemes d'Information |
| **Promotion** | 2024/2025 — Session 1 — Code INFO_32/2025 |

---



## Fonctionnalites principales

### Interface Medecin

- Creation et mise a jour de la fiche clinique du patient
- Suivi du patient : bilans biologiques, conduite a tenir, historique complet
- Redaction d'ordonnances medicales avec export PDF
- Demande d'examens biologiques et radiologiques avec generation PDF
- Consultation et validation des rapports medicaux demandes par les patients
- Creation de comptes pour les assistants medicaux

### Interface Assistant Medical

- Creation du dossier patient avec generation automatique d'un compte patient
- Saisie des bilans biologiques avec detection automatique des valeurs critiques
- Gestion de l'ordre de passage des patients avec systeme de priorite

### Interface Patient

- Demande de rapport medical en ligne
- Consultation et telechargement du rapport une fois valide par le medecin
- Acces a la liste des examens medicaux prescrits

---

## Stack Technique

### Frontend

| Technologie | Utilisation |
|---|---|
| React.js | Interface utilisateur, composants reutilisables, DOM virtuel |
| React Router | Navigation entre les pages de l'application |
| Redux + redux-persist | Gestion de l'etat global, persistance apres rechargement |
| jsPDF + html2canvas | Generation et export de documents medicaux en PDF |

### Backend

| Technologie | Utilisation |
|---|---|
| Node.js | Environnement d'execution JavaScript cote serveur |
| Express.js | Framework API REST, gestion des routes et middlewares |
| pg (node-postgres) | Connexion et requetes vers la base de donnees PostgreSQL |

### Base de donnees

| Technologie | Utilisation |
|---|---|
| PostgreSQL | SGBDR relationnel, transactions ACID, integrite referentielle |
| SQL | Creation, insertion, mise a jour et interrogation des donnees |

---

## Architecture de la base de donnees

La base est organisee autour de la table centrale `dossier_patient`, identifiee par `numcart` (numero de carte d'identite nationale). Toutes les tables associees utilisent cette cle etrangere, garantissant la coherence des donnees et la suppression en cascade.

| Table | Description |
|---|---|
| `dossier_patient` | Informations personnelles et administratives du patient (table centrale) |
| `bilan_patient` | Resultats biologiques : Hb, GB, Plq, Uree, Creatinine, Na+, K+, PTH... |
| `fiche_clinique` | Antecedents medicaux, chirurgicaux, familiaux, examen clinique |
| `conduite_patient` | Recommandations et decisions medicales post-consultation |
| `exam_links` | Liens vers les fichiers PDF d'examens prescrits |
| `rapport_links` | Liens vers les rapports medicaux generes et valides |
| `utilisateur` | Comptes medecin / assistant / patient avec roles et droits d'acces |

---

## Structure du projet

```
drneggaz-nephro/
├── frontend/
│   └── src/
│       ├── component/
│       │   ├── medecin/        # exambiolo, examradiolo, ficheclinique, ordonnance...
│       │   ├── assistant/      # dossier, bilan, ordre de passage
│       │   └── patient/        # rapport, examens
│       └── redux/              # store.js, userSlice.js
├── backend/
│   ├── controllers/            # Logique metier par ressource
│   ├── routes/                 # Endpoints API REST Express
│   ├── db.js                   # Configuration connexion PostgreSQL
│   └── server.js               # Point d'entree du serveur
├── screenshots/                # Captures d'ecran de l'application
└── README.md
```

---

## Installation et lancement

### Backend

```bash
git clone https://github.com/ton-username/drneggaz-nephro.git
cd drneggaz-nephro/backend
npm install
```

Creer un fichier `.env` :

```
DB_HOST=localhost
DB_PORT=5432
DB_USER=ton_user
DB_PASSWORD=ton_password
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

L'application sera disponible sur `http://localhost:3000`

---

## Perspectives d'amelioration

### Court terme

- Suppression securisee du dossier patient avec fenetre de confirmation et choix selectif
- Systeme de commentaires et notation des patients sur la page d'accueil

### Long terme

- Tableau d'ordre de passage affiche sur ecran TV avec mise a jour en temps reel
- Gestion des rendez-vous avec calendrier, confirmations et rappels email/SMS
- Tableau de bord avec statistiques medicales et d'activite du cabinet
- Application mobile pour les patients (rapports, rendez-vous, commentaires)

---
<img width="303" height="265" alt="AUTO PATIENT" src="https://github.com/user-attachments/assets/4147b126-9057-420c-87f4-220ccfd25574" />
<img width="957" height="448" alt="Capture d’écran 2025-04-10 210119" src="https://github.com/user-attachments/assets/b047a86d-120e-45fe-bf00-ff08b45db8f3" />
<img width="947" height="431" alt="Capture d’écran 2025-05-24 033207" src="https://github.com/user-attachments/assets/21c0607d-37db-43d9-868d-9f421735421d" />
<img width="957" height="449" alt="Capture d’écran 2025-05-24 032420" src="https://github.com/user-attachments/assets/ffcbfc84-683e-40cc-b9e3-43cf4038a2b2" />
<img width="557" height="427" alt="Capture d’écran 2025-05-24 023530" src="https://github.com/user-attachments/assets/2ebf5db1-0df2-4d4b-b80b-e6bcf51390f1" />
<img width="951" height="431" alt="Capture d’écran 2025-05-24 023111" src="https://github.com/user-attachments/assets/e15828b1-6fe3-4bdd-b056-c6a620755403" />
<img width="959" height="439" alt="Capture d’écran 2025-05-24 010625" src="https://github.com/user-attachments/assets/b303aa76-3d42-42ba-910a-39c80733e368" />
<img width="233" height="289" alt="Capture d’écran 2025-05-23 182716" src="https://github.com/user-attachments/assets/fbe962b5-7509-40f7-8855-6f070ce2e136" />
<img width="238" height="440" alt="Capture d’écran 2025-05-23 182649" src="https://github.com/user-attachments/assets/82e1781b-bc42-4fc4-9252-c55cd2e34087" />
<img width="344" height="235" alt="Capture d’écran 2025-05-23 165119" src="https://github.com/user-attachments/assets/3a0ef45d-a59c-4498-bd32-eff495157af5" />
<img width="252" height="281" alt="Capture d’écran 2025-05-23 163947" src="https://github.com/user-attachments/assets/05f0afa0-c28b-490b-882c-5fe69f3b97e1" />
<img width="943" height="389" alt="Capture d’écran 2025-05-22 215205" src="https://github.com/user-attachments/assets/c4cfec7d-fc50-4187-923f-c513ca6fd23b" />
<img width="808" height="440" alt="Capture d’écran 2025-05-22 195640" src="https://github.com/user-attachments/assets/f491949e-ad9e-402d-953f-03c131df3fb6" />
<img width="272" height="259" alt="Capture d’écran 2025-05-22 212812" src="https://github.com/user-attachments/assets/4ed7848f-00b7-4a51-be99-65e64d4626f5" />
<img width="516" height="355" alt="Capture d’écran 2025-05-22 205044" src="https://github.com/user-attachments/assets/dab75baa-ed60-4743-955b-8fffba5f7b50" />
<img width="428" height="368" alt="Capture d’écran 2025-05-22 203341" src="https://github.com/user-attachments/assets/fe5a3af8-b026-4563-a2b3-8a7965e6cbc0" />
<img width="808" height="440" alt="Capture d’écran 2025-05-22 195640" src="https://github.com/user-attachments/assets/68c5af1f-0e1c-4d29-9c40-a67abc06822a" />

*Copyright 2025 — Bourezg Douaa — Universite Oran 1*
