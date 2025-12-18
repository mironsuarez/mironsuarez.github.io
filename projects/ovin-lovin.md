---
layout: project
type: project
image: img/framework.jpg
title: "Ovin Lovin"
date: 2024-12-01
published: true
labels:
  - Next.js
  - Prisma
  - PostgreSQL
  - UX Design
summary: "A role-based cooking platform that helps students discover budget-friendly recipes, links them to local vendors, and gives admins tools to curate the community."
---

<img class="img-fluid" src="../img/framework.jpg" alt="Screenshot from the Ovin Lovin portal">

Club Ovin Lovin’ is a web platform my team designed for students who need affordable, realistic meal ideas. The app connects three communities—students, local food vendors, and site admins—so recipes always list cost-conscious ingredients, where to buy them near campus, and dietary context. We document the project publicly at <a href="https://club-oven-lovin.github.io/">club-oven-lovin.github.io</a>, ship releases through Vercel, and keep quality signals visible with GitHub Actions CI badges.

### What the app delivers

- **Student experience:** Personalized dashboards highlight budget-friendly meals, onboarding guidance, and buttons to browse, search, or add recipes. Each recipe tracks prep time, servings, ingredient lists, and dietary badges and accepts reviews plus star ratings.
- **Vendor workspace:** Store owners manage their location, hours, and per-item pricing, then attach those ingredients to recipes so students can plan exactly where to shop and how much it will cost.
- **Admin tooling:** Admins review submissions, promote users into vendor roles, and prune inaccurate content with full visibility into accounts, ingredients, and recipe queues.
- **Discovery superpowers:** Search and filtering blend name, tags, ingredients, and dietary restrictions, making it easy to jump from “I only have tofu + pasta” to a handful of realistic options.

### Technical highlights

- Built with Next.js 14 (App Router) and a shared component system so the landing page, dashboards, and forms stay consistent on phones, tablets, and lab projectors.
- Role-based access uses NextAuth, giving us distinct student, vendor, and admin flows while keeping session handling centralized.
- Prisma models a PostgreSQL database that stores recipes, ingredients, vendor inventories, dietary flags, and review metadata. Seed scripts keep demo data fresh for usability tests.
- CI/CD uses GitHub Actions to lint, test, and deploy to Vercel on every pull request, so the status badge on the landing page reflects our production readiness.

```ts
// app/(services)/recipes/search.ts
import { prisma } from '@/lib/prisma';

export async function searchRecipes({
  query = '',
  tags = [],
  dietary = [],
}: {
  query?: string;
  tags?: string[];
  dietary?: string[];
}) {
  return prisma.recipe.findMany({
    where: {
      name: { contains: query, mode: 'insensitive' },
      tags: { hasEvery: tags },
      dietaryFlags: { hasEvery: dietary },
    },
    include: {
      ingredients: {
        include: { vendorMatches: true },
      },
      reviews: true,
    },
    orderBy: { updatedAt: 'desc' },
  });
}
```

This service mirrors the experience we promise on the landing page: a single query hydrates the student search results, surfaces dietary badges, and injects vendor availability so the cost of each recipe is transparent. Together with a thorough developer guide (covering environment variables, Prisma migrations, and repository structure), it helps new contributors ramp up quickly and keep Club Ovin Lovin’ growing.
