# Cahier des charges (SRS) — TeamFlow

**Équipe :** Akram Naamane, Alaeeddine Moumene  
**Date :** 2026-01-19  
**Version :** v2.0  

---

# 1. Contexte & Objectif

## 1.1 Contexte

Les équipes de travail rencontrent souvent des difficultés dans la gestion des horaires, de la présence et des communications internes.

TeamFlow est une application web permettant de centraliser ces fonctionnalités dans un seul outil accessible via un navigateur.

## 1.2 Objectif principal

Faciliter la gestion d’une équipe en permettant :

- La gestion des équipes
- La planification des shifts
- Le pointage (check-in / check-out)
- La consultation de la présence
- La communication via chat (groupe et privé)

## 1.3 Parties prenantes

- Chef d’équipe
- Employé

---

# 2. Portée (Scope)

## 2.1 Inclus (Scope IN – V1)

- IN-1 : Authentification et gestion des rôles
- IN-2 : Gestion des équipes
- IN-3 : Demandes d’adhésion (rejoindre équipe)
- IN-4 : Tableau de bord de présence
- IN-5 : Création et gestion des shifts
- IN-6 : Système de pointage (check-in / check-out)
- IN-7 : Chat de groupe
- IN-8 : Messagerie privée

## 2.2 Exclu (Scope OUT – V1)

- OUT-1 : Appels audio/vidéo
- OUT-2 : Messagerie avancée (fichiers, réactions)
- OUT-3 : Application mobile native
- OUT-4 : Intégrations externes
- OUT-5 : Gestion RH avancée

---

# 3. Acteurs

## 3.1 Chef d’équipe

### Rôle

- Créer une équipe
- Gérer les membres (accepter/refuser)
- Planifier les shifts
- Consulter la présence
- Accéder à l’historique

### Contraintes

- Interface simple
- Accès rapide via navigateur

---

## 3.2 Employé

### Rôle

- Rejoindre une équipe
- Consulter ses shifts
- Faire check-in / check-out
- Envoyer des messages

### Contraintes

- Accès limité à ses données
- Utilisation sur mobile ou PC

---

# 4. Exigences Fonctionnelles (FR)

---

## FR-01 : Authentification

Connexion avec email et mot de passe.

✔ Accès autorisé si valide  
✔ Message d’erreur sinon  
✔ Accès bloqué sans session  

---

## FR-02 : Gestion des équipes

Le chef peut créer une équipe.

✔ Nom obligatoire  
✔ Un chef par équipe  

---

## FR-03 : Demande d’adhésion

Un employé peut rejoindre une équipe.

✔ Demande envoyée  
✔ Acceptée ou refusée par le chef  

---

## FR-04 : Gestion des membres

Le chef peut :

✔ accepter  
✔ refuser  
✔ voir les membres  

---

## FR-05 : Gestion des shifts

✔ Création de shifts  
✔ Assignation à un employé  
✔ Modification et suppression  

---

## FR-06 : Consultation des shifts

✔ L’employé voit uniquement ses shifts  
✔ Mise à jour automatique  

---

## FR-07 : Pointage

✔ Check-in au début  
✔ Check-out à la fin  
✔ Heure réelle enregistrée  

---

## FR-08 : Présence

✔ Affichage des présences  
✔ Accès réservé au chef  

---

## FR-09 : Chat de groupe

✔ Messages visibles par l’équipe  
✔ Historique conservé  

---

## FR-10 : Messagerie privée

✔ Messages entre 2 utilisateurs  
✔ Historique conservé  

---

# 5. Exigences Non Fonctionnelles (NFR)

---

## NFR-01 (Performance)

Chargement ≤ 2 secondes  

---

## NFR-02 (Sécurité)

- Authentification obligatoire  
- Vérification des rôles  
- Sécurisation backend  

---

## NFR-03 (Disponibilité)

Accessible via navigateur  

---

## NFR-04 (UX)

Actions simples en ≤ 3 clics  

---

## NFR-05 (Compatibilité)

- Chrome  
- Firefox  
- Edge  
- Mobile + Desktop  

---

## NFR-06 (Maintenabilité)

Architecture séparée :

- Frontend (Angular)
- Backend (Node.js / Express)
- Service métier (TeamService)

---

# 6. Contraintes

- C-1 : JavaScript (Angular + Node.js)
- C-2 : Plateforme Web
- C-3 : Délai académique
- C-4 : UML obligatoire

---

# 7. Données & Règles Métier

## 7.1 Entités

- User
- Team
- TeamMember
- Shift
- Attendance
- Message

---

## 7.2 Règles métier

- Un utilisateur peut appartenir à une équipe
- Une équipe contient plusieurs membres
- Seul le chef gère les shifts
- Un employé pointe uniquement sur ses shifts
- Les messages privés sont limités aux participants
- Les messages publics sont visibles par l’équipe

---

# 8. Hypothèses & Dépendances

## 8.1 Hypothèses

- Les utilisateurs ont un compte
- Accès internet disponible
- Interface simple

## 8.2 Dépendances

- Backend API
- Base de données SQLite
- Frontend Angular

---

# 9. Critères d’acceptation (Definition of Done)

- [x] Fonctionnalités principales implémentées
- [x] Gestion des erreurs
- [x] UML complet
- [x] ADR + SRS cohérents
- [x] Application fonctionnelle sur navigateur
