# 🎵 Vinyl Record Collection

**Vinyl Record Collection** est une application mobile et web conçue pour aider les collectionneurs à gérer leur discothèque de vinyles et leur liste de souhaits. Développée avec **Vue.js** pour le frontend et **Firebase** pour le backend, cette application offre une expérience intuitive et sécurisée pour organiser, rechercher et suivre vos vinyles préférés.

---

## 📌 **Fonctionnalités**

### ✅ **Gestion de la Discothèque**

- **Ajout de vinyles** : Saisie manuelle des informations (artiste, album, année, label, genre, état, valeur estimée, notes personnelles, photo de la pochette).
- **Liste des vinyles** : Affichage sous forme de liste ou de grille avec vignettes des pochettes.
- **Recherche avancée** : Filtres par artiste, album, genre, année ou état.
- **Fiche détaillée** : Visualisation et modification des informations d'un vinyle.
- **Tri personnalisable** : Par artiste, année, genre ou état.

### ✅ **Liste de Souhaits**

- **Ajout de vinyles souhaités** : Avec priorité (Faible, Moyenne, Élevée).
- **Liste dédiée** : Affichage et gestion des vinyles souhaités.
- **Recherche et filtres** : Identiques à ceux de la discothèque.

### ✅ **Compte Utilisateur**

- **Inscription/Connexion** : Création de compte via email et mot de passe.
- **Profil utilisateur** : Nom d'utilisateur, photo de profil et réinitialisation du mot de passe.
- **Sauvegarde des données** : Stockage sécurisé dans Firebase.

### ✅ **Export/Import**

- **Export** : Export de la collection au format **CSV** ou **JSON**.
- **Import** : Import de données depuis un fichier **CSV** ou **JSON**.

---

## 🛠 **Technologies Utilisées**

### Frontend

