# 📘 Plateforme d'Évaluation Technique – Spécifications

## Vue d'ensemble

Plateforme web locale d'évaluation technique pour le recrutement de développeurs, basée sur une architecture microservices avec API Gateway et moteur d’exécution externalisé.

### Problématique

- Les évaluations manuelles sont lentes et incohérentes.
- Difficulté à scaler les tests avec plusieurs candidats simultanément.

### Solution proposée

- Plateforme web avec interface **Next.js** pour les utilisateurs.
- **API Gateway Java** centralisant les requêtes vers les microservices (Auth, Test, Result).
- Exécution du code via **Judge0 self-hosted** en sandbox Docker.
- Gestion centralisée des données dans **PostgreSQL**.

### Utilisateurs cibles

- **Interviewer**: Crée et gère les évaluations.
- **Candidate**: Passe les tests et soumet le code.
- **Administrator**: Supervise la plateforme et les utilisateurs.

---

## 📋 Objectifs et Périmètre

### Objectifs Métier

- Créer et gérer des évaluations chronométrées.
- Permettre aux candidats de passer des tests dans une fenêtre définie.
- Évaluer automatiquement les soumissions.
- Fournir des résultats détaillés et objectifs.
- Notifier candidats et recruteurs.

### Objectifs Techniques

- **Frontend**: Next.js avec React 18+ (SSR et SPA selon besoins).
- **Backend**: Java API Gateway avec microservices dédiés.
- **Base de données**: PostgreSQL centralisé.
- **Exécution code**: Docker sandbox via Judge0 API.
- **Authentification**: JWT + RBAC.
- **Notifications**: Emails.
- **Tests**: Unitaires, intégration et E2E.

---

## ✅ Périmètre IN (Fonctionnalités)

| Fonctionnalité               | Description |
|-------------------------------|------------|
| Authentification              | Login/register via Auth Service, JWT, gestion de rôles. |
| Gestion d’Assessments         | CRUD assessments via Test Service. |
| Problèmes & cas de test       | Définition de problèmes et test cases via Test Service. |
| Invitations                   | Envoi email avec token via Test Service. |
| Fenêtre de disponibilité      | Vérification côté Test Service. |
| Durée d’examen                | Chronomètre côté frontend, validé via Test Service. |
| Soumission de code            | Frontend envoie à Result Service pour exécution Judge0. |
| Exécution automatique         | Judge0 exécute le code en sandbox Docker. |
| Calcul de score               | Result Service calcule le scoring automatiquement. |
| Dashboard résultats           | Visualisation via frontend, data fournie par Result Service. |
| Notifications email           | Emails automatiques via Result Service. |

### ❌ Périmètre OUT

- IA pour correction.
- Anti-plagiat avancé.
- Surveillance vidéo.
- Support multi-langues avancé.
- Scalabilité niveau production haute.

---
## 🏗 Architecture du Système

### Schéma d’Architecture ASCII

<img width="832" height="1248" alt="schema" src="https://github.com/user-attachments/assets/20e759b7-38e1-4476-960f-616262167e9f" />


### Acteurs et Rôles

| Acteur      | Responsabilités |
|------------|----------------|
| Interviewer | Crée assessments, définit problèmes, invite candidats, consulte résultats |
| Candidate   | Reçoit invitation, passe test, soumet code, consulte résultats |
| Admin       | Gère utilisateurs, supervise plateforme |

### Processus Principal (Workflow)

1. Interviewer crée un assessment → Test Service.
2. Configuration (durée, disponibilité, problèmes).
3. Invitations envoyées → Test Service.
4. Candidate démarre le test via Next.js frontend → Auth Service valide.
5. Chronomètre lancé → frontend + Test Service.
6. Soumission de code → Result Service → Judge0 API pour exécution.
7. Score calculé → Result Service.
8. Résultats affichés + email → Result Service.

---

## 📊 Modèle de Données

| Entité         | Champs Principaux |
|----------------|-----------------|
| Users           | id, email, password_hash, role, created_at |
| Assessments     | id, title, description, creator_id, availability_start/end, duration_minutes, created_at |
| Problems        | id, assessment_id, title, description, difficulty, points |
| TestCases       | id, problem_id, input, expected_output, is_hidden, weight |
| Invitations     | id, assessment_id, candidate_id, token, status, sent_at, expires_at |
| Submissions     | id, invitation_id, problem_id, code, language, submitted_at, status |
| Scores          | id, submission_id, test_cases_passed, test_cases_total, points_earned, execution_time_ms |

