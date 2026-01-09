# Gestion du Personnel - Projet MERN

Système complet de gestion du personnel développé avec la stack MERN (MongoDB, Express, React, Node.js). Cette application permet de gérer les utilisateurs et les rôles avec authentification JWT et autorisations basées sur les rôles.

## 📋 Table des matières

- [Aperçu du projet](#aperçu-du-projet)
- [Technologies](#technologies)
- [Structure du projet](#structure-du-projet)
- [Installation](#installation)
- [Configuration](#configuration)
- [Démarrage](#démarrage)
- [API Endpoints](#api-endpoints)
- [Authentification](#authentification)
- [Rôles et Permissions](#rôles-et-permissions)
- [Fonctionnalités](#fonctionnalités)
- [Scripts disponibles](#scripts-disponibles)

## 🎯 Aperçu du projet

Ce projet est un système de gestion du personnel avec les fonctionnalités suivantes:
- Authentification des utilisateurs avec JWT
- Système de rôles et permissions
- Dashboard administrateur
- Gestion des uploads de fichiers
- Interface utilisateur responsif avec React et Bootstrap

## 🛠️ Technologies

### Backend
- **Node.js** v20.11.1
- **Express.js** 5.2.1 - Framework web
- **MongoDB** avec **Mongoose** 9.0.1 - Base de données
- **JWT** (jsonwebtoken) 9.0.3 - Authentification
- **Bcrypt** 6.0.0 - Hashage des mots de passe
- **Multer** 2.0.2 - Gestion des uploads
- **Express-Validator** 7.3.1 - Validation des données
- **CORS** - Gestion des requêtes cross-origin
- **Nodemon** 3.1.11 - Rechargement automatique en développement

### Frontend
- **React** 19.2.0
- **Vite** 7.2.4 - Build tool
- **React Router DOM** 7.10.1 - Routage
- **Redux Toolkit** 2.11.1 - Gestion d'état
- **Axios** 1.13.2 - Client HTTP
- **React Bootstrap** 2.10.10 - Composants UI
- **Bootstrap** 5.3.8 - Framework CSS
- **ESLint** 9.39.1 - Linting

## 📁 Structure du projet

```
projetMasar-srum/
├── backend/
│   ├── config/
│   │   ├── connectDB.js          # Configuration MongoDB
│   │   └── seed/
│   │       ├── seedAdmin.js      # Seed compte administrateur
│   │       └── seedRoles.js      # Seed des rôles
│   ├── controllers/
│   │   └── auth.controller.js    # Logique authentification
│   ├── middlewares/
│   │   ├── isAuth.js             # Vérification authentification
│   │   ├── hashRole.js           # Gestion des rôles
│   │   └── validations/
│   │       ├── authValidations.js
│   │       └── validator.js
│   ├── models/
│   │   ├── User.js               # Schéma utilisateur
│   │   └── Role.js               # Schéma rôle
│   ├── routes/
│   │   └── auth.route.js         # Routes authentification
│   ├── utils/
│   │   ├── multer.js             # Configuration Multer
│   │   └── removeUploadImg.js    # Suppression fichiers
│   ├── uploads/                  # Dossier uploads
│   ├── server.js                 # Point d'entrée
│   ├── package.json
│   └── .env                      # Variables d'environnement
├── frontend/
│   ├── src/
│   │   ├── api/
│   │   │   └── axios.js          # Configuration Axios
│   │   ├── assets/               # Images et ressources
│   │   ├── components/
│   │   │   ├── NavBare.jsx       # Barre de navigation
│   │   │   ├── Footer.jsx        # Pied de page
│   │   │   └── AdminSidebar.jsx  # Sidebar admin
│   │   ├── JS/
│   │   │   ├── features/
│   │   │   │   └── authSlice.js  # État authentification
│   │   │   └── store/
│   │   │       └── store.js      # Configuration Redux
│   │   ├── pages/
│   │   │   ├── auth/
│   │   │   │   ├── Login.jsx
│   │   │   │   └── Register.jsx
│   │   │   ├── dasboard/
│   │   │   │   └── AdminDashboard.jsx
│   │   │   └── Unauthorized.jsx
│   │   ├── App.jsx               # Composant racine
│   │   ├── main.jsx              # Point d'entrée
│   │   └── index.css
│   ├── vite.config.js
│   ├── eslint.config.js
│   ├── package.json
│   └── index.html
├── package.json
└── README.md
```

## 🚀 Installation

### Prérequis
- Node.js v20.11.1+
- npm v10.4.0+
- MongoDB en local ou MongoDB Atlas

### Étapes d'installation

1. **Cloner le repository**
```bash
git clone https://github.com/mokas2017/gomycode.git
cd projetMasar-srum
```

2. **Installer les dépendances du backend**
```bash
cd backend
npm install
```

3. **Installer les dépendances du frontend**
```bash
cd ../frontend
npm install
```

## ⚙️ Configuration

### Variables d'environnement Backend

Créez un fichier `.env` dans le dossier `backend/`:

```env
# MongoDB
MONGO_URI=mongodb://localhost:27017/gestion-personnel
# ou MongoDB Atlas
MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/gestion-personnel

# Serveur
PORT=4500
NODE_ENV=development

# JWT
JWT_SECRET=votre_secret_jwt_très_sécurisé
JWT_EXPIRE=7d

# Email (optionnel)
EMAIL_HOST=votre_email_host
EMAIL_USER=votre_email
EMAIL_PASS=votre_password
```

### Variables d'environnement Frontend

Créez un fichier `.env` dans le dossier `frontend/`:

```env
VITE_API_URL=http://localhost:4500
```

## ▶️ Démarrage

### Mode développement

**Démarrer le backend** (Terminal 1):
```bash
cd backend
npm run dev
```
Le serveur démarre sur `http://localhost:4500`

**Démarrer le frontend** (Terminal 2):
```bash
cd frontend
npm run dev
```
L'application démarre sur `http://localhost:5173`

### Mode production

**Backend**:
```bash
cd backend
npm start
```

**Frontend**:
```bash
cd frontend
npm run build
npm run preview
```

## 📡 API Endpoints

### Authentification

#### Register - Créer un nouvel utilisateur
```
POST /api/auth/register
Content-Type: application/json

{
  "username": "utilisateur",
  "email": "email@example.com",
  "password": "password123",
  "role": "user"
}
```

#### Login - Connexion
```
POST /api/auth/login
Content-Type: application/json

{
  "email": "email@example.com",
  "password": "password123"
}
```

#### Logout - Déconnexion
```
POST /api/auth/logout
```

#### Current User - Utilisateur courant
```
GET /api/auth/current
```

#### Update Profile - Mettre à jour le profil
```
PUT /api/auth/update
Content-Type: application/json

{
  "username": "nouveau_nom",
  "email": "newemail@example.com"
}
```

## 🔐 Authentification

L'authentification est gérée avec **JWT (JSON Web Tokens)**:

1. L'utilisateur se connecte avec ses identifiants
2. Un token JWT est généré et stocké dans les cookies
3. Le token est envoyé avec chaque requête protégée
4. Le middleware `isAuth` vérifie la validité du token
5. En cas d'expiration, l'utilisateur doit se reconnecter

### Middleware d'authentification

Utilisez le middleware `isAuth` pour protéger les routes:

```javascript
const { isAuth } = require('../middlewares/isAuth');

router.get('/protected-route', isAuth, (req, res) => {
  // Logique de la route
});
```

## 👥 Rôles et Permissions

### Rôles disponibles

1. **Admin** - Accès complet à toutes les fonctionnalités
2. **Manager** - Gestion des utilisateurs
3. **User** - Accès limité aux fonctionnalités basiques

### Système de permissions

Le middleware `hashRole` gère les permissions basées sur les rôles:

```javascript
const { hashRole } = require('../middlewares/hashRole');

router.delete('/users/:id', isAuth, hashRole(['admin']), deleteUser);
```

## ✨ Fonctionnalités

- ✅ Authentification JWT sécurisée
- ✅ Système de rôles et permissions
- ✅ Dashboard administrateur
- ✅ Gestion des utilisateurs
- ✅ Upload de fichiers avec Multer
- ✅ Validation des données avec express-validator
- ✅ Gestion d'état avec Redux Toolkit
- ✅ Interface responsif avec Bootstrap
- ✅ CORS configuré
- ✅ Seed de données initiales

## 📝 Scripts disponibles

### Backend

| Script | Description |
|--------|-------------|
| `npm run dev` | Démarrer le serveur en mode développement avec Nodemon |
| `npm start` | Démarrer le serveur en mode production |

### Frontend

| Script | Description |
|--------|-------------|
| `npm run dev` | Démarrer le serveur Vite en développement |
| `npm run build` | Créer la build pour la production |
| `npm run preview` | Prévisualiser la build production |
| `npm run lint` | Lancer ESLint pour vérifier le code |

## 🔗 Ressources utiles

- [Documentation Express.js](https://expressjs.com/)
- [Documentation MongoDB](https://docs.mongodb.com/)
- [Documentation React](https://react.dev/)
- [Documentation Redux Toolkit](https://redux-toolkit.js.org/)
- [Documentation Vite](https://vitejs.dev/)
- [Documentation JWT](https://jwt.io/)

## 👨‍💻 Auteur

- **Slouma Med Karim** - Développeur principal

## 📄 Licence

Ce projet est sous licence ISC. Voir le fichier `package.json` pour plus de détails.

## 🚨 Troubleshooting

### Erreur de connexion MongoDB
- Vérifier que MongoDB est lancé
- Vérifier la chaîne `MONGO_URI` dans `.env`
- S'assurer que les identifiants MongoDB sont corrects

### CORS Error
- Vérifier que `origin` dans la configuration CORS correspond à l'URL du frontend
- Par défaut: `http://localhost:5173`

### JWT Token invalide
- Vérifier la variable `JWT_SECRET` dans `.env`
- Vérifier que le token n'a pas expiré
- Nettoyer les cookies du navigateur et se reconnecter

### Port déjà en utilisation
```bash
# Trouver le process utilisant le port 4500
netstat -ano | findstr :4500

# Changer le PORT dans le .env
PORT=5000
```

---

**Dernière mise à jour**: Janvier 2026
