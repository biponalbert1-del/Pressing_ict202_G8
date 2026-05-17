# Pressing Groupe 8

Application web de gestion de pressing developpee avec React, TypeScript et Vite.

Elle permet a une entreprise de pressing de gerer ses vetements, ses clients, les paiements, les statuts de lavage, la location et l'historique des commandes. Les donnees sont stockees localement dans le navigateur avec IndexedDB.

## Fonctionnalites

- Inscription, connexion et deconnexion des comptes entreprise ou client
- Tableau de bord avec statistiques: total, vetements laves, non laves, retards, valeur pressing et vetements disponibles a la location
- Ajout, modification et suppression de vetements
- Gestion des informations client: nom, telephone, prix, date de retrait et notes
- Ajout d'image pour chaque vetement
- Statuts de vetement: propre, sale, en lavage, loue, retouche
- Gestion des paiements: paye ou non paye
- Vue des commandes avec paiements en attente et retards
- Separation automatique des vetements laves et non laves
- Recherche et filtres par statut
- Historique des actions sur chaque vetement
- Minuteur de lavage avec passage automatique au statut propre
- Notifications visuelles et sonores
- Parametres: langue, theme clair/sombre, logo, informations de l'application
- Import et export des donnees au format JSON
- Donnees de demonstration pour tester rapidement l'application

## Structure du projet

```text
Pressing_ict202_G08/
|-- src/
|   |-- App.tsx        # Composant principal et logique de l'application
|   |-- db.ts          # Acces a IndexedDB: lecture/ecriture des donnees
|   |-- i18n.ts        # Textes de l'interface en francais et en anglais
|   |-- main.tsx       # Point d'entree React
|   |-- styles.css     # Styles de l'application
|   `-- types.ts       # Types TypeScript utilises dans le projet
|-- image3.avif        # Image utilisee dans l'interface
|-- logo.jpg           # Logo par defaut
|-- index.html         # Page HTML chargee par Vite
|-- package.json       # Dependances et scripts npm
|-- package-lock.json  # Versions exactes des dependances installees
|-- tsconfig.json      # Configuration TypeScript
|-- vite.config.ts     # Configuration Vite
`-- README.md          # Documentation du projet
```

## Fonctionnement

Au lancement, l'application charge les parametres, les comptes et les vetements depuis IndexedDB. Si aucun compte n'est connecte, l'utilisateur peut creer un compte ou se connecter.

Un compte entreprise peut ajouter et gerer les vetements du pressing. Chaque vetement contient ses informations principales, son client, son prix pressing, son prix de location, son statut, son etat de paiement, sa date de retrait, une image et un historique.

Un compte client ne voit que les commandes liees a son nom ou a son numero de telephone. Cette vue permet de consulter les commandes autorisees sans acceder aux actions de gestion.

Les vetements sont affiches dans deux colonnes principales: les vetements laves et les vetements non laves. Les filtres, la recherche et la vue des commandes permettent de retrouver rapidement une commande. Quand un vetement passe en lavage, le panneau de temps suit la duree ecoulee et peut le marquer automatiquement comme propre apres le delai configure.

Toutes les donnees restent dans le navigateur de l'utilisateur. L'export JSON permet de sauvegarder les donnees, et l'import JSON permet de les restaurer.

## Prerequis

- Node.js
- npm

## Installation

Dans le dossier du projet, installer les dependances:

```bash
npm install
```

## Demarrer en developpement

Lancer le serveur Vite:

```bash
npm run dev
```

Vite affiche ensuite une adresse locale, generalement:

```text
http://localhost:5173/
```

Ouvrir cette adresse dans le navigateur pour utiliser l'application.

## Generer la version de production

```bash
npm run build
```

La version compilee est generee dans le dossier `dist/`.

## Previsualiser la version de production

Apres un build, lancer:

```bash
npm run preview
```

## Scripts disponibles

- `npm run dev`: demarre l'application en mode developpement
- `npm run build`: compile TypeScript et genere la version de production
- `npm run preview`: previsualise la version de production

## Stockage des donnees

L'application utilise IndexedDB avec trois espaces de stockage:

- `businesses`: comptes entreprise et client
- `garments`: vetements et commandes
- `settings`: langue, theme, logo et compte actif

Les donnees sont donc locales au navigateur. Si le cache ou les donnees du site sont supprimes, les informations peuvent etre perdues sauf si elles ont ete exportees avant.
