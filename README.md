# Erik Pearson

Forward Deployed Engineer. Nine years customer-facing in field sales for a $6B distributor, and since 2023 the engineer who builds, deploys, and supports the software those same field teams use.

Three applications have run in production since 2024 across three regional offices: 22,494 practices mapped, 77 provisioned users, 54 activated, 38 of them active in the last 90 days. Multi-tenant row-level security enabled on all 47 core tables and carrying 133 policies. I designed the schema, wrote the front ends, built the auth and RLS model, deployed it, ran the onboarding sessions, and still support all of it while carrying a full sales quota.

The products run on my employer's data and stay private. What is here is the technique underneath them, pulled out and written up so you can read the actual work in a few minutes:

- **rls-multitenant-patterns**: Postgres row-level security for multi-tenant field apps. Wide reads, narrow writes, tested policies.
- **entity-resolution-postgres**: deduplicating business records from three sources that never agree. Normalize, block, score, survivorship. No external service, no ML pipeline, just SQL.
- **n8n-approval-patterns**: tokenized multi-stage approvals. Single-use hashed tokens, GET to confirm and POST to commit, an audit trail.
- **supabase-security-audit**: the read-only audit I ran against my own production database before anyone asked. 45 functions now execute only under the service role.
- **image-to-excel-converter**: photograph a document, get a clean Excel file. Claude Vision does the extraction, one of the two places in anything I have built where a model actually runs.

I published the four pattern repos on the same day in August 2026, when I decided to write them up for a job search. The commit history is short on purpose. The reasoning is not.

**Stack:** TypeScript, JavaScript, React, Next.js, Node.js, Python, PostgreSQL, Supabase, row-level security, REST APIs, Mapbox GL JS, Vercel, n8n, PWA.

Open to travel and on-site deployment.

[Portfolio](https://erik-pearson-portfolio.vercel.app) · [LinkedIn](https://www.linkedin.com/in/erikpearson2) · [Resume (PDF)](https://erik-pearson-portfolio.vercel.app/Erik_Pearson_Resume.pdf)
