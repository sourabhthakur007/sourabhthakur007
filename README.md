# Hi, I'm Sourabh 👋

**Backend engineer — Python · FastAPI · PostgreSQL · AWS.** Based in Himachal Pradesh, India.

I build backend systems and the infrastructure they run on. Over the last year I've shipped two products end to end, mostly on my own — from database and APIs to frontend, payments, servers, and the 2am incidents. Before that, three years at Samsung building video-processing pipelines on AWS.

Open to senior backend roles, remote — **available immediately.** Reach me on **[LinkedIn](https://linkedin.com/in/sourabh-thakur)**.

---

## What I'm building — [HimLocal](https://himlocal.com)

A multi-tenant SaaS platform that hotels, restaurants and shops in Himachal Pradesh use to run their business and sell online. I'm the only engineer on it — schema, backend, frontend, infrastructure, deploys. It's early (a handful of vendors), but the code does real work: **[anytimesport.in](https://anytimesport.in)**, a cricket-equipment retailer in Kullu, runs its entire storefront on it — catalogue, cart, UPI and card payments, a Google Shopping feed — on its own domain, taking real orders and real money.

One platform, five verticals, each vendor on their own subdomain or custom domain:

| Vertical | What it does |
|---|---|
| **Restaurants** | POS billing, kitchen display screen, table-QR ordering, receipt printing, cash reconciliation, and an **offline mode** so a café keeps taking orders when its internet drops |
| **Retail** | Storefronts with variants, cart, checkout, coupons, shipping, and an automated Google Shopping product feed |
| **Hotels** | Booking calendar with pricing rules, online check-in, and channel-manager sync |
| **Maps & treks** | A trail-curation tool and discovery map on PostGIS with a custom vector-tile pipeline |
| **Stays** | A metasearch surface over an external inventory partner, engineered to be CDN-cacheable |

## Also shipped — [TrackNation](https://tracknation.in)

A study platform for UPSC aspirants — free notes, active-recall tests, and a study tracker built around spaced repetition, so the system surfaces what a student is about to forget instead of what they just revised. **Live, with 80+ students studying on it daily.** Full-stack and solo: Python/FastAPI backend, MongoDB, React frontend, deployment.

## Selected engineering

- **Offline-first restaurant POS.** Cafés here lose connectivity for hours, so the tablet keeps working with no network. Offline order codes are unique *by construction* — café prefix + device + epoch + sequence — so two tablets can't mint the same number without asking a server. Every queued operation carries an idempotency key; the queue drains in one batched call and an operation is deleted from the device only once the server acknowledges it, so a failure stays visible instead of vanishing. A Web Locks leader stops multiple browser tabs from double-draining the same queue.

- **Concurrency-safe checkout.** Inventory is row-locked at checkout (`SELECT … FOR UPDATE`) so two people can't both buy the last item; payment creation is idempotency-keyed so a replayed gateway webhook can't double-charge; and stock held by abandoned carts is reclaimed instead of being lost forever.

- **Making an uncacheable map cacheable.** A map viewport is continuous, so every pan is a distinct URL and nothing caches. I snap the viewport centre to an integer grid cell, collapsing an infinite URL space into a finite one the CDN and browser can both cache — then bound cache staleness as arithmetic under the data partner's contractual price-freshness ceiling.

- **Event-driven media pipeline (Samsung).** I owned an AWS pipeline (S3 → SNS → SQS → Lambda → ECS Fargate) that ingested video, fingerprinted it, and fed a content-recognition system for a consumer entertainment platform — including capacity-aware eviction and re-queueing, partial-failure handling, the ops dashboard, and production on-call.

## How I work

I build with AI coding agents every day — mainly Claude Code. The discipline matters more than the tool: spec first, the agent produces the change, and I review every line before it lands. Nothing merges on a red test suite. It's the fastest way to build and also the fastest way to ship something you don't understand — so I don't keep code I couldn't explain in a review.

## Tech

**Languages** — Python, TypeScript / JavaScript, SQL, Bash
**Backend** — FastAPI, Node.js, REST API design, async Python, event-driven systems, message queues, background workers
**Data** — PostgreSQL, PostGIS, Redis, MongoDB, SQLAlchemy, schema migrations, query tuning
**Cloud** — AWS (EC2, S3, SNS, SQS, Lambda, ECS Fargate, SES, CloudFront, CloudWatch, IAM), Docker, nginx, Linux, CI/CD
**Frontend** — React, Next.js, TypeScript, Tailwind CSS

---

**[LinkedIn](https://linkedin.com/in/sourabh-thakur)** &nbsp;·&nbsp; [himlocal.com](https://himlocal.com) &nbsp;·&nbsp; [tracknation.in](https://tracknation.in)
