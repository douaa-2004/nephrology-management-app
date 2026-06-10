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

*Copyright 2025 — Bourezg Douaa — Universite Oran 1*
