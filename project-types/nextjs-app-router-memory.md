---
id: mem.nextjs-app-router
type: memory
title: Next.js 14+ App Router Project Memory
tags: [nextjs, react, frontend, app-router, typescript]
summary: Complete context for Next.js 14+ projects using App Router with React Server Components, TypeScript, and modern patterns.
audience: team
domain: frontend
version: 1
---

# Next.js 14+ App Router Project Memory

## Project Overview

This is a **Next.js 14+ project using the App Router** architecture. All new features use the App Router paradigm with React Server Components as the default.

## Tech Stack

### Core Framework
- **Next.js 14+** (App Router)
- **React 18+** (Server Components)
- **TypeScript** (Strict mode enabled)

### Styling
- **Tailwind CSS** (Utility-first)
- **CSS Modules** (Component-scoped styles)

### Data Fetching
- **Server Components** (Primary data fetching)
- **Server Actions** (Form submissions, mutations)
- **React Query/SWR** (Client-side data when needed)

### State Management
- **React Context** (Client-side state)
- **URL State** (Search params, route state)
- **Server State** (Database, APIs)

### Database & ORM
- **Prisma** (Type-safe ORM)
- **PostgreSQL** (Primary database)

### Authentication
- **NextAuth.js v5** (Auth.js)
- **JWT** tokens
- **Session** management

## Project Structure

```
/app                    - Next.js App Router directory
  /api                  - API routes
  /(routes)             - Route groups
  layout.tsx            - Root layout
  page.tsx              - Home page
  loading.tsx           - Loading states
  error.tsx             - Error boundaries

/components             - React components
  /ui                   - Reusable UI components
  /forms                - Form components
  /layouts              - Layout components

/lib                    - Utility functions
  /actions              - Server Actions
  /utils                - Helper functions
  /hooks                - Custom React hooks
  /api                  - API clients

/prisma                 - Database
  schema.prisma         - Database schema
  /migrations           - Migration files

/public                 - Static assets
  /images               - Image files
  /fonts                - Font files

/types                  - TypeScript types
  index.ts              - Shared types
```

## File Naming Conventions

### Components
- **PascalCase** for components: `UserProfile.tsx`
- **camelCase** for utilities: `formatDate.ts`
- **kebab-case** for routes: `user-profile/page.tsx`

### Special Files
- `page.tsx` - Route pages
- `layout.tsx` - Layouts
- `loading.tsx` - Loading UI
- `error.tsx` - Error boundaries
- `not-found.tsx` - 404 pages
- `route.ts` - API routes
- `template.tsx` - Templates

## Coding Conventions

### Server vs. Client Components

**Default to Server Components:**
```tsx
// No 'use client' directive = Server Component
export default function ProductList() {
  // Can directly fetch data, access database
  const products = await prisma.product.findMany();
  return <div>{/* render */}</div>;
}
```

**Use Client Components when you need:**
- Event handlers (onClick, onChange)
- React hooks (useState, useEffect)
- Browser APIs
- Third-party libraries requiring client

```tsx
'use client';

import { useState } from 'react';

export default function SearchBar() {
  const [query, setQuery] = useState('');
  return <input value={query} onChange={(e) => setQuery(e.target.value)} />;
}
```

### Data Fetching Patterns

**Server Components (Preferred):**
```tsx
// Direct database access
async function getData() {
  const data = await prisma.user.findMany();
  return data;
}

export default async function Page() {
  const data = await getData();
  return <div>{/* render */}</div>;
}
```

**Server Actions (Mutations):**
```tsx
'use server';

export async function createUser(formData: FormData) {
  const name = formData.get('name') as string;
  const user = await prisma.user.create({
    data: { name }
  });
  revalidatePath('/users');
  return user;
}
```

**Client-side (When necessary):**
```tsx
'use client';

import useSWR from 'swr';

export default function ClientData() {
  const { data } = useSWR('/api/users', fetcher);
  return <div>{/* render */}</div>;
}
```

### TypeScript Patterns

