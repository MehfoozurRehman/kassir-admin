# Kassir Admin

An admin dashboard for multi-shop retail, built with Next.js and Convex. It covers shops, payments and sales analytics, behind a cookie-based sign-in.

## The problem

A retailer with several shops needs one place to see each shop's details, its payments and how sales are trending. This app is the admin side of that: sign in, browse shops and payments, and compare activity across shops.

## What it does

- **Sign-in.** A login form calls the `loginAdmin` Convex mutation. The dashboard layout reads a session cookie and validates it with `validateUser` before rendering any page, and redirects if the check fails.
- **Shops** (`/dashboard/shops`). A table of shops, with a detail page for each (`/dashboard/shops/[id]`) that lists that shop's payments.
- **Payments** (`/dashboard/payments`). A full list of payments, loaded from Convex.
- **Analytics** (`/dashboard/analytics`). Payment counts per shop, loaded from Convex. The dashboard home (`/dashboard`) shows an interactive area chart built with Recharts.
- **Data tables.** A reusable table with pagination at 10 rows per page, column filtering and drag-to-reorder rows, built on TanStack Table and dnd-kit.
- **Themes.** Light and dark mode through a theme provider.

## How it's built

- **Framework.** Next.js 15.5 App Router with Turbopack and React 19. Server components load data with `fetchQuery` and `fetchMutation` from `convex/nextjs`. Client components use `useMutation` from `convex/react`, for example on the login form.
- **Backend.** Convex, with a schema covering users, shops, payments, products, inventory and orders. `createAdmin` hashes passwords before storing them.
- **UI.** Tailwind CSS v4, Radix UI primitives and shadcn-style components (see `components.json`), with Lucide and Tabler icons.

Two decisions stand out:

1. **Server-side access checks.** The dashboard layout reads the session cookie on the server and validates it before rendering, so protected pages do not depend on client-side checks.
2. **Shared table component.** One data-table component is used across lists, so pagination, filtering and sorting behave the same everywhere.

## Running it locally

```bash
pnpm install
```

Create `.env.local`:

```env
NEXT_PUBLIC_CONVEX_URL="your-convex-deployment-url"
```

Then run:

```bash
npx convex dev    # Convex backend
pnpm dev          # runs api.js, then next dev --turbopack
```

Open `http://localhost:3000`. Other scripts: `pnpm build`, `pnpm start`, `pnpm lint`, `pnpm format`.

## What I learned / what I'd do next

- `api.js` is a minified, obfuscated script that runs before `dev`, `build` and `start`. It should be reviewed, and removed if it is not needed.
- The dashboard home page (`/dashboard`) renders its chart and table from a bundled `app/dashboard/data.json` file, not from Convex. The shops and payments pages do use Convex. Either connect the home page to live data or remove the sample file.
- There are no automated tests.
- The `create-admin` route and the `createAdmin` mutation do not check for an existing signed-in admin. Access control should be added before any deployment.
- Connecting the analytics page to more than payment counts (for example revenue by day) would make it more useful.
