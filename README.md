# Erik Pearson

Forward Deployed Engineer. Nine years customer-facing in field sales for a $6B distributor, and since 2023 the engineer who builds, deploys, and supports the software those same field teams use.

## Evals

I test a prompt or an agent against labelled data before I trust it, and I grade with code, not with another model.

- **[crm-agent-evals](https://github.com/blackdiamondcyber-png/crm-agent-evals)**: a tool-using CRM agent with seven tools over a seeded sales territory, and 56 tasks a rep might type between stops. The grader replays every write the agent made against a fresh database and never grades its prose. On a one-line prompt, Claude Sonnet carried out seven of eight bulk status-change requests without asking, 72 status changes in all. With six written rules it asked first every time, got 87.5% of tasks right, and never wrote to an account the rep had not named. A third prompt written from its misses reached 96.4%, which I report as optimistic because its rules came from the same tasks. It also caught strict tool schemas making Sonnet leak its own tool-call markup into search filters: 16 of 238 calls, and none once strict mode was off. The first full run mostly found bugs in my own harness, and the README lists all four.
- **[field-notes-to-crm](https://github.com/blackdiamondcyber-png/field-notes-to-crm)**: a dictated visit note in, a structured CRM activity out, using Claude with a strict tool schema. 150 labelled notes, per-field scores, hallucination rate and cost per run. Written rules took contact extraction from 63.3% to 99.7% F1 and dropped activity-type accuracy from 94.0% to 85.3%, and the harness traced the drop to one rule. CI re-scores the committed predictions in TypeScript and in an independent Python scorer, and the two must agree exactly.

## Production

Three applications have run in production since 2024 across three regional offices: 17,770 accounts live on the map, resolved from 22,494 source records, and 77 provisioned users who adopted it with no mandate and no official project status behind it. Row-level security is on every table, with 133 policies across the 42 tables the apps read and write. I designed the schema, wrote the front ends, built the auth and RLS model, deployed it, ran the onboarding sessions, and still support all of it while carrying a full sales quota.

The products run on my employer's data and stay private. What is here is the technique underneath them, pulled out and written up so you can read the actual work in a few minutes:

- **[rls-multitenant-patterns](https://github.com/blackdiamondcyber-png/rls-multitenant-patterns)**: Postgres row-level security for multi-tenant field apps. Wide reads, narrow writes, and policies with tests against them, including a bulk import only the service role can call and a test proving PUBLIC cannot.
- **[entity-resolution-postgres](https://github.com/blackdiamondcyber-png/entity-resolution-postgres)**: deduplicating business records from three sources that never agree. Normalize, block, score and apply survivorship, all in plain SQL. A 20,000-row synthetic benchmark in CI shows blocking cutting 199,990,000 possible pairs to 4,104 while keeping all 4,000 planted duplicates reachable.
- **[n8n-approval-patterns](https://github.com/blackdiamondcyber-png/n8n-approval-patterns)**: tokenized multi-stage approvals. Single-use hashed tokens, GET to confirm and POST to commit, and an audit trail.
- **[supabase-security-audit](https://github.com/blackdiamondcyber-png/supabase-security-audit)**: the read-only audit I ran against my own production database before anyone asked. 45 functions now execute only under the service role. CI runs the audit against a seeded database, which is how it found two bugs in the audit itself.
- **[image-to-excel-converter](https://github.com/blackdiamondcyber-png/image-to-excel-converter)**: photograph a document, get a clean Excel file. Claude Vision does the extraction. It is one of three capture tools where a model actually runs, alongside a barcode scanner and a part finder. The three territory apps run no models.

I wrote the four pattern repos up in one sitting in August 2026, when I started a job search, so their commit history is short. The systems behind them have been running since 2024. The two eval repos are newer still: both were built in September 2026, with Claude Code, and their histories are short for the same reason.

**Stack:** Claude API (tool use, structured output, Vision), LLM evals, Claude Code, TypeScript, JavaScript, Python, SQL, React, Next.js, Node.js, PostgreSQL, Supabase, row-level security, REST APIs, Mapbox GL JS, Vercel, n8n, PWA.

Outside work: TinyTally, a baby tracker I built for my own family, now in App Store review. Next.js, TypeScript, Supabase with row-level security on all 21 tables, offline-first writes through an IndexedDB queue and a hand-rolled service worker, 1,297 tests, 42 migrations since July 2026. The repo is private (a family app); the [live walkthrough](https://www.youtube.com/watch?v=pFtf6lvvLDU) shows it running on production against a seeded family.

Open to travel and on-site deployment.

[Portfolio](https://erik-pearson-portfolio.vercel.app) · [LinkedIn](https://www.linkedin.com/in/erikpearson2) · [Resume (PDF)](https://erik-pearson-portfolio.vercel.app/Erik_Pearson_Resume.pdf) · [Walkthrough videos](https://www.youtube.com/@TexasFDE)