---

## 🛠 Stack Technique

### Frontend (Next.js)

- React 18+, TypeScript recommandé.
- State Management: Redux Toolkit ou Context API.
- UI Components: Material-UI ou shadcnUI.
- Code Editor: Monaco Editor.
- HTTP Client: Axios.
- Routing: Next.js routing (SSR/SPA).

### Backend (Java API Gateway + Microservices)

- Framework: JEE / Spring Boot possible pour microservices.
- Microservices: Auth, Test, Result.
- API: RESTful, JSON, JWT.
- ORM: JPA/Hibernate.
- Validation: Bean Validation.
- Sécurité: RBAC + JWT.
- Documentation: OpenAPI/Swagger.

### Execution Engine

- Judge0 API self-hosted.
- Docker sandbox: CPU, mémoire, timeout stricts.
- Support langages: Python, Java, JavaScript (extensible).

### Base de Données

- PostgreSQL 14+, centralisé.
- Migration: Flyway.
- Stockage des résultats, submissions, users, assessments.

---

## 🔒 Sécurité

| Aspect                  | Mesure |
|-------------------------|--------|
| Authentification        | JWT avec refresh tokens, Auth Service dédié |
| Autorisation            | RBAC via API Gateway |
| Validation temporelle    | Test Service vérifie disponibilité et durée |
| Isolation d'exécution    | Judge0 + Docker sandbox |
| Injection SQL            | Prepared statements (JPA) |
| XSS                      | Sanitization des inputs |
| CORS                     | Configuration stricte |

---

## ✅ Tests

- **Unitaires**: scoring, validation soumissions, logique métier.
- **Intégration**: endpoints API REST, workflow invitation → submission → scoring.
- **Fonctionnels**: scénarios utilisateurs bout-en-bout, chronomètre, notifications.
- **Performance**: tests charge basiques.

---

## 🚀 Déploiement

- Local: docker-compose (DB + API Gateway + services + frontend dev).
- Backend: Dockerfile JEE.
- Frontend: Build Next.js statique servi par nginx ou Vercel.
- Execution Engine: Judge0 containerisé.
- Cloud: AWS/Azure/GCP (optionnel).

---

## 📅 Backlog & Planning (Sprints)

- **Sprint 1**: Auth + setup microservices.
- **Sprint 2**: CRUD assessments & invitations, spike Judge0.
- **Sprint 3**: Soumission, execution, scoring.
- **Sprint 4**: Dashboard complet, notifications, tests, documentation.

---

## 🔧 Recommandations Techniques Critiques

- **Execution Engine**: Judge0 self-hosted pour sécurité et multi-langages.
- **Error Handling**: Timeout, memory overflow, compilation/runtime errors → messages clairs.
- **API Contract**: OpenAPI 3.0 dès Sprint 1.
- **Front-to-back coordination**: API Gateway centralise toutes les requêtes vers microservices.
- **Sécurité containers**: CPU/memory limits, read-only filesystem, network disabled.

---

## 🎯 Points Clés de Succès

- MVP fonctionnel avant fonctionnalités avancées.
- Sécurité stricte sur Judge0 Docker.
- Tests continus + démos régulières.
- Documentation à jour tout au long du projet.

---

## 📚 Ressources Utiles

- React Documentation
- JEE Tutorial
- Docker Security Best Practices
- JWT.io
- Monaco Editor
- OpenAPI Specification
- Judge0 - Solution complète open-source
- Piston - Code execution engine
- docker-py - SDK Python pour Docker
- Sphere Engine - Solution commerciale (référence)

---

## 👥 Organisation de l'Équipe

| Rôle             | Responsabilités |
|-----------------|----------------|
| Scrum Master      | Anime les sprints, supprime les blocages |
| Product Owner     | Priorise le backlog, valide les features |
| Référent Backend  | Architecture JEE, API REST |
| Référent Frontend | Application Next.js, UX |
| Référent DevOps   | Docker, exécution, déploiement |
| Référent Qualité  | Tests, documentation, métriques |

**Communication**: Daily stand-up: 10 min chaque jour (optionnel pour équipe étudiante)
