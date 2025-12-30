# ShopJS v2 Frontend

Modern e-commerce frontend built with Next.js (App Router), TypeScript, and Tailwind CSS.

Live demo: [shopjsv2-frontend.vercel.app](https://shopjsv2-frontend.vercel.app)

## Features

- Product listing with search
- Product details page with quantity controls
- Client-side cart with localStorage persistence
- Authentication (signup/login)
- Checkout flow (authenticated users only)
- Admin dashboard (admin users only)

## Tech stack

- Next.js 15 (App Router)
- React 19, TypeScript
- Tailwind CSS + shadcn/ui components
- Zod schemas for runtime validation
- React Context + reducers for state management

## Pages

- `/` home
- `/products` products list
- `/products/[id]` product details
- `/cart` cart
- `/payment` checkout (protected)
- `/users/login` login
- `/users/signup` signup
- `/admin` admin dashboard (protected)

## Requirements

- Node.js 18+
- npm or yarn
- The backend API running (see the backend repository)

## Getting started (local)

Install dependencies:

```bash
npm install
```

Create `.env.local`:

```dotenv
NEXT_PUBLIC_API_URL=http://localhost:4000
```

Notes:

- `NEXT_PUBLIC_API_URL` is exposed to the browser by design (public env var).
- Prefer a base URL without a trailing slash (for example `http://localhost:4000`).

Start the dev server:

```bash
npm run dev
```

Open `http://localhost:3000`.

## Scripts

```bash
npm run dev
npm run build
npm run start
npm run lint
```

## Project structure

```
src/
  app/            # Next.js App Router routes
  components/     # UI components
  context/        # Auth and cart providers
  lib/api/        # Typed API client helpers
  schemas/        # Zod schemas
  types/          # TypeScript types
```

## Authentication and authorization

- The backend issues a token on signup/login.
- The frontend stores the authenticated user in localStorage.
- Protected pages:
  - `/payment` requires an authenticated user
  - `/admin` requires an authenticated admin user

Admin data fetching:

- The admin dashboard calls the internal Next route `GET /api/admin/orders`.
- Authentication is passed through the `Authorization: Bearer <token>` header.

## API integration

This frontend talks to the backend API endpoints:

- `GET /products` (with optional `?search=term`)
- `GET /products/:id`
- `POST /user/signup`
- `POST /user/login`
- `POST /orders` (authenticated)
- `GET /orders` (admin only)
- `PUT /orders/mark-delivered/:id` (admin only)

## Deployment (Vercel)

Set the environment variable:

- `NEXT_PUBLIC_API_URL` = your backend API base URL

## Related project

- Backend repository: [shopjsv2-backend](https://github.com/antancelin/shopjsv2-backend)
