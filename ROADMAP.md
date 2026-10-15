# AppLumpas

- But : application de gestion pour un groupe de carnaval qui construit son char tous les samedis de septembre à janvier et participe à des cavalcades.
- Stack : à décider
- Dépôt : (https://github.com/Julien68480/AppLumpas)

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
- 2026-10-15 Messages de commit : Conventional Commits (type en anglais, description en français, ex. `feat: ajoute la liste des membres`) - raison : standard répandu en entreprise, historique lisible
- 2026-10-15 Branches : une branche par étape, format `<type>/XX-<nom>` (ex. `feat/03-liste-membres`), fusionnée dans `main` une fois validée - raison : format professionnel tout en gardant le lien avec les étapes de la ROADMAP
- 2026-10-15 Visibilité du dépôt : public - raison : visible par les recruteurs, montre la progression. Règles : aucun secret (mots de passe, clés) et aucune donnée réelle des membres dans le dépôt
- 2026-10-15 .gitignore : dépôt GitHub créé vide ; `.gitignore` générés par les outils officiels (`dotnet new gitignore` pour .NET, celui de Vite pour React) - raison : fichiers officiels à jour, pas de conflit au premier envoi. À vérifier avant le premier commit : `bin/`, `obj/`, `node_modules/` exclus

## Étapes

À définir ensemble.

## Notions vues

Aucune pour l'instant.

## Points à retravailler

Aucun pour l'instant.
