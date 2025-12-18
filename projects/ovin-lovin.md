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

# Club Oven Lovin' Project Overview

![Toaster oven pizzas on sheet pans](../public/images/hero-toaster-1.jpeg)

## Mission and audience
Club Oven Lovin' gives college students healthy, budget-friendly meals they can cook with just a toaster oven—no full kitchen required. The landing hero highlights recipes, price breakdowns, and dietary filters tailored to ingredients near the UH campus, with quick links to sign in or browse recipes immediately. 【F:src/components/marketing/HeroSection.tsx†L17-L63】

### Why the hero and stats matter
The hero section is a warm, orange-and-cream welcome that spells out the value proposition and gives students two clear calls to action: sign in to start cooking or jump straight into browsing recipes. It pairs short copy with an image slider of toaster-oven meals to set expectations and showcase achievable dishes. 【F:src/components/marketing/HeroSection.tsx†L17-L68】

Right below, Quick Stats runs server-side to log visits and display live counts of recipes, users, and total page views pulled from Prisma, reinforcing momentum and community activity without blocking page renders if telemetry fails. 【F:src/components/QuickStats.tsx†L19-L72】

## What we built
- **Landing story + quick metrics.** A warm hero with an image slider introduces the club, while the Quick Stats panel logs visits and shows live counts of recipes, users, and total page views using Prisma. 【F:src/components/marketing/HeroSection.tsx†L17-L68】【F:src/components/QuickStats.tsx†L19-L72】
- **Recipe browsing with smart search.** Students can filter community recipes by name, ingredient, tags, or dietary needs; cards display tags, average rating, and a favorite heart tied to the viewer's profile. 【F:src/components/RecipeListClient.tsx†L21-L92】【F:src/components/RecipeCard.tsx†L41-L138】
- **Rich recipe detail pages.** Each recipe shows owner, tags, ratings, and reviews; signed-in cooks can edit, delete, or favorite entries, and the page suggests where to buy ingredients based on vendor inventories. 【F:src/app/recipes/[id]/page.tsx†L13-L214】【F:src/app/recipes/[id]/page.tsx†L215-L431】
- **Community contributions.** Authenticated users submit new dishes with validation, image uploads, tags, and dietary flags; success toasts and redirects keep the flow smooth. 【F:src/components/AddRecipeForm.tsx†L17-L147】
- **Personalized home and profile.** Signed-in members land on a tailored home page with curated tips and top-rated picks, and can manage their profile, dietary badges, contributed recipes, and favorites from a dedicated profile hub. 【F:src/app/user-home-page/page.tsx†L1-L167】【F:src/components/UserProfile.tsx†L1-L133】
- **Vendor partnership tools.** Vendors manage storefront details and live ingredient lists, edit prices/availability inline, and add new items that surface automatically on recipe pages. 【F:src/app/vendors/page.tsx†L1-L41】【F:src/components/Vendor.tsx†L1-L170】

![Caprese flatbread ready for the toaster oven](../public/images/recipes/toaster-oven-caprese-flat.png)

## Technical foundation
- Built with **Next.js 14** and **React Bootstrap** for fast, responsive pages styled to match the orange-and-cream brand palette. 【F:src/app/layout.tsx†L1-L31】【F:src/components/marketing/HeroSection.tsx†L17-L37】
- **NextAuth** secures sign-in, sign-up, protected routes, and role-aware actions (admin vs. recipe owner). 【F:src/app/browse-recipes/page.tsx†L1-L33】【F:src/app/add-recipe/page.tsx†L1-L18】
- **Prisma + PostgreSQL** power recipes, favorites, vendors, and telemetry like page visits; all counts and lookups come from the database for real-time accuracy. 【F:src/components/QuickStats.tsx†L19-L72】【F:src/app/recipes/[id]/page.tsx†L163-L207】
- **UX polish** includes SweetAlert-style toasts, live favorite toggles, and rating widgets to keep contributors engaged while maintaining data integrity through schema validation. 【F:src/components/AddRecipeForm.tsx†L86-L147】【F:src/components/RecipeCard.tsx†L41-L138】

## Impact
Together we shipped a fully authenticated community cookbook tailored to UH students, complete with contribution workflows, vendor sourcing, and engagement telemetry. The experience now greets members with personalized tips, curates top-rated dishes, and keeps vendors in sync so students can cook more and spend less.