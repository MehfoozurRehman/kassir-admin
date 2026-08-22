# POS Admin: Cloud Point-of-Sale & Store Management Portal

An administrative store control panel, inventory matrix manager, and cashier terminal orchestration dashboard built with Next.js 15 App Router (Turbopack), React 19, Convex real-time backend, TanStack Table, and Tailwind CSS v4.

## Overview

`pos-admin` centralizes multi-store retail and restaurant operations:
- **Inventory & Orders**: Paginated catalog filtering via TanStack Table v8.
- **Visual Analytics**: Real-time sales metrics and revenue breakdown charts (Recharts v3).
- **Store Layouts**: Drag-and-drop table and department layout management (`@dnd-kit/core`).
- **Real-Time Sync**: Instant order notifications and live stock decrements via Convex.

## Tech Stack

- **Framework**: [Next.js](https://nextjs.org/) (v15 App Router, Turbopack)
- **Backend & Database**: [Convex](https://convex.dev/) (`convex`)
- **Data Grids & Charts**: TanStack Table v8, Recharts v3, Tabler Icons, Lucide Icons
- **Frontend Core**: React 19, TypeScript, Radix UI Primitives, Vaul Drawers
- **Styling**: Tailwind CSS v4 (`@tailwindcss/postcss`)

## Prerequisites

- Node.js (v20 or higher recommended)
- Package manager (`pnpm` recommended)
- Convex deployment instance

## Getting Started

1. **Install dependencies**:
   ```bash
   pnpm install
   ```

2. **Configure Environment Variables**:
   Create a `.env.local` file:
   ```env
   NEXT_PUBLIC_CONVEX_URL="your-convex-deployment-url"
   ```

3. **Start the Convex Backend**:
   ```bash
   npx convex dev
   ```

4. **Run the Development Server**:
   ```bash
   pnpm dev
   ```

5. **Access the Dashboard**:
   Open `http://localhost:3000` in your web browser.

## Available Scripts

- `pnpm dev` - Starts Next.js dev server with Turbopack.
- `pnpm build` - Compiles the dashboard for production.
- `pnpm start` - Starts the production server.
- `pnpm format` - Formats code using Prettier.

## Author

Created by [Mehfooz-ur-Rehman](https://github.com/MehfoozurRehman).
