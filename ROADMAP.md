# AppLumpas

- But : application de gestion pour un groupe de carnaval qui construit son char tous les samedis de septembre à janvier et participe à des cavalcades.
- Stack : back-end C# / ASP.NET Core Web API (contrôleurs), tests xUnit ; front-end React + TypeScript avec Vite, tests Vitest + React Testing Library ; base de données PostgreSQL ; conteneurs : Docker + Docker Compose
- Dépôt : https://github.com/Julien68480/AppLumpas (public, licence MIT)

## Objectif de l'application

### Fonctionnalités

- **Saisons** : les données sont organisées par saison, avec un historique consultable d'une année sur l'autre.
- **Membres** : gestion des membres du groupe.
- **Cotisations** : une cotisation unique par saison, même montant pour tous, payée en une seule fois. Suivi de qui a payé ou non.
- **Cavalcades** : liste des cavalcades d'une saison (date, lieu) et planning de présence des membres pour chacune.
- **Invités** :
  - des personnes extérieures au groupe peuvent être invitées sur une cavalcade, par un membre (on sait quel membre a invité qui) ;
  - le groupe prévoit des déguisements supplémentaires pour eux : il faut connaître le nombre de déguisements à prévoir par cavalcade ;
  - prix de participation identique pour toutes les cavalcades : on suit seulement si l'invité a payé ou non, avec un visuel clair.
- **Gilets jaunes** :
  - bénévoles extérieurs qui assurent la sécurité lors d'une cavalcade ;
  - chaque cavalcade de sécurité donne droit à une participation gratuite en tant qu'invité sur une autre cavalcade de son choix (3 sécurités = 3 participations gratuites) ;
  - un gilet jaune invité n'est rattaché à aucun membre et ne paie pas ;
  - l'appli suit les droits acquis et utilisés.
- **Construction du char** : planning des samedis de construction (qui est présent), tâches (à faire / en cours / terminé, assignées à des membres).
- **Inventaire** du matériel et des fournitures.

### Plus tard

- Tailles des déguisements (à discuter avec la couturière).

## Décisions