- **Framework** : [Vue.js 3](https://vuejs.org/) (Composition API)
- **UI Library** : [Quasar Framework](https://quasar.dev/) (pour une expérience mobile et desktop optimisée)
- **State Management** : [Pinia](https://pinia.vuejs.org/) (pour la gestion d'état)
- **Routing** : [Vue Router](https://router.vuejs.org/)
- **Styling** : CSS/SCSS avec [Tailwind CSS](https://tailwindcss.com/) (optionnel)

### Backend

- **Base de données** : [Firebase Realtime Database](https://firebase.google.com/docs/database) (pour le stockage des données)
- **Authentification** : [Firebase Authentication](https://firebase.google.com/docs/auth) (email/mot de passe)
- **Stockage** : [Firebase Storage](https://firebase.google.com/docs/storage) (pour les images des pochettes)

### Outils de Développement

- **Build Tool** : [Vite](https://vitejs.dev/)
- **Testing** : [Vitest](https://vitest.dev/) (pour les tests unitaires)
- **Linting** : [ESLint](https://eslint.org/) + [Prettier](https://prettier.io/)

---

## 🚀 **Installation et Exécution**

### Prérequis

- Node.js (version 16 ou supérieure)
- npm ou yarn
- Un projet Firebase configuré (voir [Configuration Firebase](#-configuration-firebase))

### Étapes d'installation

1. **Cloner le dépôt**
  ```bash
   git clone https://github.com/votre-utilisateur/vinyl-record-collection.git
   cd vinyl-record-collection
  ```
2. **Installer les dépendances**
  ```bash
   npm install
   # ou
   yarn install
  ```
3. **Configurer Firebase**
  - Créez un projet sur [Firebase Console](https://console.firebase.google.com/).
  - Activez **Authentication** (méthode email/mot de passe) et **Realtime Database**.
  - Copiez les clés de configuration de votre projet Firebase dans un fichier `.env` à la racine du projet :
    ```env
    VITE_FIREBASE_API_KEY=votre_api_key
    VITE_FIREBASE_AUTH_DOMAIN=votre_auth_domain
    VITE_FIREBASE_PROJECT_ID=votre_project_id
    VITE_FIREBASE_STORAGE_BUCKET=votre_storage_bucket
    VITE_FIREBASE_MESSAGING_SENDER_ID=votre_messaging_sender_id
    VITE_FIREBASE_APP_ID=votre_app_id
    VITE_FIREBASE_DATABASE_URL=votre_database_url
    ```
4. **Lancer l'application en mode développement**
  ```bash
   npm run dev
   # ou
   yarn dev
  ```
   L'application sera accessible à l'adresse `http://localhost:5173`.

---

## 📂 **Structure du Projet**

```
vinyl-record-collection/
├── public/                  # Fichiers statiques
├── src/
│   ├── assets/              # Images, polices, etc.
│   ├── components/          # Composants Vue réutilisables
│   ├── composables/         # Logique réutilisable (Composition API)
│   ├── layouts/             # Mises en page (ex: layout principal)
│   ├── pages/               # Pages de l'application
│   │   ├── HomePage.vue     # Page d'accueil
│   │   ├── CollectionPage.vue # Page de la discothèque
│   │   ├── WishlistPage.vue  # Page de la liste de souhaits
│   │   ├── LoginPage.vue    # Page de connexion
│   │   └── ProfilePage.vue  # Page du profil utilisateur
│   ├── router/              # Configuration du routeur
│   ├── stores/              # Stores Pinia
│   ├── utils/               # Fonctions utilitaires
│   ├── App.vue              # Composant racine
│   └── main.js              # Point d'entrée de l'application
├── .env                     # Variables d'environnement
├── vite.config.js           # Configuration de Vite
└── package.json             # Dépendances et scripts
```

---

## 🔧 **Configuration Firebase**

1. **Créer un projet Firebase**
  - Allez sur [Firebase Console](https://console.firebase.google.com/) et créez un nouveau projet.
2. **Activer les services nécessaires**
  - **Authentication** : Activez la méthode de connexion par **email/mot de passe**.
  - **Realtime Database** : Créez une base de données en mode **test** (pour le développement) ou **verrouillé** (pour la production). Configurez les règles de sécurité comme suit pour le développement :
    ```json
    {
      "rules": {
        ".read": "auth != null",
        ".write": "auth != null"
      }
    }
    ```
  - **Storage** : Activez Firebase Storage pour stocker les images des pochettes.
3. **Ajouter les clés de configuration**
  - Dans votre projet Firebase, allez dans **Paramètres du projet** > **Vos applications** > **Ajouter une application web**.
  - Copiez les clés de configuration et ajoutez-les dans votre fichier `.env` (voir [Installation](#-installation-et-exécution)).

---

## 📱 **Fonctionnalités Futures**

- **Scan de code-barres** : Ajout de vinyles via scan de code-barres ou QR code.
- **Reconnaissance visuelle** : Ajout de vinyles via une photo de la pochette.
- **Intégration avec Discogs** : Récupération automatique des métadonnées.
- **Synchronisation cloud** : Sauvegarde automatique sur Firebase.
- **Alertes de disponibilité** : Notifications si un vinyle souhaité est disponible en ligne.
- **Communauté** : Partage de collections et échanges entre utilisateurs.

---

## 🤝 **Contribution**

Les contributions sont les bienvenues ! Voici comment contribuer :

1. Forker le projet.
2. Créer une branche pour votre fonctionnalité (`git checkout -b feature/ma-fonctionnalité`).
3. Commiter vos modifications (`git commit -m "Ajout de ma fonctionnalité"`).
4. Pousser vers la branche (`git push origin feature/ma-fonctionnalité`).
5. Ouvrir une **Pull Request**.

---

## 📄 **Licence**

Ce projet est sous licence **MIT**. Consultez le fichier [LICENSE](LICENSE) pour plus de détails.

---

## 📬 **Contact**

Pour toute question ou suggestion, n'hésitez pas à ouvrir une **Issue** sur GitHub ou à me contacter via :

- **Email** : [apertoapp@gmail.com](mailto:apertoapp@gmail.com)
- **GitHub** : [@apertoapp](https://github.com/apertoapp)

---

**✨ Merci d'utiliser Vinyl Record Collection !** 🎵
