# 📚 CoursWap

**CoursWap** est une plateforme collaborative de partage de cours et de formations qui met en relation des étudiants avec des professeurs pour faciliter l'apprentissage et l'échange de connaissances.

## 🎯 À propos du projet

CoursWap est une application web full-stack qui permet aux étudiants de trouver des professeurs pour des cours particuliers et aux enseignants de proposer leurs services. La plateforme offre des fonctionnalités de réservation de sessions, de partage de vidéos éducatives, et de gestion de calendrier intégré.

### ✨ Fonctionnalités principales

- 🔐 **Authentification sécurisée** :  Connexion locale et via Google OAuth 2.0
- 👥 **Gestion des profils** : Profils différenciés pour étudiants et professeurs
- 📅 **Système de réservation** : Prise de rendez-vous en one-to-one
- 🎥 **Partage de vidéos** : Upload et consultation de contenus éducatifs (AWS S3)
- 🗓️ **Intégration calendrier** : Synchronisation avec Google Calendar
- 🗺️ **Géolocalisation** : Recherche de professeurs à proximité (Google Maps)
- 💬 **Communication temps réel** : Chat et notifications via WebSocket (Socket.io)
- 📊 **Statistiques** : Tableaux de bord pour suivre l'activité
- 📖 **Documentation API** : Interface Swagger pour l'API REST

## 🏗️ Structure du projet

```
CoursWap/
├── backend/                # API REST Node.js/Express
│   ├── controllers/        # Logique métier des endpoints
│   │   ├── authControllers. js
│   │   ├── userController.js
│   │   ├── meetControllers.js
│   │   ├── calendarController.js
│   │   ├── VideoController.js
│   │   ├── OneToOneControllers.js
│   │   ├── statsControllers.js
│   │   ├── tokenController.js
│   │   └── wordCloudController.js
│   │
│   ├── models/             # Schémas MongoDB/Mongoose
│   │   ├── User.js
│   │   ├── Meet.js
│   │   ├── OneToOneEvent.js
│   │   ├── Video.js
│   │   ├── WordCloud.js
│   │   ├── App.js
│   │   └── addressCache.js
│   │
│   ├── routes/             # Définition des routes API
│   │   ├── authRoutes.js
│   │   ├── userRoutes.js
│   │   ├── meetRoutes.js
│   │   ├── professeurRoutes.js
│   │   ├── oneToOneEventRoutes.js
│   │   ├── calendarRoutes.js
│   │   ├── videoRoutes.js
│   │   ├── statsRoutes.js
│   │   ├── tokenRoutes.js
│   │   └── wordCloudRoutes.js
│   │
│   ├── services/           # Services externes et utilitaires
│   │   ├── googleAuthService.js
│   │   ├── localAuthService.js
│   │   └── tokenService.js
│   │
│   ├── middleware/         # Middlewares Express
│   ├── server.js           # Point d'entrée de l'application
│   └── package.json
│
└── frontend/               # Application React
    ├── public/             # Ressources statiques
    ├── src/
    │   ├── pages/          # Pages de l'application
    │   │   ├── LoginRegister. jsx
    │   │   ├── ProfilPage.jsx
    │   │   ├── ContactProfesseur.jsx
    │   │   ├── CreateMeetingPage.jsx
    │   │   └── UploadVideoPage.jsx
    │   │
    │   ├── component/      # Composants réutilisables
    │   │   ├── AuthProvider.jsx
    │   │   ├── EspaceEtu.jsx
    │   │   ├── EspaceProf.jsx
    │   │   ├── AddressForm.jsx
    │   │   ├── gMap.jsx
    │   │   ├── LiveButton.jsx
    │   │   └── VideoUploadButton.jsx
    │   │
    │   ├── style/          # Styles CSS
    │   ├── App.jsx         # Composant racine
    │   ├── Header.jsx      # En-tête de l'application
    │   ├── MainPage.jsx    # Page principale
    │   └── main.jsx        # Point d'entrée React
    │
    ├── package.json
    └── vite.config.mjs     # Configuration Vite
```

## 🛠️ Technologies utilisées

### Backend
- **Node.js** & **Express. js** - Framework serveur
- **MongoDB** & **Mongoose** - Base de données NoSQL
- **Passport.js** - Authentification (Local + Google OAuth 2.0)
- **Socket.io** - Communication temps réel
- **AWS SDK** & **Multer-S3** - Stockage de vidéos
- **Google APIs** - Intégration Calendar et Maps
- **Swagger** - Documentation API
- **Bcrypt** - Hachage de mots de passe
- **Moment.js** - Gestion des dates

### Frontend
- **React 19** - Bibliothèque UI
- **React Router DOM** - Navigation SPA
- **Vite** - Build tool et dev server
- **Tailwind CSS** - Framework CSS utility-first
- **Socket.io Client** - WebSocket client
- **Google Maps API** - Géolocalisation
- **React OAuth Google** - Authentification Google
- **React Toastify** - Notifications utilisateur
- **JWT Decode** - Décodage de tokens

## 🚀 Installation et démarrage

### Prérequis
- Node.js (v16+)
- MongoDB (local ou Atlas)
- Compte AWS S3 (pour le stockage de vidéos)
- Clés API Google (OAuth 2.0, Calendar, Maps)

### Configuration

1. **Cloner le dépôt**
```bash
git clone https://github.com/FredWantou/CoursWap.git
cd CoursWap
```

2. **Configuration Backend**
```bash
cd backend
npm install
```

Créer un fichier `.env` dans le dossier `backend/` :
```env
SERVER_PORT=4000
COOKIE_KEY=your_cookie_secret_key
MONGODB_URI=mongodb://localhost/cours-wap-bdd

# Google OAuth
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret

# AWS S3
AWS_ACCESS_KEY_ID=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret_key
AWS_REGION=your_aws_region
S3_BUCKET_NAME=your_bucket_name

# Google APIs
GOOGLE_CALENDAR_API_KEY=your_calendar_api_key
GOOGLE_MAPS_API_KEY=your_maps_api_key
```

Démarrer le serveur backend :
```bash
node server.js
```
Le serveur démarre sur `http://localhost:4000`

3. **Configuration Frontend**
```bash
cd ../frontend
npm install
```

Démarrer l'application React :
```bash
npm start
```
L'application démarre sur `http://localhost:3000`

## 📖 Documentation API

Une fois le backend démarré, la documentation Swagger est accessible à l'adresse : 
```
http://localhost:4000/api-docs
```

## 🔐 Authentification

L'application supporte deux modes d'authentification :
- **Authentification locale** avec email et mot de passe
- **Google OAuth 2.0** pour une connexion simplifiée

## 🎨 Interface utilisateur

- **Espace Étudiant** : Recherche de professeurs, réservation de cours, consultation de vidéos
- **Espace Professeur** : Gestion de disponibilités, upload de contenus, suivi des réservations

## 👥 Contributeurs

- **Fred Wantou** - [@FredWantou](https://github.com/FredWantou)
- **Kevin** - [@kejaulin](https://github.com/kejaulin)
- **Oprah Nkam** - [@Oprah]()

## 📄 Licence

Ce projet est sous licence MIT.

---

**🌟 N'hésitez pas à contribuer au projet en ouvrant des issues ou en proposant des pull requests ! **
