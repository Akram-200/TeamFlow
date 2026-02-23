# ADR-01 — Choix d’une architecture Web App Client–Serveur REST

**Statut :** Accepted  
**Date :** 2026-01-25  
**Décideurs :** Alaeeddine Moumene, Akram Naamane  
**Contexte projet :** TeamFlow — Application de gestion d’équipe et de shifts  

---

## 1. Contexte

### Problème / besoin

Le système TeamFlow doit être accessible aux employés et aux chefs d’équipe :

- Sur mobile et desktop
- Sans installation obligatoire
- Avec gestion :
  - des utilisateurs
  - des rôles
  - des shifts
  - de la présence
  - des chats privés et publics

### Contraintes

- Accessibilité web requise
- Maintenabilité et simplicité
- Budget et temps limités (MVP)
- Méthodologie imposée : SDLC + documentation + UML

### Forces en présence

- Simplicité de déploiement
- Performance suffisante
- Séparation frontend / backend
- Risque lié à la dépendance réseau

---

## 2. Décision

Nous choisissons une architecture **Web Application Client–Serveur basée sur une API REST**.

Le frontend (interface web) consommera une API backend via HTTP.  
La logique métier sera isolée côté serveur.

Cette architecture permet :

- Une séparation claire entre interface utilisateur et logique métier
- Une meilleure maintenabilité
- Un accès depuis n’importe quel navigateur moderne

---

## 3. Alternatives considérées

### Option A — Application Mobile Native

**Avantages :**
- Expérience utilisateur optimisée
- Notifications push natives
- Meilleure intégration système

**Inconvénients :**
- Développement et maintenance plus coûteux
- Complexité multiplateforme (iOS / Android)
- Non nécessaire pour un MVP académique

---

### Option B — Application Desktop

**Avantages :**
- Performances locales élevées
- Gestion simplifiée des ressources locales

**Inconvénients :**
- Installation obligatoire
- Non adaptée à l’usage mobile
- Complexité de distribution et mise à jour

---

## 4. Justification

Cette décision est retenue car :

- Compatible avec l’usage sur postes partagés
- Déploiement centralisé
- Conforme aux exigences du cours (SDLC + UML)
- Réduit la charge de maintenance
- Permet une évolution agile du système
- Assure une séparation claire des responsabilités

---

## 5. Conséquences

### Positives

- Accessibilité multiplateforme (desktop + mobile navigateur)
- Mise à jour instantanée côté serveur
- Architecture modulaire et évolutive
- Adoption facilitée par les utilisateurs

---

### Négatives / Risques

- Dépendance à la connexion internet
- Sécurisation réseau nécessaire
- Gestion du temps réel à prévoir pour le chat

---

### Impact sur l’architecture

- Le backend exposera des endpoints REST (authentification, shifts, utilisateurs, chat).
- Le frontend récupérera les données via fetch ou axios.
- Le module chat nécessitera un mécanisme temps réel (WebSocket ou polling optimisé).
- Authentification via token (JWT) ou sessions sécurisées.

---

## 6. Plan d’implémentation

- [ ] Définir la structure frontend.
- [ ] Définir les endpoints REST backend.
- [ ] Implémenter l’authentification.
- [ ] Implémenter la gestion des shifts.
- [ ] Intégrer le module chat.
- [ ] Tester les communications client–serveur.

---

## 7. Validation

La décision sera validée si :

- L’application fonctionne entièrement depuis un navigateur sans installation.
- L’interface web communique correctement avec l’API.
- Les fonctionnalités principales (authentification, shifts, présence) fonctionnent indépendamment du device.
- Les modules frontend et backend sont clairement séparés.

---

## 8. Liens
- UML : diagramme de classe
<img width="731" height="594" alt="Diagramme de classes drawio" src="https://github.com/user-attachments/assets/6e8989f2-41a0-4c6a-bd91-be46f4f7f8b4" />

Ce diagramme de classes représente la structure principale du système TeamFlow.
Une Équipe contient plusieurs Users (relation 1-N).
Chaque User peut avoir plusieurs Shifts et effectuer des Pointages.
Un Shift peut générer un ou plusieurs Pointages (check-in / check-out).
Les Users peuvent également envoyer plusieurs Messages, qui peuvent être de type groupe ou privé.




-UML: Use Case Chef d'equipe
<img width="903" height="946" alt="useCase Chef dequipe drawio" src="https://github.com/user-attachments/assets/964cc050-35f2-42e1-b591-ca2c57e2f99a" />

UML use case employé :

![uml](https://github.com/user-attachments/assets/eb3401e0-5959-4273-b7a1-7f8b06d73c0c)

