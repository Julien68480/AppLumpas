# Lumpa's

Application web de gestion pour le groupe de carnaval **Lumpa's**, qui construit son char tous les samedis de septembre à janvier et participe à des cavalcades.

> 🚧 Projet en cours de développement — réalisé dans le cadre de ma formation à l'UHA 4.0.

## Fonctionnalités prévues

- **Saisons** : toutes les données sont organisées par saison, avec un historique consultable d'une année sur l'autre.
- **Membres** : gestion des membres du groupe.
- **Cotisations** : une cotisation unique par saison, avec le suivi de qui a payé.
- **Cavalcades** : liste des cavalcades d'une saison (date, lieu) et planning de présence des membres.
- **Invités** : personnes extérieures invitées par un membre sur une cavalcade, suivi de leur paiement et du nombre de déguisements à prévoir.
- **Gilets jaunes** : bénévoles qui assurent la sécurité ; chaque cavalcade de sécurité donne droit à une participation gratuite comme invité. L'application suit les droits acquis et utilisés.
- **Construction du char** : planning des samedis de construction et tâches assignées aux membres (à faire / en cours / terminé).
- **Inventaire** : matériel et fournitures du groupe.
- **Comptes et rôles** : connexion individuelle, avec des administrateurs (modifient les données) et des membres (consultent et indiquent leurs propres présences).

## Stack technique

| Partie          | Technologies                                                  |
|-----------------|---------------------------------------------------------------|
| Back-end        | C# / ASP.NET Core Web API (contrôleurs)                       |
| Front-end       | React + TypeScript, avec Vite                                 |
| Base de données | PostgreSQL                                                    |
| Conteneurs      | Docker + Docker Compose                                       |
| Tests           | xUnit (back-end), Vitest + React Testing Library (front-end)  |

## Structure du dépôt

```
AppLumpas/
├── backend/       # API ASP.NET Core, ses tests et son Dockerfile
├── frontend/      # Application React, ses tests et son Dockerfile
└── compose.yaml   # Lance l'API, le front et la base avec Docker Compose
```

## Installation

*Section à compléter.*

### Prérequis

- .NET SDK : *à compléter*
- Node.js : *à compléter*
- Docker (avec Docker Compose) : *à compléter*

### Lancer le projet

*À compléter.*

## Avancement

- [ ] Socle technique (API, front, base de données reliés)
- [ ] Saisons
- [ ] Membres
- [ ] Connexion et rôles
- [ ] Cotisations
- [ ] Cavalcades
- [ ] Planning de présence
- [ ] Invités
- [ ] Gilets jaunes
- [ ] Construction du char
- [ ] Inventaire

## Conventions

- Noms dans le code (classes, méthodes, variables) en anglais ; commentaires et messages de commit en français.
- Messages de commit au format [Conventional Commits](https://www.conventionalcommits.org/fr/) : `feat: ajoute la liste des membres`.
- Une branche par étape, au format `<type>/XX-<nom>` (ex. `feat/03-liste-membres`), fusionnée dans `main` une fois validée.

## Auteur

**Julien Simon** — étudiant en Licence Pro Métiers de l'Informatique à l'UHA 4.0 (Université de Haute-Alsace, Mulhouse).

## Licence

Ce projet est distribué sous licence [MIT](LICENSE).