**Props Interfaces:**
```tsx
interface ButtonProps {
  label: string;
  onClick: () => void;
  variant?: 'primary' | 'secondary';
  disabled?: boolean;
}

export default function Button({ label, onClick, variant = 'primary', disabled }: ButtonProps) {
  return <button onClick={onClick} disabled={disabled}>{label}</button>;
}
```

**Async Component Types:**
```tsx
interface PageProps {
  params: { id: string };
  searchParams: { [key: string]: string | string[] | undefined };
}

export default async function Page({ params, searchParams }: PageProps) {
  // ...
}
```

### Routing Conventions

**File-based Routing:**
```
/app/blog/page.tsx              → /blog
/app/blog/[slug]/page.tsx       → /blog/:slug
/app/shop/[...slug]/page.tsx    → /shop/* (catch-all)
/app/dashboard/(admin)/page.tsx → /dashboard (route group)
```

**Dynamic Routes:**
```tsx
// app/blog/[slug]/page.tsx
export default async function BlogPost({ params }: { params: { slug: string } }) {
  const post = await getPost(params.slug);
  return <article>{post.content}</article>;
}
```

**Programmatic Navigation:**
```tsx
'use client';

import { useRouter } from 'next/navigation';

export default function LoginButton() {
  const router = useRouter();
  return <button onClick={() => router.push('/login')}>Login</button>;
}
```

### API Routes

**Route Handlers:**
```tsx
// app/api/users/route.ts
import { NextRequest, NextResponse } from 'next/server';

export async function GET(request: NextRequest) {
  const users = await prisma.user.findMany();
  return NextResponse.json(users);
}

export async function POST(request: NextRequest) {
  const body = await request.json();
  const user = await prisma.user.create({ data: body });
  return NextResponse.json(user, { status: 201 });
}
```

**Dynamic API Routes:**
```tsx
// app/api/users/[id]/route.ts
export async function GET(
  request: NextRequest,
  { params }: { params: { id: string } }
) {
  const user = await prisma.user.findUnique({
    where: { id: params.id }
  });
  return NextResponse.json(user);
}
```

## Environment Variables

### File Structure
```
.env.local          - Local development (gitignored)
.env.production     - Production (never commit)
.env.example        - Template (committed)
```

### Naming Convention
```
NEXT_PUBLIC_*       - Exposed to browser
DATABASE_URL        - Server-only
API_KEY             - Server-only
```

### Usage
```tsx
// Client
const publicKey = process.env.NEXT_PUBLIC_API_KEY;

// Server
const secretKey = process.env.API_SECRET_KEY;
```

## Image Optimization

**Always use next/image:**
```tsx
import Image from 'next/image';

export default function Avatar() {
  return (
    <Image
      src="/avatar.jpg"
      alt="User avatar"
      width={200}
      height={200}
      priority={false}
    />
  );
}
```

## Metadata & SEO

**Static Metadata:**
```tsx
import { Metadata } from 'next';

export const metadata: Metadata = {
  title: 'Page Title',
  description: 'Page description',
  openGraph: {
    title: 'Page Title',
    description: 'Page description',
    images: ['/og-image.jpg'],
  },
};
```

**Dynamic Metadata:**
```tsx
export async function generateMetadata({ params }: PageProps): Promise<Metadata> {
  const post = await getPost(params.slug);
  return {
    title: post.title,
    description: post.excerpt,
  };
}
```

## Error Handling

**Error Boundaries:**
```tsx
// app/error.tsx
'use client';

export default function Error({
  error,
  reset,
}: {
  error: Error & { digest?: string };
  reset: () => void;
}) {
  return (
    <div>
      <h2>Something went wrong!</h2>
      <button onClick={() => reset()}>Try again</button>
    </div>
  );
}
```

**Not Found:**
```tsx
// app/not-found.tsx
export default function NotFound() {
  return <div>404 - Page not found</div>;
}
```

## Performance Optimization

### Loading States
```tsx
// app/dashboard/loading.tsx
export default function Loading() {
  return <div>Loading...</div>;
}
```

### Streaming with Suspense
```tsx
import { Suspense } from 'react';

export default function Page() {
  return (
    <div>
      <Suspense fallback={<Loading />}>
        <SlowComponent />
      </Suspense>
    </div>
  );
}
```

