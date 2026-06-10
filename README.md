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

## Apercu des interfaces de l'application

### Page d'accueil

![Page principale](screenshots/home.jpg)

*Slogan medical, statistiques du cabinet et navigation.*

---

### Page de connexion

![Connexion](screenshots/login.jpg)

*Authentification securisee par role : medecin, assistant medical ou patient.*

---

### Interface Medecin — Creation de la fiche clinique

![Fiche clinique](screenshots/fiche_clinique.jpg)

*Saisie des antecedents medicaux, chirurgicaux, familiaux et motif de consultation lors de la premiere consultation.*

---

### Interface Medecin — Suivi du patient

![Suivi patient](screenshots/suivi_patient.jpg)

*Six modules accessibles : fiche clinique, bilans, conduite a tenir, prescription, examens radiologiques et biologiques.*

---

### Bilan biologique du patient

![Bilan patient](screenshots/bilan_patient.jpg)

*Valeurs biologiques avec alertes automatiques en rouge pour les parametres critiques (creatinine, uree, Na+, K+, Hb...).*

---

### Redaction de l'ordonnance medicale

![Ordonnance](screenshots/ordonnance.jpg)

*Redaction et apercu de l'ordonnance medicale personnalisee, generee et imprimable en PDF.*

---

### Demande d'examens radiologiques

![Examens radiologiques](screenshots/examen_radio.jpg)

*Selection des examens radiologiques et generation automatique du document PDF a remettre au patient.*

---

### Demande d'examens biologiques

![Examens biologiques](screenshots/examen_bio.jpg)

*Interface intuitive de selection des analyses biologiques avec generation du bon de demande en PDF.*

---

### Liste des rapports medicaux en attente

![Liste rapports](screenshots/rapport_liste.jpg)

*Vue d'ensemble des demandes de rapports medicaux soumises par les patients, en attente de validation.*

---

### Rapport medical genere avec bilan integre

![Rapport genere](screenshots/rapport_genere.jpg)

*Rapport medical complet genere automatiquement, accompagne du dernier bilan du patient, telechargeable en PDF.*

---

### Interface Assistant — Creation du dossier patient

![Dossier patient](screenshots/assistant_dossier.jpg)

*Enregistrement des informations administratives et generation automatique du compte patient (email + mot de passe).*

---

### Interface Assistant — Saisie du bilan

![Bilan assistant](screenshots/assistant_bilan.jpg)

*Formulaire de saisie des constantes biologiques avec detection des valeurs hors seuils critiques.*

---

### Interface Assistant — Ordre de passage

![Ordre de passage](screenshots/ordre_passage.jpg)

*Gestion de la salle d'attente : liste des patients, priorites configurables, statut de consultation.*

---

### Interface Patient — Espace personnel

![Espace patient](screenshots/patient_interface.jpg)

*Tableau de bord patient avec acces aux rapports medicaux et aux examens prescrits.*

---

### Interface Patient — Rapport medical apres validation

![Rapport patient](screenshots/patient_rapport.jpg)

*Le patient peut consulter et telecharger son rapport medical une fois valide par le medecin.*

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
