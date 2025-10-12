# ShopJS v2 - Frontend

Interface e-commerce moderne construite avec Next.js 15, TypeScript et Tailwind CSS.

## Fonctionnalités

### **Pages & Routes**

- **`/`** - Page d'accueil avec présentation de la boutique
- **`/products`** - Liste des produits avec recherche & contrôles panier
- **`/products/[id]`** - Détails du produit avec gestion des quantités
- **`/cart`** - Panier d'achat avec gestion des articles
- **`/payment`** - Commande sécurisée (utilisateurs authentifiés uniquement)
- **`/users/login`** - Authentification utilisateur
- **`/users/signup`** - Inscription utilisateur
- **`/admin`** - Tableau de bord admin pour la gestion des commandes (admins uniquement)

### **Stack Technique**

- **Framework :** Next.js 15 avec App Router
- **Langage :** TypeScript
- **Styles :** Tailwind CSS + composants Shadcn/ui
- **Gestion d'état :** React Context + useReducer
- **Formulaires :** useActionState pour la gestion moderne des formulaires
- **Validation :** Schémas Zod pour la validation runtime
- **Cache :** Fetch natif Next.js avec revalidation personnalisée

### **Fonctionnalités Clés**

- **Panier côté client** avec persistance localStorage
- **Recherche temps réel** avec filtrage instantané
- **Design responsive** (mobile & desktop)
- **Authentification & autorisation** avec accès basé sur les rôles
- **Gestion intelligente du cache** (3min général, 1min admin)
- **Gestion d'erreurs** avec messages conviviaux
- **Optimisation d'images** avec le composant Next.js Image

## Installation & Configuration

### Prérequis

- Node.js 18+
- npm ou yarn
- API Backend en cours d'exécution (voir Shopjsv2-Backend)

### 1. Cloner & Installer

```bash
git clone https://github.com/antancelin/shopjsv2-frontend.git
cd Shopjsv2-Frontend
npm install
```

### 2. Variables d'Environnement

Créer le fichier `.env.local` :

```env
# Configuration API
NEXT_PUBLIC_API_URL=https://votre-backend-api-url.com

# Développement (optionnel)
NODE_ENV=development
```

### 3. Lancer le Serveur de Développement

```bash
npm run dev
```

Ouvrir [http://localhost:3000](http://localhost:3000)

## Scripts

```bash
npm run dev       # Démarrer le serveur de développement avec Turbopack
npm run build     # Build pour la production
npm run start     # Démarrer le serveur de production
npm run lint      # Exécuter ESLint
```

## Structure du Projet

```
src/
├── app/                   # Next.js 15 App Router
│   ├── (routes)/          # Pages de l'application
│   ├── api/               # Routes API
│   └── layout.tsx         # Layout racine
├── components/            # Composants réutilisables
│   ├── ui/                # Composants de base Shadcn/ui
│   ├── auth/              # Composants d'authentification
│   ├── cart/              # Composants panier
│   ├── product/           # Composants produit
│   ├── payment/           # Composants paiement
│   ├── admin/             # Composants admin
│   └── layout/            # Composants de layout
├── context/               # Providers React Context
│   ├── auth-context.tsx   # État d'authentification
│   └── cart-context.tsx   # État du panier
├── lib/                   # Utilitaires & clients API
│   └── api/               # Couche API avec cache
├── schemas/               # Schémas de validation Zod
└── types/                 # Définitions de types TypeScript
```

## Authentification & Sécurité

### Rôles Utilisateur

- **Utilisateurs Normaux :** Peuvent naviguer, ajouter au panier et passer des commandes
- **Utilisateurs Admin :** Accès supplémentaire au tableau de bord de gestion des commandes

### Routes Protégées

- `/payment` - Nécessite une authentification
- `/admin` - Nécessite des privilèges admin

### Fonctionnalités de Sécurité

- Validation de formulaires avec schémas Zod
- Routes API protégées
- Contrôle d'accès basé sur les rôles
- Gestion d'état d'authentification côté client

## Gestion du Panier

- **État côté client** avec React Context + useReducer
- **Stockage persistant** avec localStorage
- **Mises à jour temps réel** dans tous les composants
- **Contrôles de quantité** avec validation
- **Calculs de prix** avec support des remises

## Performance & Cache

### Stratégie de Cache Next.js

- **Requêtes générales :** Cache de 3 minutes
- **Requêtes admin :** Cache de 1 minute
- **Actions dynamiques :** Pas de cache (POST/PUT)

### Optimisations

- Optimisation d'images avec Next.js Image
- Splitting du code des composants
- Déduplication des requêtes fetch
- Génération de pages statiques quand possible

## UI/UX

- **Système de Design :** Composants Shadcn/ui
- **Design Responsive :** Approche mobile-first
- **Accessibilité :** Labels ARIA et navigation clavier
- **États de Chargement :** Écrans squelettes et spinners
- **Gestion d'Erreurs :** Messages d'erreur conviviaux

## Intégration API

Se connecte à l'API Shopjsv2-Backend avec les endpoints :

- `GET /products` - Catalogue de produits
- `GET /products/:id` - Détails du produit
- `POST /user/signup` - Inscription utilisateur
- `POST /user/login` - Authentification utilisateur
- `POST /orders` - Créer une nouvelle commande
- `GET /orders` - Gestion des commandes admin
- `PUT /orders/:id` - Mettre à jour le statut de la commande

## Déploiement

### Vercel (Recommandé)

1. Connecter votre dépôt GitHub à Vercel
2. Ajouter la variable d'environnement :
   - `NEXT_PUBLIC_API_URL` : URL de votre API backend
3. Déploiement automatique à chaque push

### Autres Plateformes

Compatible avec toute plateforme supportant Next.js :

- Netlify
- AWS Amplify
- Railway
- DigitalOcean App Platform

## Projets Associés

- **[Shopjsv2-Backend](https://github.com/antancelin/shopjsv2-backend)** - Serveur API Express.js

---

**Construit utilisant Next.js 15, TypeScript et les patterns React modernes.**
