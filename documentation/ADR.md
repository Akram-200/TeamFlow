# Architecture Decision Records ADR-<NN> — <Titre de la décision>
**Statut :** Proposed | Accepted | Rejected | Superseded  
**Date :** <2026-01-25>  
**Décideurs :** <Alaeeddine Moumene , Akram Naamane>  
**Contexte projet :** <TeamFlow / module>

---

## 1. Contexte
- **Problème / besoin :** le systeme doit etre accessible a des employes et chefs d'équipe sur mobile et desktop , avec gestion des utilisateurs, chats prive ou publique, présence et shifts.
- **Contraintes :** Accessibilité web requise , maintenabilité et simplicité , cout et temps limités , outils imposés: SDLC + documentation + UML
- **Forces en présence :** simplicite de deploiement, performance suffisante, séparation du frontend et backend, risque réseau

---

## 2. Décision
> Décrire la décision en 1–3 phrases.
Nous choisissons une architecture web app client serveur REST avec une interface web front end consommant API backend .
> pour séparer l’interface utilisateur de la logique métier, améliorer la maintenabilité et permettre un accès depuis n’importe quel navigateur. 

---

## 3. Alternatives considérées
### Option A — <Applications Mobile Native>
- **Avantages :** <expérience utilisateur optimisée, notifications push native>
- **Inconvénients :** <développemnt et maintenance plus cher, complexité multiplateforme, non necéssaire pour un MVP>

### Option B — <Applications Destkop>
- **Avantages :** performances locales et gestion des fichiers simplifiée
- **Inconvénients :** installation obligatoire , pas adaptées a l'usage mobile, friction côté utilisateurs 

---

## 4. Justification (Pourquoi cette décision ?)
- Compatible avec le besoin des employés (utilisation sur poste partagé).
- Déploiement centralisé.
- Conforme au cours et exigences du SDLC.
- Réduit la charge de maintenance.
- Permet une évolution agile.

---

## 5. Conséquences
### Positives
- Accessibilité multiplateformeé
- Mise à jour instantanée (serveur)
- Séparation claire des responsabilités.
- Adoption facile par les utilisateurs finaux
  

### Négatives / Risques
- Dépendance à la connexion internet
- Sécurisation réseau nécessaire.
- Gestion du temps réel à prévoir. 

### Impact sur l’architecture / le code
- Backend exposera des endpoints REST.
- Frontend récupérera les données via fetch et axios.
- Module chat nécessitera un canal temps réel.

---

## 6. Plan d’implémentation (court)
- [ ] Étape 1 : Définir la structure frontend.
- [ ] Étape 2 : Définir l’API REST backend.
- [ ] Étape 3 : Intégrer et tester les communications client-serveur.

---

## 7. Validation
- **Comment vérifier que c’est bon ?**
  - L’interface web communique correctement avec l’API.
  - L’application fonctionne depuis un navigateur sans installation.
  - Les fonctionnalités (auth, shifts, pointage) sont indépendantes du device.

---

## 8. Liens
- UML : <lien/nom de fichier>
- Issue/Tâche : <lien>
- Référence : <doc officiel / cours>
