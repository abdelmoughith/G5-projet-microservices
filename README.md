# 🎓 EduPath-MS - Learning Analytics & Recommandations

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Java](https://img.shields.io/badge/Java-21-orange.svg)](https://www.oracle.com/java/)
[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688.svg)](https://fastapi.tiangolo.com/)

> Plateforme d'apprentissage intelligent pour améliorer la qualité de l'enseignement et optimiser l'accompagnement des étudiants grâce à l'intelligence artificielle et l'analyse prédictive.

## 📋 Table des matières

- [À propos](#-à-propos)
- [Fonctionnalités](#-fonctionnalités)
- [Architecture](#-architecture)
- [Technologies](#-technologies)
- [Prérequis](#-prérequis)
- [Installation](#-installation)
- [Démarrage](#-démarrage)
- [Services et Ports](#-services-et-ports)
- [Structure du Projet](#-structure-du-projet)
- [Utilisation](#-utilisation)
- [Modèle d'IA](#-modèle-dintelligence-artificielle)
- [CI/CD](#-cicd)
- [Contribution](#-contribution)
- [Auteurs](#-auteurs)
- [Licence](#-licence)

## 🎯 À propos

**EduPath-MS** est une plateforme d'apprentissage intelligent conçue pour améliorer la qualité de l'enseignement et optimiser l'accompagnement des étudiants grâce à une architecture microservices distribuée. Elle combine des services métier développés en **Spring Boot** et un moteur d'intelligence artificielle implémenté en **FastAPI**, chargé d'effectuer l'analyse prédictive des performances académiques et de générer des recommandations pédagogiques personnalisées.

### Innovation Clé

Contrairement aux plateformes traditionnelles, EduPath-MS utilise **exclusivement des fichiers CSV** pour la persistance des données pédagogiques, évitant la complexité des bases de données relationnelles. Cette approche permet :

- ✅ Réduction des coûts d'infrastructure
- ✅ Portabilité élevée
- ✅ Facilité d'exploitation pour l'analyse et l'entraînement des modèles d'IA
- ✅ Interopérabilité avec d'autres outils (Excel, Python, outils statistiques)

## ✨ Fonctionnalités

### 🎓 Gestion Pédagogique
- **Gestion des utilisateurs** : Création, consultation et mise à jour des profils étudiants et enseignants
- **Gestion des cours** : Organisation des cours, modules et ressources pédagogiques
- **Suivi des activités** : Enregistrement automatique des interactions et de la progression
- **Analytics** : Calcul d'indicateurs académiques et statistiques globales

### 🤖 Intelligence Artificielle
- **Prédiction de réussite** : Modèle XGBoost avec **80.32% d'accuracy** et **AUC-ROC de 0.85**
- **Identification des risques** : Détection précoce des étudiants à risque d'échec
- **Recommandations personnalisées** :
  - Révisions des chapitres fondamentaux
  - Proposition de ressources complémentaires
  - Ajustement du rythme d'apprentissage
  - Suggestions d'accompagnement pédagogique

### 📊 Tableaux de Bord
- **Tableau de bord étudiant** : Recommandations, progression, performances
- **Tableau de bord enseignant** : Vue globale de la classe, étudiants à risque
- **Tableau de bord IA** : Visualisation des prédictions et métriques

## 🏗️ Architecture

EduPath-MS repose sur une **architecture microservices** distribuée avec les composants suivants :

```
┌─────────────────────────────────────────────────────────────┐
│                      Frontend (React)                       │
│                         Port: 3000                          │
└───────────────────────┬─────────────────────────────────────┘
                        │
┌───────────────────────▼─────────────────────────────────────┐
│                    API Gateway                              │
│                    Port: 8089                               │
└───┬──────┬──────┬──────┬──────┬──────┬──────────────────────┘
    │      │      │      │      │      │
    │      │      │      │      │      └───► EduPath ML (FastAPI)
    │      │      │      │      │            Port: 8000
    │      │      │      │      │
    │      │      │      │      └───► Analytics Service
    │      │      │      │            Port: 8084
    │      │      │      │
    │      │      │      └───► Activity Service
    │      │      │            Port: 8083
    │      │      │
    │      │      └───► Course Service
    │      │            Port: 8082
    │      │
    │      └───► User Service
    │            Port: 8081
    │
    └───► Eureka Server (Service Discovery)
          Port: 3334
          
    └───► Config Server (Configuration Centralisée)
          Port: 8888
```

### Services

| Service | Port | Technologie | Description |
|---------|------|-------------|-------------|
| **Config Server** | 8888 | Spring Cloud Config | Configuration centralisée |
| **Eureka Server** | 3334 | Netflix Eureka | Service discovery |
| **API Gateway** | 8089 | Spring Cloud Gateway | Point d'entrée unique |
| **User Service** | 8081 | Spring Boot | Gestion des utilisateurs |
| **Course Service** | 8082 | Spring Boot | Gestion des cours |
| **Activity Service** | 8083 | Spring Boot | Suivi des activités |
| **Analytics Service** | 8084 | Spring Boot | Analytics et statistiques |
| **EduPath ML** | 8000 | FastAPI (Python) | Intelligence artificielle |
| **Frontend** | 3000 | React | Interface utilisateur |

## 🛠️ Technologies

### Backend
- **Java 21** (ou Java 17 LTS)
- **Spring Boot 3.x** : Framework pour les microservices
- **Spring Cloud** :
  - Spring Cloud Config (configuration centralisée)
  - Netflix Eureka (service discovery)
  - Spring Cloud Gateway (API Gateway)
- **Maven** : Gestion des dépendances

### Machine Learning & IA
- **Python 3.11**
- **FastAPI** : Framework moderne pour le service d'IA
- **XGBoost** : Modèle de machine learning
- **Pandas, NumPy, Scikit-learn** : Bibliothèques ML

### Frontend
- **React** : Bibliothèque JavaScript
- **Node.js 18+** : Environnement d'exécution
- **npm** : Gestionnaire de paquets

### Infrastructure & DevOps
- **Docker** & **Docker Compose** : Conteneurisation et orchestration
- **GitHub Actions** : Pipeline CI/CD
- **Jenkins** : Pipeline CI/CD alternatif
- **Git Submodules** : Gestion multi-repositories

## 📦 Prérequis

Avant de commencer, assurez-vous d'avoir installé :

- **Docker** (version 20.10 ou supérieure)
- **Docker Compose** (version 2.0 ou supérieure)
- **Git** (pour cloner les sous-modules)

### Vérification de l'installation

```bash
docker --version
docker-compose --version
git --version
```

## 🚀 Installation

### 1. Cloner le repository

```bash
git clone https://github.com/abdelmoughith/G5-projet-microservices.git
cd G5-projet-microservices
```

### 2. Initialiser les sous-modules Git

```bash
git submodule update --init --recursive
```

### 3. Vérifier la structure

Assurez-vous que tous les dossiers suivants existent :
- `spring-config-global/`
- `eureka-server-global/`
- `gateway-global/`
- `user-service-global/`
- `course-service/`
- `activity-service/`
- `analytics-service-global/`
- `EduPath/` (service ML)
- `Edu-path-project/` (frontend)

## 🏃 Démarrage

### Démarrage rapide avec Docker Compose

```bash
# Démarrer tous les services
docker-compose up -d

# Voir les logs
docker-compose logs -f

# Voir les logs d'un service spécifique
docker-compose logs -f user-service

# Arrêter tous les services
docker-compose down

# Arrêter et supprimer les volumes
docker-compose down -v
```

### Ordre de démarrage

Les services démarrent automatiquement dans le bon ordre grâce aux dépendances définies dans `docker-compose.yml` :

1. **Config Server** (démarre en premier)
2. **Eureka Server** (attend que Config Server soit healthy)
3. **MySQL** (démarre en parallèle)
4. **API Gateway** (attend Config + Eureka)
5. **Services métier** (attendent Config + Eureka + MySQL)
6. **EduPath ML** (service indépendant)
7. **Frontend** (attend API Gateway + ML Service)

### Vérification du statut

```bash
# Vérifier que tous les conteneurs sont en cours d'exécution
docker-compose ps

# Vérifier les healthchecks
docker-compose ps --format "table {{.Name}}\t{{.Status}}"
```

### Accès aux services

Une fois démarrés, les services sont accessibles aux adresses suivantes :

- **Frontend** : http://localhost:3000
- **API Gateway** : http://localhost:8089
- **Eureka Dashboard** : http://localhost:3334
- **Config Server** : http://localhost:8888
- **EduPath ML API** : http://localhost:8000
- **User Service** : http://localhost:8081
- **Course Service** : http://localhost:8082
- **Activity Service** : http://localhost:8083
- **Analytics Service** : http://localhost:8084

## 📁 Structure du Projet

```
G5-projet-microservices/
├── docker-compose.yml              # Orchestration Docker
├── .gitmodules                     # Sous-modules Git
├── README.md                       # Ce fichier
│
├── Infrastructure Services
│   ├── spring-config-global/       # Config Server
│   ├── eureka-server-global/       # Eureka Server
│   └── gateway-global/             # API Gateway
│
├── Business Services
│   ├── user-service-global/        # User Service
│   ├── course-service/             # Course Service
│   ├── activity-service/           # Activity Service
│   └── analytics-service-global/  # Analytics Service
│
├── ML Service
│   └── EduPath/                    # Service Machine Learning (FastAPI)
│
├── Frontend
│   └── Edu-path-project/           # Application React
│
└── Configuration
    └── microservices-config/       # Configurations partagées
```

## 💻 Utilisation

### Accès à l'application

1. Ouvrez votre navigateur et accédez à : **http://localhost:3000**

2. **Inscription/Connexion** :
   - Créez un compte étudiant ou enseignant
   - Connectez-vous avec vos identifiants

3. **Fonctionnalités disponibles** :
   - **Étudiants** : Consultation des cours, suivi de progression, recommandations personnalisées
   - **Enseignants** : Gestion des cours, suivi des étudiants, tableaux de bord analytiques
   - **Administrateurs** : Gestion complète de la plateforme

### API REST

Toutes les requêtes passent par l'API Gateway (port 8089). Exemple :

```bash
# Obtenir les informations d'un utilisateur
curl http://localhost:8089/api/users/{userId}

# Obtenir les cours
curl http://localhost:8089/api/courses

# Obtenir les recommandations pour un étudiant
curl http://localhost:8089/api/ai/recommendations/{studentId}
```

## 📸 Captures d'Écran

Voici quelques captures d'écran des principales interfaces de la plateforme EduPath-MS :
![WhatsApp Image 2025-12-27 at 10 59 02](https://github.com/user-attachments/assets/1e047b86-9152-4a0e-a4da-3ac97f6a239c)
![WhatsApp Image 2025-12-27 at 10 58 07](https://github.com/user-attachments/assets/a3b9e32c-afbe-408a-85ad-4d4a8307c86f)
![WhatsApp Image 2025-12-27 at 10 57 43](https://github.com/user-attachments/assets/812d4ef1-b88d-4583-be8c-0097aa41c2c6)
![WhatsApp Image 2025-12-27 at 10 54 42](https://github.com/user-attachments/assets/0b414bda-869f-4624-bc78-dd2273f9b84d)
![WhatsApp Image 2025-12-27 at 10 54 38](https://github.com/user-attachments/assets/71e6396f-d562-4674-a304-63984f0985ce)
![WhatsApp Image 2025-12-27 at 11 08 42](https://github.com/user-attachments/assets/fe81f6e1-afa0-48fd-8484-f6ab4fa1086e)
![WhatsApp Image 2025-12-27 at 11 03 35](https://github.com/user-attachments/assets/cb2edca4-8535-4a7f-b7df-f340d7c3292a)
![WhatsApp Image 2025-12-27 at 11 03 08](https://github.com/user-attachments/assets/1e6ebbbd-a93a-482c-a530-b990991734dd)
![WhatsApp Image 2025-12-27 at 11 01 40](https://github.com/user-attachments/assets/817b1379-722c-4079-8ac0-a1f526fdfa4b)
![WhatsApp Image 2025-12-27 at 11 00 47](https://github.com/user-attachments/assets/e40a7b4b-7b0e-4bac-8c75-3ce8e3e29800)
![WhatsApp Image 2025-12-27 at 11 00 30](https://github.com/user-attachments/assets/87c512a7-e58f-44a2-b94f-24ee91918a65)
![WhatsApp Image 2025-12-27 at 10 59 51](https://github.com/user-attachments/assets/bf96668b-46e5-42a1-89a0-32527d01239c)
![WhatsApp Image 2025-12-27 at 10 59 33](https://github.com/user-attachments/assets/8d982c6a-18a7-44e5-a5b2-99ddc92bb1da)


### Interfaces Utilisateur

- **Page de connexion** : Interface d'authentification pour étudiants et enseignants
- **Page d'inscription** : Formulaire d'enregistrement des nouveaux utilisateurs
- **Tableau de bord étudiant** : Vue d'ensemble de la progression et des recommandations
- **Catalogue des cours** : Liste complète des modules disponibles
- **Vue d'un cours** : Interface de lecture et d'interaction avec le contenu pédagogique
- **Évaluations** : Page de tests et quiz pour les étudiants
- **Tableau de bord IA** : Visualisation des prédictions de réussite et métriques
- **Tableau de bord administrateur**



## 🤖 Modèle d'Intelligence Artificielle

### Dataset

Le modèle est entraîné sur le **dataset OULAD** (Open University Learning Analytics Dataset) :
- **32 593 étudiants**
- **10 655 280 interactions VLE**
- **173 912 évaluations**
- **22 modules**
- **6 364 ressources pédagogiques**

### Modèle XGBoost

- **Algorithme** : eXtreme Gradient Boosting
- **Tâche** : Classification binaire (Réussite/Échec)
- **Features** : 15 variables regroupées en 4 catégories :
  1. Démographiques et académiques
  2. Engagement VLE (clics, interactions)
  3. Performance académique (scores)
  4. Historique (tentatives précédentes)

### Performances

- **Accuracy** : **80.32%**
- **Precision** : 0.82
- **Recall** : 0.79
- **F1-Score** : 0.80
- **AUC-ROC** : **0.85** (excellente capacité de discrimination)

### Pipeline de Traitement

1. **Normalisation** (LMS Connector) : Préparation des données brutes
2. **Feature Engineering** (Prepa Data) : Création des features
3. **Profilage** (Student Profiler) : Analyse des profils étudiants
4. **Prédiction** (Path Predictor) : Génération des prédictions et recommandations

<img width="1919" height="949" alt="image" src="https://github.com/user-attachments/assets/1369a7cd-35cd-49a9-9470-02c85b3e68f0" />
<img width="1919" height="947" alt="image" src="https://github.com/user-attachments/assets/946f4729-76ff-4b9c-b417-3658d8ca6cb5" />
<img width="1919" height="947" alt="image" src="https://github.com/user-attachments/assets/463af15b-1fe6-4d54-bdd3-3f2557366606" />


## 🔄 CI/CD

Le projet utilise un pipeline CI/CD automatisé :

### GitHub Actions

À chaque `push` ou `pull request`, le pipeline exécute :
1. Récupération du code source
2. Compilation et tests
3. Construction des images Docker
4. Publication sur registre Docker
5. Déploiement automatisé sur VPS

### Jenkins

Pipeline alternatif avec les étapes suivantes :
1. Clonage du dépôt Git
2. Compilation et exécution des tests
3. Construction de l'image Docker
4. Lancement du conteneur
5. Vérification du bon fonctionnement

### Déploiement

- **Environnement** : VPS Hostinger, Ubuntu 24 LTS
- **Orchestration** : Docker Compose
- **Versionnement** : Images Docker versionnées (latest, v1.0, v1.1, etc.)

## 🤝 Contribution

Les contributions sont les bienvenues ! Pour contribuer :

1. Fork le projet
2. Créez une branche pour votre fonctionnalité (`git checkout -b feature/AmazingFeature`)
3. Committez vos changements (`git commit -m 'Add some AmazingFeature'`)
4. Push vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrez une Pull Request

### Standards de code

- Suivez les conventions de nommage Java/Python
- Ajoutez des tests pour les nouvelles fonctionnalités
- Documentez votre code
- Assurez-vous que tous les tests passent

## 👥 Auteurs

- **HEDDAJI Malika**
- **LEMKHANTAR Abdelmoughith**
- **ZAKI EL IDRISSI Abdallah**
- **ELKHASSIBI Khawla**
- **TAOUFIK Mohamed Amine**

**Institution** : École Marocaine des Sciences de l'Ingénieur (EMSI), Membre de Honoris United Universities, Maroc

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.

## 🔗 Liens Utiles

- **Repository principal** : https://github.com/abdelmoughith/G5-projet-microservices
- **Gateway** : https://github.com/abdelmoughith/gateway-global
- **Documentation** : https://github.com/abdelmoughith/G5-projet-microservices
- **Contact** : contact@edupath-ms.com

## 📊 Statistiques du Projet

- **Version** : v1.0
- **Services** : 9 microservices
- **Langages** : Java 21, Python 3.11, JavaScript (React)
- **Architecture** : Microservices avec Spring Cloud
- **Persistance** : Fichiers CSV
- **Modèle ML** : XGBoost (Accuracy: 80.32%)

## ⚠️ Notes Importantes

- Les données pédagogiques sont stockées dans des **fichiers CSV** (pas de base de données relationnelle)
- Tous les services doivent être démarrés pour que la plateforme fonctionne correctement
- Le service ML nécessite des données d'entraînement pour fonctionner
- En production, changez les mots de passe par défaut dans `docker-compose.yml`

## 🐛 Dépannage

### Problèmes courants

**Les services ne démarrent pas :**
```bash
# Vérifier les logs
docker-compose logs

# Redémarrer un service spécifique
docker-compose restart user-service
```

**Erreur de connexion à Eureka :**
- Vérifiez que le Config Server est démarré et accessible
- Attendez que le healthcheck du Config Server soit validé

**Le frontend ne se connecte pas à l'API :**
- Vérifiez que l'API Gateway est démarré (port 8089)
- Vérifiez les logs du frontend : `docker-compose logs front`

**Problèmes avec les sous-modules Git :**
```bash
# Réinitialiser les sous-modules
git submodule deinit --all
git submodule update --init --recursive
```

## 📈 Roadmap

- [ ] Enrichissement des données d'apprentissage (forums, interactions multimédias)
- [ ] Amélioration de la précision des prédictions (modèles plus avancés)
- [ ] Personnalisation avancée des recommandations
- [ ] Tests de charge et optimisation des performances
- [ ] Application mobile
- [ ] Intégration avec Moodle, Google Classroom
- [ ] Modèle SaaS éducatif

---

⭐ Si ce projet vous a aidé, n'hésitez pas à lui donner une étoile !

