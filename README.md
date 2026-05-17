# 🎵 Vinyl Record Collection

> Application mobile Flutter & Firebase pour gérer votre discothèque vinyle personnelle.

![Flutter](https://img.shields.io/badge/Flutter-3.x-02569B?style=flat&logo=flutter)
![Firebase](https://img.shields.io/badge/Firebase-Firestore%20%7C%20Auth-FFCA28?style=flat&logo=firebase)
![Dart](https://img.shields.io/badge/Dart-3.x-0175C2?style=flat&logo=dart)
![License](https://img.shields.io/badge/License-MIT-green?style=flat)
![Status](https://img.shields.io/badge/Status-Beta-orange?style=flat)

---

## 📖 Table des matières

- [Présentation](#-présentation)
- [Fonctionnalités](#-fonctionnalités)
- [Architecture](#-architecture)
- [Prérequis](#-prérequis)
- [Installation](#-installation)
- [Configuration Firebase](#-configuration-firebase)
- [Structure du projet](#-structure-du-projet)
- [API externes](#-api-externes)
- [Sécurité & RGPD](#-sécurité--rgpd)
- [Tests](#-tests)
- [Roadmap](#-roadmap)
- [Contribuer](#-contribuer)
- [Licence](#-licence)

---

## 🎯 Présentation

**Vinyl Record Collection** est une application mobile cross-platform (iOS & Android) développée avec **Flutter** et **Firebase**, destinée aux collectionneurs de vinyles. Elle centralise la gestion de la discothèque personnelle, la liste de souhaits et les interactions avec la communauté de collectionneurs.

L'application répond à trois besoins fondamentaux :
- **Inventorier** sa collection physique de manière rapide et précise (scan code-barres, reconnaissance visuelle)
- **Suivre** les vinyles souhaités avec alertes de disponibilité et historique des prix
- **Partager** et **échanger** au sein d'une communauté de passionnés

---

## ✨ Fonctionnalités

### 🗄️ Ma Collection (Discothèque)

| Fonctionnalité | Description |
|---|---|
| Ajout manuel | Saisie libre de toutes les métadonnées d'un vinyle |
| Scan code-barres / QR | Identification automatique via la caméra du téléphone |
| Reconnaissance visuelle | Ajout d'un vinyle par photo de pochette |
| Fiche détaillée | Artiste, album, année, label, genre, état, valeur estimée, notes, photo |
| Catégorisation | Par genre, artiste, année, état ou valeur |
| Recherche avancée | Filtres combinés multi-critères |
| Statistiques | Nombre de vinyles, valeur totale, répartition par genre/artiste |

### 💝 Liste de Souhaits

- Ajout de vinyles recherchés avec niveau de priorité (ex. : *"À acheter rapidement"*)
- **Alertes de disponibilité** : notification push si un vinyle souhaité apparaît sur Discogs ou eBay
- **Suivi des prix** : historique et évolution du prix pour chaque vinyle suivi

### 🤝 Fonctionnalités Sociales

- **Partage de collection** : export PDF ou lien public partageable
- **Messagerie intégrée** : échanges directs entre utilisateurs pour proposer des ventes ou trocs
- **Communauté** : forum ou groupes de discussion organisés par genre ou artiste

### ⚙️ Fonctionnalités Techniques Avancées

- **Mode hors ligne** : accès complet à la collection sans connexion internet (Firebase offline persistence)
- **Sauvegarde automatique** : synchronisation cloud via Firebase ou export local
- **Intégrations** : synchronisation avec Discogs (métadonnées), Spotify (extraits audio)

---

## 🏗️ Architecture

L'application suit une architecture **Clean Architecture** avec séparation claire des couches :

```
Presentation Layer  ──→  Flutter Widgets + BLoC / Riverpod
        ↓
Domain Layer        ──→  Use Cases, Entities, Repository Interfaces
        ↓
Data Layer          ──→  Firebase (Firestore, Auth, Storage), API clients (Discogs, Spotify)
```

### Stack technique

| Couche | Technologie |
|---|---|
| **Frontend mobile** | Flutter 3.x (Dart) |
| **Authentification** | Firebase Authentication (Email/Password, Google Sign-In, Apple Sign-In) |
| **Base de données** | Cloud Firestore (NoSQL, temps réel) |
| **Stockage fichiers** | Firebase Storage (photos de pochettes) |
| **Notifications push** | Firebase Cloud Messaging (FCM) |
| **Backend serverless** | Firebase Cloud Functions (Node.js) |
| **API Vinyles** | Discogs API (métadonnées, cotes) |
| **API Audio** | Spotify Web API (extraits 30 secondes) |
| **Scan** | `flutter_barcode_scanner` + ML Kit (Google) |

---

## 📋 Prérequis

Avant de cloner ce dépôt, assurez-vous d'avoir installé :

- [Flutter SDK](https://flutter.dev/docs/get-started/install) ≥ 3.0.0
- [Dart SDK](https://dart.dev/get-dart) ≥ 3.0.0 (inclus avec Flutter)
- [Android Studio](https://developer.android.com/studio) ou [Xcode](https://developer.apple.com/xcode/) (pour iOS)
- [Firebase CLI](https://firebase.google.com/docs/cli) ≥ 12.0.0
- Un compte [Firebase](https://console.firebase.google.com/) (plan Spark gratuit ou Blaze)
- Un compte développeur [Discogs](https://www.discogs.com/developers/) (clé API gratuite)
- Un compte développeur [Spotify](https://developer.spotify.com/) (Client ID + Secret)

```bash
# Vérifier les prérequis Flutter
flutter doctor
```

---

## 🚀 Installation

### 1. Cloner le dépôt

```bash
git clone https://github.com/votre-organisation/vinyl-record-collection.git
cd vinyl-record-collection
```

### 2. Installer les dépendances

```bash
flutter pub get
```

### 3. Configurer les variables d'environnement

Dupliquer le fichier d'exemple et renseigner vos clés :

```bash
cp .env.example .env
```

```dotenv
# .env
DISCOGS_API_KEY=votre_cle_discogs
DISCOGS_API_SECRET=votre_secret_discogs
SPOTIFY_CLIENT_ID=votre_client_id_spotify
SPOTIFY_CLIENT_SECRET=votre_client_secret_spotify
```

> ⚠️ **Important** : Ne commitez jamais le fichier `.env`. Il est déjà listé dans `.gitignore`.

### 4. Lancer l'application

```bash
# Android
flutter run --flavor development

# iOS
flutter run --flavor development --target lib/main_dev.dart
```

---

## 🔥 Configuration Firebase

### Créer le projet Firebase

```bash
# Se connecter à Firebase
firebase login

# Initialiser Firebase dans le projet
firebase init
```

Activez les services suivants dans la [Firebase Console](https://console.firebase.google.com/) :
- **Authentication** (Email/Password + Google + Apple)
- **Cloud Firestore** (mode production)
- **Firebase Storage**
- **Cloud Messaging** (FCM)
- **Cloud Functions**

### Ajouter les fichiers de configuration

**Android** — télécharger `google-services.json` et le placer dans :
```
android/app/google-services.json
```

**iOS** — télécharger `GoogleService-Info.plist` et le placer dans :
```
ios/Runner/GoogleService-Info.plist
```

### Règles Firestore

Les règles de sécurité Firestore sont définies dans `firestore.rules`. Déployer avec :

```bash
firebase deploy --only firestore:rules
```

Exemple de structure des règles :

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Un utilisateur ne peut accéder qu'à sa propre collection
    match /users/{userId}/records/{recordId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
    // Liste de souhaits privée
    match /users/{userId}/wishlist/{itemId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
    // Collections publiques (lecture seule si partagées)
    match /publicCollections/{docId} {
      allow read: if true;
      allow write: if request.auth != null;
    }
  }
}
```

---

## 📁 Structure du projet

```
vinyl-record-collection/
├── lib/
│   ├── main.dart                    # Point d'entrée
│   ├── main_dev.dart                # Entrée – env. développement
│   ├── core/
│   │   ├── constants/               # Constantes globales (couleurs, routes…)
│   │   ├── errors/                  # Gestion centralisée des erreurs
│   │   ├── network/                 # Client HTTP, intercepteurs
│   │   └── utils/                   # Helpers, extensions Dart
│   ├── features/
│   │   ├── auth/                    # Authentification (login, register, profil)
│   │   ├── collection/              # Ma Collection (CRUD vinyles)
│   │   ├── wishlist/                # Liste de souhaits + alertes prix
│   │   ├── scanner/                 # Scan code-barres & reconnaissance visuelle
│   │   ├── community/               # Forum, messagerie, échanges
│   │   └── settings/                # Paramètres, thème, compte, RGPD
│   └── shared/
│       ├── widgets/                 # Composants UI réutilisables
│       ├── models/                  # Modèles de données partagés
│       └── services/                # Services transverses (Firebase, Discogs, Spotify)
├── test/
│   ├── unit/                        # Tests unitaires
│   ├── widget/                      # Tests de widgets
│   └── integration/                 # Tests d'intégration
├── functions/                       # Firebase Cloud Functions (Node.js)
├── firestore.rules                  # Règles de sécurité Firestore
├── storage.rules                    # Règles Firebase Storage
├── firebase.json                    # Configuration Firebase CLI
├── pubspec.yaml                     # Dépendances Flutter
├── .env.example                     # Exemple de variables d'environnement
└── README.md
```

---

## 🔌 API externes

### Discogs API

Utilisée pour récupérer automatiquement les métadonnées des vinyles (artiste, label, année, genre, valeur marchande).

- Documentation : [https://www.discogs.com/developers/](https://www.discogs.com/developers/)
- Authentification : OAuth 1.0 ou jeton personnel
- Quota : 60 requêtes/minute (plan gratuit)

### Spotify Web API

Utilisée pour afficher des extraits audio de 30 secondes directement dans la fiche vinyle.

- Documentation : [https://developer.spotify.com/documentation/web-api/](https://developer.spotify.com/documentation/web-api/)
- Authentification : OAuth 2.0 (Client Credentials Flow)
- Scope minimal requis : `user-read-playback-state`

---

## 🔒 Sécurité & RGPD

### Authentification

- Connexion via **Email/Mot de passe**, **Google** ou **Apple**
- Sessions gérées par Firebase Authentication avec tokens JWT

### Chiffrement

- Les données sensibles (valeur estimée des collections) sont chiffrées côté client avant écriture dans Firestore
- Les communications sont chiffrées en transit via HTTPS/TLS (géré par Firebase)

### Conformité RGPD

| Droit | Implémentation |
|---|---|
| Droit d'accès | Export de toutes les données depuis *Paramètres > Mon compte > Exporter mes données* |
| Droit à l'oubli | Suppression complète du compte et de toutes les données associées depuis *Paramètres > Supprimer mon compte* |
| Consentement | Bandeau de consentement lors du premier lancement, opt-in explicite pour les notifications |
| Portabilité | Export JSON ou PDF de la collection |

---

## 🧪 Tests

```bash
# Tests unitaires
flutter test test/unit/

# Tests de widgets
flutter test test/widget/

# Tests d'intégration (émulateur requis)
flutter test integration_test/

# Couverture de code
flutter test --coverage
genhtml coverage/lcov.info -o coverage/html
```

---

## 🗓️ Roadmap

### v1.0 — MVP (en cours)
- [x] Authentification Firebase
- [x] CRUD de la collection (ajout, modification, suppression)
- [x] Scan code-barres
- [x] Intégration Discogs API
- [ ] Liste de souhaits
- [ ] Mode hors ligne

### v1.1 — Fonctionnalités sociales
- [ ] Messagerie entre utilisateurs
- [ ] Partage de collection (lien public / PDF)
- [ ] Forum communauté

### v1.2 — Intelligence & Intégrations
- [ ] Reconnaissance visuelle de pochette (ML Kit)
- [ ] Alertes de prix (Discogs + eBay)
- [ ] Extraits Spotify

### v2.0 — Marché intégré
- [ ] Marketplace interne (vente entre utilisateurs)
- [ ] Système de notation des vendeurs
- [ ] Paiement sécurisé

---

## 🤝 Contribuer

Les contributions sont les bienvenues ! Merci de suivre le processus ci-dessous.

### Processus de contribution

1. **Forker** le dépôt
2. **Créer** une branche feature : `git checkout -b feature/ma-nouvelle-fonctionnalite`
3. **Committer** vos changements : `git commit -m "feat: ajout de la reconnaissance visuelle"`
4. **Pousser** la branche : `git push origin feature/ma-nouvelle-fonctionnalite`
5. **Ouvrir** une Pull Request vers la branche `develop`

### Convention de commits (Conventional Commits)

```
feat:     Nouvelle fonctionnalité
fix:      Correction de bug
docs:     Mise à jour de la documentation
style:    Formatage (sans changement de logique)
refactor: Refactoring sans ajout de fonctionnalité
test:     Ajout ou modification de tests
chore:    Tâches de maintenance (dépendances, CI…)
```

### Standards de code

- Respecter les règles définies dans `analysis_options.yaml`
- Formater le code avec `dart format .` avant tout commit
- Ajouter des tests unitaires pour toute nouvelle logique métier
- Documenter les méthodes publiques avec des commentaires Dart Doc

---

## 📄 Licence

Ce projet est distribué sous licence **MIT**. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

## 📞 Contact & Support

- **Bugs & Suggestions** : [Ouvrir une issue](https://github.com/votre-organisation/vinyl-record-collection/issues)
- **Discussions** : [GitHub Discussions](https://github.com/votre-organisation/vinyl-record-collection/discussions)
- **Email** : support@vinyl-record-collection.app

---

<p align="center">
  Fait avec ❤️ par des passionnés de vinyles · Flutter + Firebase
</p>