### Static vs. Dynamic Rendering
```tsx
// Force static
export const dynamic = 'force-static';

// Force dynamic
export const dynamic = 'force-dynamic';

// Revalidate every 60 seconds
export const revalidate = 60;
```

## Testing Approach

### Unit Tests
- **Jest** for logic
- **React Testing Library** for components
- Test Server Actions separately

### E2E Tests
- **Playwright** for end-to-end tests
- Test critical user journeys

### File Naming
```
ComponentName.test.tsx
utils.test.ts
```

## Deployment Checklist

- [ ] Environment variables configured
- [ ] Database migrations run
- [ ] Build completes without errors
- [ ] All tests passing
- [ ] Bundle size checked
- [ ] Lighthouse score > 90
- [ ] SEO metadata complete

## Commands

```bash
# Development
npm run dev

# Build
npm run build

# Production
npm start

# Lint
npm run lint

# Type check
npm run type-check

# Database
npx prisma generate
npx prisma migrate dev
npx prisma studio
```

## Common Patterns to Follow

### 1. Prefer Server Components
Default to Server Components, only use 'use client' when necessary

### 2. Use Server Actions for Mutations
Instead of API routes for POST/PUT/DELETE, use Server Actions

### 3. Colocate Related Code
Keep components, types, and utilities close to where they're used

### 4. Type Everything
Use TypeScript strict mode, no `any` types

### 5. Optimize Images
Always use next/image, never <img>

### 6. Handle Loading States
Provide loading.tsx for every route with data fetching

### 7. Implement Error Boundaries
Add error.tsx at route level

### 8. Use Route Groups
Organize routes with parentheses: (marketing), (app), (admin)

## Important Notes

- **Server Components are async** - can await data directly
- **Client Components cannot be async** - use useEffect/SWR
- **This is production code** - write for scale, maintainability, and team collaboration
- **We move fast** - but with clean code and good practices
- **Test thoroughly** - especially data fetching and error states

---

## 🔗 Related Arsenal Items

### Recommended Pairings

**⚙️ Development Rule:**
- [Next.js App Router Rule](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/by-framework/nextjs-app-router.md) - Windsurf behavior rules for Next.js development

**🔄 Workflows:**
- [Code Review Assistant](https://github.com/ChrisTansey007/ai-workflows-arsenal/blob/main/windsurf/development/code-review-assistant.md) - AI-powered code review
- [Run Tests and Fix](https://github.com/ChrisTansey007/ai-workflows-arsenal/blob/main/windsurf/development/run-tests-and-fix.md) - Automated testing workflow
- [Commit and PR](https://github.com/ChrisTansey007/ai-workflows-arsenal/blob/main/windsurf/git-workflows/commit-and-pr.md) - Git workflow automation

**📝 Team Standards:**
- [Code Review Standards Memory](../team-workflows/code-review-standards-memory.md) - Team code review process

**🔗 Complete Examples:**
- [Full-Stack Next.js App](https://github.com/ChrisTansey007/arsenal-integration-hub/tree/main/examples/fullstack-nextjs-app) - Complete setup example
- [Solo Developer Setup](https://github.com/ChrisTansey007/arsenal-integration-hub/tree/main/examples/solo-developer) - Solo dev configuration

### Quick Setup

```bash
# Install all Arsenal repos
curl -sSL https://raw.githubusercontent.com/ChrisTansey007/arsenal-integration-hub/main/scripts/install-all.sh | bash

# Copy this memory + matching rule + workflows
cp ~/arsenals/windsurf-memories-arsenal/project-types/nextjs-app-router-memory.md .windsurf/memories/
cp ~/arsenals/ai-rules-arsenal/windsurf/by-framework/nextjs-app-router.md .windsurf/rules/
cp ~/arsenals/ai-workflows-arsenal/windsurf/development/*.md .windsurf/workflows/
```

## Links & Resources

- [Next.js App Router Docs](https://nextjs.org/docs/app)
- [Server Components](https://nextjs.org/docs/app/building-your-application/rendering/server-components)
- [Server Actions](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions-and-mutations)
- [Routing](https://nextjs.org/docs/app/building-your-application/routing)
