---
layout: project
type: project
image: img/framework.jpg
title: "Ovin Lovin"
date: 2025-12-17
published: true
labels:
  - Web Development
  - JavaScript
  - Leadership
summary: "Documenting how I led Club Ovin Lovin in building a full-stack hub for announcements, resources, and member engagement."
---

<img class="img-fluid" src="../img/framework.jpg" alt="Screenshot from the Ovin Lovin portal">

Club Ovin Lovin started as a handful of us who wanted to keep project updates, study guides, and workshop notes in one place. I volunteered to build the platform that would glue the club together, so I designed and shipped a web application that feels more like a digital clubhouse than a static site. I took the lead on specifying the information architecture, interviewing members about their pain points, and translating those insights into a clean dashboard for announcements, archives, and live links.

### Highlights

- Built a responsive component library so our event recaps, slides, and recordings render beautifully on phones, tablets, and the lab’s projector.
- Implemented role-based authentication, giving officers a secure authoring experience while every member still sees the latest content instantly.
- Automated the “join the club” process with a self-serve onboarding form that pipes data straight into our roster spreadsheet and mailing list.
- Embedded micro-interactions (like real-time RSVP counts and link previews) that make it obvious when a resource was updated or a meeting is live.

To keep the codebase maintainable, I split the app into API, data, and presentation layers. The snippet below shows how I wired up the event service so that the same endpoint powers the dashboard and the public agenda widget:

```js
// services/events.js
export async function listEvents({ limit = 10 } = {}) {
  const response = await fetch(`/api/events?limit=${limit}`);
  if (!response.ok) throw new Error('Unable to load events');
  const items = await response.json();
  return items.map((event) => ({
    ...event,
    start: new Date(event.start),
    end: new Date(event.end),
  }));
}
```

This project taught me how to be both the product owner and the engineer. I iterated quickly with feedback from each meeting, wrote the documentation that helped hand off maintenance, and mentored two new members by pairing on pull requests. Club Ovin Lovin now runs every workshop, fundraiser, and community update through the app, so the club’s energy lives online even when we’re not sharing the same lab space.
