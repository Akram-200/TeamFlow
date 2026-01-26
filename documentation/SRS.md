# Cahier des charges (SRS léger) — TeamFlow
**Équipe :** Akram Naamane, Alaeeddine Moumene
**Date :** 2026-01-19 
**Version :** <v0.1 / v1.0>

---

## 1. Contexte & objectif
- **Contexte :** Ce projet existe pour régler tout les obstacles qu’une équipe peut avoir
- **Objectif principal :** Faciliter et centrer tout ce qu’une équipe a besoin pour fonctionner efficacement
- **Parties prenantes :** Chef d’équipe, Emploiyer

---

## 2. Portée (Scope)
### 2.1 Inclus (IN)
- IN-1 : Authentification + rôle
- IN-2 : Dashboard de présence
- IN-3 : Creation et affichage des Shifts aux employeurs
- IN-4 : Permettre le Pointage

### 2.2 Exclu (OUT)
- OUT-1 : Gestion d’appel
- OUT-2 : Messagerie avancé
- OUT-3 : Sécurité

---

## 3. Acteurs / profils utilisateurs
- **Acteur A : Chef d’équipe
  Rôle :
    Configure l’application (création d’équipe, ajout des employés, définition des rôles).
    Planifie et publie les shifts / horaires.
    Consulte et valide les pointages (présence, retard, absence).
    
  Besoins :
    Voir rapidement qui est présent / absent en temps réel.
    Créer, modifier et supprimer des shifts.
    Attribuer des shifts aux employés.
    Peut envoyer des messages privés aux employés.
    Peut envoyer des messages dans le canal de discussion d’équipe (chat de groupe)
    
  Contraintes :
    Peu de temps pour gérer l’outil, donc interface simple et rapide.
    Doit pouvoir utiliser le système depuis un navigateur web (desktop ou mobile).
  
- **Acteur B : Employé
  Rôle :
    Consulte ses horaires.
    Se pointe à l’arrivée et au départ.
  
  Besoins :
    Accéder facilement à son compte (login simple).
    Voir ses shifts à venir (jour / semaine).
    Se pointer en quelques clics au début et à la fin du shift.
    Peut envoyer des messages privés au chef d’équipe ou à un autre membre.
    Peut envoyer des messages dans le groupe.
    Peut consulter et participer au chat de groupe de l’équipe.
  
  Contraintes :
    Peut utiliser un téléphone ou un poste partagé au travail.
    Ne doit pas avoir accès aux données des autres employés.

---

## 4. Exigences fonctionnelles (FR)
- FR-1 : Le système doit permettre l’authentification des utilisateurs et l’attribution d’un rôle (chef d’équipe ou employé).
- FR-2 : Le système doit permettre au chef d’équipe de créer, modifier et supprimer des comptes employés.
- FR-3 : Le système doit afficher un tableau de bord permettant au chef d’équipe de consulter la présence des employés en temps réel.
- FR-4 : Le système doit permettre au chef d’équipe de créer, modifier et supprimer des shifts (date, heure, employé assigné).
- FR-5 : Le système doit permettre à chaque employé de consulter ses shifts.
- FR-6 : Le système doit permettre à l’utilisateur de se pointer (check-in) au début du shift et de se dépointer (check-out) à la fin du shift.
- FR-7 : Le système doit enregistrer l’heure réelle de pointage afin d’identifier retards, absences ou écarts.
- FR-8 : Le système doit permettre au chef d’équipe de consulter l’historique des pointages.
- FR-9 : Le système doit fournir un chat de groupe accessible à tous les membres de l’équipe.
- FR-10 : Le système doit permettre à un utilisateur de sélectionner un autre membre et d’envoyer un message privé.
- FR-11 : Le système doit afficher l’historique du chat de groupe.
- FR-12 : Le système doit afficher l’historique des conversations privées (uniquement pour les deux participants).
- FR-13 : Le système doit gérer les permissions de visibilité :
  • le chat de groupe est visible par tous les membres
  • une conversation privée est visible uniquement par ses deux participants
- FR-14 : Le système doit notifier l’utilisateur lorsqu’il reçoit un nouveau message (groupe ou privé).

---

## 5. Exigences non fonctionnelles (NFR)
> Performance / sécurité / disponibilité / UX / maintenabilité…
- **NFR-1 (Performance) :Le système doit afficher les données principales (dashboard, shifts, chat) avec un temps de réponse inférieur à 2 secondes dans des conditions normales.
- **NFR-2 (Sécurité) : Le système doit exiger une authentification avant d’accéder aux fonctionnalités internes.
- **NFR-3 (UX) :** <ex. parcours en ≤ 3 clics>
- **NFR-4 (Qualité) :** <ex. couverture minimale de tests>

---

## 6. Contraintes
- **C-1 (Technologie) :** <langage / framework imposé>
- **C-2 (Plateforme) :** <web / mobile / desktop>
- **C-3 (Délai) :** <dates de phases>
- **C-4 (Outils) :** <Git, CI, etc.>

---

## 7. Données & règles métier (si applicable)
- **Entités principales :** <User, Order, ...>
- **Règles métier :** <validation, calculs, permissions, etc.>

---

## 8. Hypothèses & dépendances
### 8.1 Hypothèses
- H-1 : <ex. utilisateurs ont un compte>
- H-2 : <...>

### 8.2 Dépendances
- D-1 : <API externe / BD / service>
- D-2 : <...>

---

## 9. Critères d’acceptation globaux (Definition of Done – mini)
- [ ] Fonctionnalités livrées et testées
- [ ] Tests unitaires présents
- [ ] Gestion d’erreurs minimale
- [ ] Documentation à jour (UML + ADR si requis)
