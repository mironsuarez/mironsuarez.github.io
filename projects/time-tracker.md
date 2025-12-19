---
layout: project
type: project
image: img/projects/timer/image.png
title: "Time Tracker"
date: 2023-11-15
published: true
labels:
  - Next.js
  - Prisma
  - Productivity
  - UX Research
summary: "A minimalist time tracker where I spin up multiple timers, categorize activities, and audit how I really spend my week."
---

<img class="img-fluid rounded shadow mb-4 w-100" src="../img/projects/timer/image.png" alt="Screenshot from the timer app">

Time Tracker grew out of my need to understand where my evenings were going. Already built apps felt too rigid and often require payment or subscription. So I built a multi-timer workspace that lets me track context switches without losing history.

## Highlights

- **Unlimited timers.** Create timers for study, workouts, freelancing, or rest and run any combination simultaneously.
- **Timeline view.** A heatmap and stacked bar chart show exactly how long I spent on each category per day.
- **Session notes.** Each timer can capture a short reflection so I remember what I accomplished during that block.

## Under the hood

- **Next.js app router** with server components renders timers even when the client reconnects mid-session.
- **Prisma + SQLite** when offline, with sync to PostgreSQL.


Simple helpers like these keep the business logic readable while I focus on UX experiments, such as how to display overlapping timers or how to summarize a week without clutter. This timmer is now my go-to ritual check, and it has drastically improved how intentionally I spend my time.
