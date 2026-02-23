# Cahier des charges (SRS) — TeamFlow

**Équipe :** Akram Naamane, Alaeeddine Moumene  
**Date :** 2026-01-19  
**Version :** v1.0  

---

# 1. Contexte & Objectif

## 1.1 Contexte

Les équipes de travail rencontrent souvent des difficultés dans la gestion des horaires, de la présence et des communications internes.

TeamFlow est une application web destinée à centraliser ces fonctionnalités dans un seul outil simple et accessible depuis un navigateur.

## 1.2 Objectif principal

Faciliter la gestion opérationnelle d’une équipe en permettant :

- La planification des shifts
- Le pointage (check-in / check-out)
- La consultation de la présence en temps réel
- La communication via chat (groupe et privé)

## 1.3 Parties prenantes

- Chef d’équipe
- Employé

---

# 2. Portée (Scope)

## 2.1 Inclus (Scope IN – V1)

- IN-1 : Authentification et gestion des rôles
- IN-2 : Tableau de bord de présence
- IN-3 : Création, modification et suppression des shifts
- IN-4 : Système de pointage (check-in / check-out)
- IN-5 : Chat de groupe
- IN-6 : Messagerie privée

## 2.2 Exclu (Scope OUT – V1)

- OUT-1 : Gestion d’appels vocaux ou vidéo
- OUT-2 : Messagerie avancée (fichiers, réactions, etc.)
- OUT-3 : Application mobile native
- OUT-4 : Intégrations externes (Slack, Google, etc.)
- OUT-5 : Gestion RH avancée ou paie

---

# 3. Acteurs

## 3.1 Chef d’équipe

### Rôle
- Configure l’équipe
- Gère les employés
- Planifie les shifts
- Consulte les présences
- Accède à l’historique des pointages

### Contraintes
- Interface simple et rapide
- Accessible via navigateur (desktop ou mobile)

---

## 3.2 Employé

### Rôle
- Consulte ses horaires
- Se pointe au début et à la fin du shift
- Utilise le chat

### Contraintes
- Peut utiliser un téléphone ou un poste partagé
- N’a pas accès aux données des autres employés

---

# 4. Exigences Fonctionnelles (FR)

---

## FR-01 : Authentification

Le système doit permettre à un utilisateur de se connecter avec un rôle (chef d’équipe ou employé).  
**Priorité : Must**

**Critères de validation :**
1. Identifiants valides → accès accordé.
2. Identifiants invalides → message d’erreur.
3. Accès interdit si non authentifié.

---

## FR-02 : Gestion des comptes employés

Le système doit permettre au chef d’équipe de créer, modifier et supprimer des comptes employés.  
**Priorité : Must**

**Critères :**
1. Seul le chef peut gérer les comptes.
2. Email unique obligatoire.
3. Suppression interdite si l’employé possède des shifts actifs.

---

## FR-03 : Tableau de bord de présence

Le système doit afficher au chef d’équipe la liste des employés avec leur statut (présent, absent, en retard).  
**Priorité : Must**

**Critères :**
1. Mise à jour après pointage.
2. Affichage clair du statut.
3. Accès interdit aux employés.

---

## FR-04 : Gestion des shifts

Le système doit permettre au chef d’équipe de créer, modifier et supprimer des shifts.  
**Priorité : Must**

**Critères :**
1. Date et heure obligatoires.
2. Un shift doit être assigné à un employé.
3. Seul le chef peut modifier ou supprimer un shift.

---

## FR-05 : Consultation des shifts

Le système doit permettre à un employé de consulter ses shifts (jour / semaine).  
**Priorité : Must**

**Critères :**
1. Affichage limité aux shifts personnels.
2. Mise à jour automatique après modification.
3. Accès refusé aux shifts d’autres employés.

---

## FR-06 : Pointage (Check-in / Check-out)

Le système doit permettre à un employé de se pointer au début et à la fin d’un shift.  
**Priorité : Must**

**Critères :**
1. Pointage autorisé uniquement si un shift est planifié.
2. Enregistrement de l’heure réelle.
3. Refus si tentative en dehors du shift planifié.

---

## FR-07 : Historique des pointages

Le système doit permettre au chef d’équipe de consulter l’historique des pointages.  
**Priorité : Should**

**Critères :**
1. Filtrage par employé.
2. Affichage date + heure réelle.
3. Consultation en lecture seule.

---

## FR-08 : Chat de groupe

Le système doit permettre aux membres d’une équipe d’échanger via un chat commun.  
**Priorité : Should**

**Critères :**
1. Visible par tous les membres de l’équipe.
2. Historique conservé.
3. Message affiché immédiatement.

---

## FR-09 : Messagerie privée

Le système doit permettre à un utilisateur d’envoyer un message privé à un autre membre.  
**Priorité : Should**

**Critères :**
1. Visible uniquement par les deux participants.
2. Historique conservé.
3. Notification lors d’un nouveau message.

---

# 5. Exigences Non Fonctionnelles (NFR)

---

## NFR-01 (Performance)

Les pages principales doivent charger en ≤ 2 secondes dans des conditions normales.

---

## NFR-02 (Sécurité)

- Authentification obligatoire.
- Les mots de passe doivent être hashés.
- Les permissions doivent être vérifiées côté backend.

---

## NFR-03 (Disponibilité)

Le système doit être accessible 7 jours sur 7 hors maintenance planifiée.

---

## NFR-04 (UX)

Les actions principales (consulter shifts, pointer, envoyer message) doivent être réalisables en ≤ 3 clics.

---

## NFR-05 (Qualité)

Des tests unitaires doivent couvrir :
- Authentification
- Pointage
- Création de shifts

---

## NFR-06 (Compatibilité)

Le système doit fonctionner sur Chrome, Firefox et Edge (versions récentes) en mode desktop et mobile.

---

## NFR-07 (Maintenabilité)

Le code doit respecter une architecture séparant :

- Frontend (Vue.js)
- Backend (Node.js / API REST)

---

# 6. Contraintes

- C-1 : Technologies — JavaScript, Node.js, Vue.js
- C-2 : Plateforme — Web
- C-3 : Délai — Fin de la session hiver 2026
- C-4 : Outils — Git + documentation UML

---

# 7. Données & Règles Métier

## 7.1 Entités principales

- User
- Équipe
- Shift
- Pointage
- Message

## 7.2 Règles métier

- Un utilisateur doit appartenir à une équipe.
- Seul le chef d’équipe peut gérer les shifts.
- Un employé peut se pointer uniquement sur un shift planifié.
- Le pointage enregistre l’heure réelle.
- Les messages privés sont visibles uniquement par les participants.
- Le chat de groupe est visible par tous les membres.

---

# 8. Hypothèses & Dépendances

## 8.1 Hypothèses

- Les utilisateurs disposent d’un compte.
- Les utilisateurs savent utiliser une application web simple.
- Tous les utilisateurs appartiennent à une équipe.

## 8.2 Dépendances

- Base de données pour stockage.
- Backend API pour traitement.
- Mécanisme temps réel pour le chat.

---

# 9. Critères d’acceptation globaux (Definition of Done)

- [ ] Toutes les fonctionnalités du Scope IN sont implémentées.
- [ ] Tests unitaires présents.
- [ ] Gestion minimale des erreurs.
- [ ] Documentation (SRS + ADR + UML) complète et cohérente.
- [ ] Application accessible via navigateur.
