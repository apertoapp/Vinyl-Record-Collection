# 🎵 Vinyl Record Collection

**Vinyl Record Collection** est une application mobile développée avec **Flutter** et propulsée par un backend **Firebase**. Elle permet aux collectionneurs de vinyles de gérer simplement leur discothèque personnelle, leur liste de souhaits et les principales informations associées à chaque disque, tout en s'appuyant sur des services backend modernes comme l'authentification, la base de données cloud, le stockage de médias et les fonctions serveur de Firebase.

---

## Aperçu

L'application a été pensée pour offrir une expérience fluide aux passionnés de musique qui souhaitent centraliser leurs vinyles possédés et ceux qu'ils recherchent encore. Grâce à Flutter, le projet cible une base de code unique pour Android et iOS, tandis que Firebase fournit les briques backend nécessaires à l'authentification, à la synchronisation des données, au stockage des pochettes et à l'exécution de logique métier côté serveur.

---

## 📌 Fonctionnalités principales

### ✅ Gestion de la collection

L'application permet de créer et maintenir une collection personnelle de vinyles avec des fiches détaillées. Chaque entrée peut contenir des métadonnées comme l'artiste, le titre, l'année, le label, les genres, les notes personnelles, l'état du disque, l'état de la pochette, le prix d'achat et d'autres informations utiles à un collectionneur.

Fonctionnalités associées :
- Ajout manuel d'un vinyle.
- Modification d'une fiche existante.
- Suppression d'un vinyle de la collection.
- Consultation du détail d'une édition.
- Classement et organisation de la discothèque.

### ✅ Gestion de la wishlist

L'application propose une liste de souhaits distincte de la collection principale afin de suivre les disques recherchés. Cette séparation entre éléments possédés et éléments désirés facilite le suivi des achats à venir et la priorisation des recherches.

Fonctionnalités associées :
- Ajout d'un vinyle à la wishlist.
- Déplacement d'un vinyle de la wishlist vers la collection.
- Définition d'une priorité ou d'un prix cible.
- Suppression d'un élément de la liste de souhaits.

### ✅ Recherche et consultation

L'application permet de retrouver rapidement un disque au sein de la collection ou de la wishlist grâce à des mécanismes de recherche et de filtrage. Les métadonnées issues de catalogues spécialisés comme Discogs peuvent également servir à enrichir les fiches et à fiabiliser les informations affichées.

Fonctionnalités associées :
- Recherche par artiste, album, label ou année.
- Filtres sur les genres, formats ou statuts.
- Tri alphabétique, chronologique ou personnalisé.
- Consultation d'une fiche détaillée avec pochette et informations d'édition.

### ✅ Enrichissement des données via Discogs

Le projet peut s'appuyer sur l'API Discogs pour récupérer des informations de release, des identifiants et des images, ce qui simplifie l'ajout d'un disque et améliore la qualité des métadonnées. L'accès authentifié à Discogs est notamment utile pour récupérer certaines ressources comme les images de releases.

Fonctionnalités associées :
- Recherche d'un album depuis une source externe.
- Préremplissage des champs à partir des données disponibles.
- Sélection d'une édition précise.
- Rattachement d'un identifiant externe à la fiche locale.

---

## 🚀 Stack technique

| Couche | Technologie | Rôle |
|--------|-------------|------|
| Frontend mobile | Flutter | Développement cross-platform Android/iOS avec une base de code unique |
| Langage | Dart | Implémentation de l'interface, de la logique applicative et de l'intégration Flutter |
| Authentification | Firebase Authentication | Gestion sécurisée des comptes utilisateurs et des sessions |
| Base de données | Cloud Firestore | Stockage et synchronisation des données applicatives |
| Stockage médias | Firebase Cloud Storage | Hébergement des pochettes, images et médias associés |
| Backend serverless | Cloud Functions for Firebase | Exécution de logique métier et traitements backend sans serveur dédié |

---

## 🛠 Architecture fonctionnelle

L'application repose sur une architecture mobile connectée à Firebase pour séparer clairement l'interface utilisateur, la logique métier et la persistance des données. Flutter gère les écrans et les interactions côté client, tandis que Firebase centralise les services d'identité, de base de données, de stockage et d'automatisation backend.

### Composants backend Firebase

- **Firebase Authentication** : création de compte, connexion, gestion de session et sécurisation des accès aux données
- **Cloud Firestore** : stockage des collections, wishlists, profils utilisateurs et métadonnées applicatives avec synchronisation cloud.
- **Cloud Storage** : stockage des images de pochettes ou médias liés aux vinyles.
- **Cloud Functions** : traitements backend comme l'enrichissement de données, la validation, les notifications ou les tâches asynchrones déclenchées par des événements.