- 2026-10-15 Nom du projet : AppLumpas
- 2026-10-15 Type d'application : application web - raison : plusieurs utilisateurs, accès par simple lien sur PC ou téléphone, données partagées
- 2026-10-15 Dépôt : supprimer l'ancien dépôt carnaval-app et créer un nouveau dépôt AppLumpas - raison : l'ancien dépôt était vide, départ propre
- 2026-10-15 Langage back-end : C# (.NET) - raison : apprentissage en cours, proche du Java déjà connu, demandé en stage dans la région et en Suisse
- 2026-10-15 Framework back-end : ASP.NET Core Web API avec contrôleurs - raison : structure claire pour une appli riche, séparation serveur / interface, modèle courant en entreprise
- 2026-10-15 Front-end : React avec TypeScript - raison : déjà un peu pratiqué, très demandé en stage, ouvre la voie à React Native pour une future appli mobile
- 2026-10-15 Base de données : PostgreSQL - raison : multi-utilisateurs et prête pour la mise en ligne dès le départ, très demandée en entreprise
- 2026-10-15 Tests back-end : xUnit - raison : standard actuel pour ASP.NET Core, le plus présent dans la documentation et les tutoriels
- 2026-10-15 Outil front-end : Vite (SPA React) - raison : correspond à l'architecture API séparée, simple et rapide, standard actuel
- 2026-10-15 Tests front-end : Vitest + React Testing Library - raison : intégré à Vite sans configuration, même syntaxe que Jest
- 2026-10-15 Langue : noms (classes, méthodes, variables) en anglais ; commentaires et messages de commit en français - raison : norme sur les noms, logique expliquée clairement pendant l'apprentissage
- 2026-10-15 Branches : une branche par étape, format `<type>/XX-<nom>` (ex. `feat/03-liste-membres`), fusionnée dans `main` une fois validée - raison : format professionnel tout en gardant le lien avec les étapes de la ROADMAP
- 2026-10-15 Visibilité du dépôt : public - raison : visible par les recruteurs, montre la progression. Règles : aucun secret (mots de passe, clés) et aucune donnée réelle des membres dans le dépôt
- 2026-10-15 .gitignore : dépôt GitHub créé vide ; `.gitignore` générés par les outils officiels (`dotnet new gitignore` pour .NET, celui de Vite pour React) - raison : fichiers officiels à jour, pas de conflit au premier envoi. À vérifier avant le premier commit : `bin/`, `obj/`, `node_modules/` exclus
- 2026-10-15 Licence : MIT - raison : la plus courante pour un projet vitrine, simple à comprendre
- 2026-10-16 Découpage du plan : socle technique d'abord (« squelette qui marche » front → API → base), puis une fonctionnalité de bout en bout par étape - raison : isoler les difficultés d'installation des trois briques (.NET, Vite, PostgreSQL) avant le métier
- 2026-10-16 Ordre des fonctionnalités : Saisons → Membres → Cotisations → Cavalcades → Planning de présence → Invités → Gilets jaunes → Construction → Inventaire - raison : suivre les dépendances, aucune étape ne remet en cause une précédente
- 2026-10-16 Connexion : comptes individuels avec rôles, plusieurs administrateurs peuvent modifier les données - raison : données personnelles protégées, traçabilité, compétence demandée en stage
- 2026-10-16 Rôles : admins (modifient tout) et membres (consultent, indiquent leurs propres présences aux cavalcades et samedis de construction) - raison : le planning se remplit par chacun, sans dépendre des admins
- 2026-10-16 Responsable des invités : pas de rôle dédié, c'est un admin comme les autres avec une tâche attribuée dans le groupe - raison : deux rôles suffisent (admin, membre), remplacement possible, traçabilité assurée par l'historique
- 2026-10-16 Historique : chaque élément garde « modifié par » et « modifié le », écrasés à chaque changement (pas de journal complet) - raison : répond au besoin de suivi, simple, extensible plus tard aux paiements
- 2026-10-16 Place de la connexion : après Saisons et Membres, avant les autres fonctionnalités - raison : Identity abordé une fois le schéma API + base + écran maîtrisé, lien compte ↔ membre naturel
- 2026-10-16 Plan d'étapes : 37 étapes validées (voir section Étapes) - mise en ligne non planifiée, à décider plus tard
- 2026-10-16 Structure du dépôt : deux dossiers à la racine, backend/ et frontend/, chacun avec son propre .gitignore - raison : lisible, chaque partie autonome avec ses outils et ses tests
- 2026-10-27 Langue du README : français - raison : cohérent avec le reste du dépôt
- 2026-10-29 Docker : tout le projet conteneurisé (API, front, base) avec Docker Compose - raison : déploiement simplifié, base pour une future CI/CD
- 2026-10-29 Introduction de Docker : PostgreSQL via Docker Compose à l'étape 05, puis API + front conteneurisés dans une étape dédiée après le premier aller-retour complet - raison : découvrir Docker sur un cas simple, isoler les difficultés
- 2026-10-29 Usage de Docker : en développement, base dans Docker et API + front lancés depuis l'IDE ; `docker compose up` lance tout le projet comme en production - raison : débogage simple au quotidien, images prêtes pour le déploiement
- 2026-10-29 Emplacement : compose.yaml à la racine du dépôt, un Dockerfile dans backend/ et un dans frontend/ - raison : compose.yaml orchestre tout le projet, chaque partie reste autonome
- 2026-10-29 Plan d'étapes : 38 étapes - ajout de l'étape 07 (conteneurisation), étapes suivantes renumérotées
- 2026-10-29 Version de .NET : .NET 10 - raison : LTS (support jusqu'en novembre 2028), version la plus récente
- 2026-10-29 Structure du back-end : à plat dans backend/ (AppLumpas.slnx, AppLumpas.Api/, AppLumpas.Api.Tests/) - raison : simple et lisible pour deux projets
- 2026-10-29 Premier test : test unitaire du contrôleur - raison : découvrir xUnit simplement ; tests d'intégration plus tard
- 2026-10-29 IDE C# : VS Code + C# Dev Kit - raison : déjà installé

## Étapes

### Socle technique
- [fait] 01 Initialiser le dépôt : README, licence, .gitignore, premier commit
- [en cours] 02 Créer l'API ASP.NET Core avec une route de test, et un premier test xUnit
- [ ] 03 Créer le front Vite + React + TypeScript, une page d'accueil, et un premier test Vitest
- [ ] 04 Faire appeler l'API par le front et afficher la réponse
- [ ] 05 Lancer PostgreSQL avec Docker Compose et y connecter l'API, sans secret dans le dépôt
- [ ] 06 Premier aller-retour complet : une donnée en base, lue par l'API, affichée dans le front
- [ ] 07 Conteneuriser l'API et le front (Dockerfiles) et tout lancer avec Docker Compose

### Saisons
- [ ] 08 Modèle « Saison » et table en base
- [ ] 09 API : lister et créer une saison
- [ ] 10 Écran : liste et création des saisons
- [ ] 11 Modifier, supprimer, et consulter les saisons passées

### Membres
- [ ] 12 Modèle « Membre » et API : lister et créer
- [ ] 13 Écran : liste et ajout des membres
- [ ] 14 Modifier, supprimer, et gérer les saisies invalides

### Connexion et rôles
- [ ] 15 Mettre en place ASP.NET Core Identity et un premier compte admin
- [ ] 16 Connexion et déconnexion côté API
- [ ] 17 Écran de connexion et pages protégées
- [ ] 18 Rôles admin et membre, appliqués aux saisons et aux membres
- [ ] 19 Relier un compte à un membre ; création des comptes membres par un admin
- [ ] 20 « Modifié par / modifié le » sur les saisons et les membres

### Cotisations
- [ ] 21 Montant de la cotisation d'une saison
- [ ] 22 Marquer payé / non payé par membre, avec un visuel clair

### Cavalcades
- [ ] 23 API : cavalcades d'une saison (date, lieu)
- [ ] 24 Écran des cavalcades

### Planning de présence
- [ ] 25 Un membre indique sa présence à une cavalcade
- [ ] 26 Écran du planning par cavalcade

### Invités
- [ ] 27 Un admin inscrit un invité sur une cavalcade, rattaché au membre qui l'invite
- [ ] 28 Paiement de l'invité, avec un visuel clair
- [ ] 29 Nombre de déguisements à prévoir par cavalcade

### Gilets jaunes
- [ ] 30 Inscrire un gilet jaune et ses sécurités sur une cavalcade
- [ ] 31 Calculer ses droits acquis
- [ ] 32 Utiliser un droit : participation gratuite comme invité, droits restants

### Construction du char
- [ ] 33 Samedis de construction de la saison
- [ ] 34 Un membre indique sa présence à un samedi
- [ ] 35 Tâches : créer et assigner à des membres
- [ ] 36 Statut des tâches (à faire / en cours / terminé)

### Inventaire
- [ ] 37 Liste, ajout et quantités du matériel
- [ ] 38 Modifier et supprimer

## Notions vues

Aucune pour l'instant.

## Points à retravailler

Aucun pour l'instant.
