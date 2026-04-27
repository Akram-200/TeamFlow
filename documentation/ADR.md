# ADR-01 — Choix d’une architecture Web App Client–Serveur REST

**Statut :** Accepted  
**Date :** 2026-01-25  
**Dernière mise à jour :** 2026-04-26  
**Décideurs :** Alaeeddine Moumene, Akram Naamane  
**Contexte projet :** TeamFlow — Application de gestion d’équipe, de shifts, de présence et de communication  

---

## 1. Contexte

### Problème / besoin

Le système TeamFlow doit être accessible aux employés et aux chefs d’équipe :

- Sur mobile et desktop  
- Sans installation obligatoire  
- Avec gestion :
  - des utilisateurs  
  - des rôles (Chef / Employé)  
  - des équipes  
  - des shifts  
  - de la présence (check-in / check-out)  
  - des chats privés et publics  

---

### Contraintes

- Accessibilité web requise  
- Maintenabilité et simplicité  
- Budget et temps limités (MVP)  
- Méthodologie imposée : SDLC + documentation + UML  

---

### Forces en présence

- Simplicité de déploiement  
- Performance suffisante  
- Séparation frontend / backend  
- Risque lié à la dépendance réseau  

---

## 2. Décision

Nous choisissons une architecture **Web Application Client–Serveur basée sur une API REST**.

Le frontend (interface web Angular) consomme une API backend via HTTP.  
La logique métier est isolée côté serveur dans un service dédié.

Architecture :

Frontend (Angular)
↓
API REST (Express)
↓
Service métier (TeamService)
↓
Base de données (SQLite)


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
- Permet une évolution progressive du système  
- Assure une séparation claire des responsabilités  

---

## 5. Conséquences

### Positives

- Accessibilité multiplateforme (desktop + mobile navigateur)  
- Mise à jour instantanée côté serveur  
- Architecture modulaire et évolutive  
- Adoption facilitée par les utilisateurs  
- Organisation claire du code (Frontend / Backend / Service / DB)  

---

### Négatives / Risques

- Dépendance à la connexion internet  
- Sécurisation réseau nécessaire  
- Messagerie non temps réel (limitation actuelle)  
- Stockage des mots de passe à améliorer (hash recommandé)  

---

### Impact sur l’architecture

- Le backend expose des endpoints REST :
  - authentification  
  - équipes  
  - membres  
  - shifts  
  - présence  
  - messages  

- Le frontend communique avec l’API via `ApiService`.

- La logique métier est centralisée dans `TeamService`.

- La base SQLite contient :
  - users  
  - teams  
  - team_members  
  - shifts  
  - attendance  
  - messages  

- Authentification basée sur **sessions**.

---

## 6. Plan d’implémentation

- [x] Définir la structure frontend  
- [x] Définir les endpoints REST backend  
- [x] Implémenter l’authentification  
- [x] Implémenter la gestion des équipes  
- [x] Implémenter les rôles et demandes d’adhésion  
- [x] Implémenter la gestion des shifts  
- [x] Implémenter le check-in / check-out  
- [x] Implémenter la gestion de la présence  
- [x] Implémenter la messagerie (public + privé)  
- [x] Tester les communications client–serveur  

---

## 7. Validation

La décision sera validée si :

- L’application fonctionne entièrement depuis un navigateur sans installation  
- L’interface web communique correctement avec l’API  
- Les utilisateurs peuvent s’inscrire et se connecter  
- Les équipes peuvent être créées et rejointes  
- Les shifts et la présence fonctionnent correctement  
- La messagerie fonctionne  
- Les modules frontend et backend sont clairement séparés  

---

## 8. Liens
- UML : diagramme
<img width="572" height="261" alt="Capture d’écran 2026-04-26 231723" src="https://github.com/user-attachments/assets/b1c781aa-46ef-4101-b954-7945f5481c6e" />

<img width="716" height="265" alt="Capture d’écran 2026-04-26 231616" src="https://github.com/user-attachments/assets/f966fe0f-2eae-450f-997f-e4af9f7c7c92" />

<img width="527" height="213" alt="Capture d’écran 2026-04-26 231522" src="https://github.com/user-attachments/assets/dc43d393-2e32-486f-94c6-8fbdb162ed55" />

<img width="841" height="606" alt="WhatsApp Image 2026-04-26 at 11 19 40 PM" src="https://github.com/user-attachments/assets/3d3a4d49-1734-4505-a0e6-de82a583a06b" />

<img width="865" height="257" alt="Capture d’écran 2026-04-26 231316" src="https://github.com/user-attachments/assets/ad058024-3f71-4980-b4c4-11c792f02e10" />

<img width="792" height="749" alt="WhatsApp Image 2026-04-26 at 11 28 40 PM" src="https://github.com/user-attachments/assets/f763b132-b5b7-42c9-8f7c-e86c15bb0b2f" />

<img width="952" height="587" alt="WhatsApp Image 2026-04-26 at 11 31 16 PM" src="https://github.com/user-attachments/assets/0e06d8fa-3a94-4484-aea6-0b152259d404" />