---

## 📌 Fonctionnalités côté utilisateur

### Compte utilisateur

Selon la configuration retenue dans le projet, un utilisateur peut créer un compte, se connecter et retrouver ses données sur plusieurs appareils. Firebase Authentication prend en charge plusieurs méthodes d'authentification et s'intègre naturellement aux règles de sécurité Firestore pour restreindre l'accès aux données selon l'identité connectée.

### Synchronisation cloud

Les données de collection et de wishlist peuvent être centralisées dans Firestore afin de permettre une persistance distante et une synchronisation entre appareils. Firestore est conçu pour la synchronisation de données dans des applications mobiles et s'intègre à des usages temps réel ou quasi temps réel selon l'architecture choisie.

### Gestion des médias

Les pochettes de vinyles et autres images associées peuvent être stockées dans Firebase Cloud Storage, ce qui évite d'alourdir directement la base documentaire. Ce service complète Firestore en prenant en charge les fichiers tout en restant compatible avec les règles de sécurité Firebase.

---

## 📂 Structure suggérée du dépôt

La structure exacte peut varier, mais un dépôt Flutter/Firebase est généralement organisé avec le code applicatif Flutter d'un côté et les fonctions backend Firebase de l'autre. Dans les projets GitHub intégrant une application mobile et Firebase, il est courant de séparer l'application principale et le dossier `functions/` pour la logique serverless.

```text
.
├── android/
├── ios/
├── lib/
│   ├── core/
│   ├── features/
│   ├── shared/
│   └── main.dart
├── test/
├── assets/
├── firebase.json
├── firestore.rules
├── storage.rules
├── functions/
└── pubspec.yaml
```

---

## Installation

### Prérequis

- Flutter installé sur la machine de développement.
- SDK Android et/ou environnement Xcode configuré selon la plateforme ciblée.
- Un projet Firebase configuré.
- La CLI FlutterFire ou la configuration Firebase nécessaire au projet.

### Étapes

```bash
git clone <url-du-depot>
cd <nom-du-depot>
flutter pub get
flutterfire configure
flutter run
```

L'initialisation Firebase dans un projet Flutter passe par les plugins FlutterFire et la configuration du projet Firebase avant l'exécution de l'application. La documentation FlutterFire décrit précisément ce rôle de passerelle entre Flutter et les services Firebase.

---

## Configuration Firebase

Le backend Firebase doit au minimum fournir :
- un projet Firebase actif ;
- Firebase Authentication si une connexion utilisateur est requise ;
- une base Cloud Firestore ;
- éventuellement Cloud Storage pour les images ;
- éventuellement Cloud Functions pour la logique serveur complémentaire.

Des règles de sécurité doivent être mises en place pour limiter l'accès aux documents Firestore et aux fichiers Storage selon l'utilisateur authentifié. Firebase Authentication s'intègre justement avec les règles de sécurité pour restreindre les opérations de lecture et d'écriture en fonction du statut d'authentification.

---

## Exemples de fonctionnalités métier

L'application peut inclure les écrans ou modules suivants :
- tableau de bord de la collection ;
- liste des vinyles possédés ;
- liste de souhaits ;
- détail d'un vinyle ;
- recherche locale et distante ;
- import ou enrichissement via Discogs ;
- profil utilisateur et paramètres ;
- statistiques simples sur la collection.

---

## Sécurité et qualité

Le choix de Firebase permet de s'appuyer sur des services managés pour l'authentification, le stockage et la logique backend, ce qui réduit la charge d'infrastructure tout en renforçant la scalabilité. Cloud Functions exécute du code backend en réponse à des événements Firebase ou à des requêtes HTTPS, sans nécessiter l'administration d'un serveur dédié..

Des outils complémentaires comme Crashlytics, Remote Config ou des parcours avancés autour de la suppression de données et de la sécurité peuvent également être intégrés dans un projet Flutter/Firebase plus mature. La documentation avancée Firebase pour Flutter met notamment en avant l'authentification, Firestore, Remote Config, Crashlytics et des scénarios de sécurité renforcée comme le MFA.

---

## Roadmap possible

Évolutions envisageables :
- scan de code-barres ;
- notifications push ;
- recommandations de disques ;
- partage de collection ;
- export CSV ou PDF ;
- mode hors ligne enrichi ;
- statistiques avancées et suivi de valeur de collection.

---

## 🤝 Contribution

Les contributions peuvent couvrir l'amélioration des fonctionnalités Flutter, de l'expérience utilisateur, de l'intégration Firebase et des règles de sécurité. Toute évolution touchant à Firestore, Storage ou Cloud Functions doit rester cohérente avec l'architecture backend déjà en place et avec les bonnes pratiques du projet.

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
