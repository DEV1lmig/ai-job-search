# Search Queries for Job Scraper

<!-- Populated 2026-10-22 for Miguel Quiroz: based in Venezuela, remote only. PRIMARY TARGET: short freelance / contract projects with fast delivery and fast payment. Full-time remote roles are secondary. Re-run /setup --section search to adjust. -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`; Danish demos and any skill you add with `/add-portal` are included the same way. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

**Language scope:** write every query category in every language listed in your CLAUDE.md Languages table (typically 1-2, sometimes more). A posting requiring a language you have *not* declared, as a job condition, is excluded before scoring; a posting requiring a *higher level* than you declared in a language you *do* work in is flagged for your own judgment, not excluded — see `04-job-evaluation.md`'s Language Gate, the single source of truth for this rule. Translate each category's keywords rather than machine-translating word-for-word (e.g. "Frontend Developer" -> "Desarrollador Frontend", not a literal word-for-word translation) if you work in more than one language.

## Search Sites

Primary for short projects (freelance / contract, the main target):
- **upwork.com** - largest freelance marketplace; filter: fixed-price or hourly, "payment verified", web / AI / mobile
- **workana.com** - LATAM freelance marketplace (Spanish and English postings)
- **freelancer.com** - global freelance board
- **contra.com** - project-based work for designers and developers, no platform fee
- **toptal.com** / **arc.dev** / **lemon.io** - vetted contract developer networks (apply once, then receive matched contracts)
- **wellfound.com** - startups often post contract and part-time roles
- **freehire** - covered by `freehire-search` CLI

Secondary for full-time remote roles:
- **linkedin.com/jobs** - LinkedIn job listings (filter: Remote / Venezuela / Latin America); also covered by `linkedin-search` CLI
- **weworkremotely.com** - remote-only board, strong for full-stack and TypeScript/Python roles
- **remoteok.com** - remote-only board with salary data
- **getonbrd.com** - LATAM tech board (Spanish and English postings, many remote)
- **torre.ai** - LATAM remote talent marketplace
- **wellfound.com** - startup jobs (AI startups hiring remote)
- **freehire** - covered by `freehire-search` CLI

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for known target companies

### Priority 0: Short freelance / contract projects (fast delivery, fast payment)

The main target. Prefer postings with bounded scope, fixed price or hourly rate, verified payment and no multi-round interview.

```
site:upwork.com/jobs "React" OR "Next.js" fixed-price
site:upwork.com/jobs "FastAPI" OR "Python" API
site:upwork.com/jobs "RAG" OR "LLM" OR "chatbot" documents
site:upwork.com/jobs "React Native" OR "Expo" app
site:upwork.com/jobs "landing page" Figma Next.js
site:workana.com "desarrollador" React OR Next.js proyecto
site:workana.com "Python" OR "FastAPI" OR "inteligencia artificial" proyecto
site:workana.com "diseño UI" OR "landing page" Figma
site:freelancer.com "Next.js" OR "FastAPI" project
site:contra.com "full stack" OR "React" project
site:linkedin.com/jobs "contract" "Full Stack" React Python remote
site:linkedin.com/jobs "freelance" OR "contractor" "Next.js" remote
site:linkedin.com/jobs "part-time" "AI Engineer" OR "RAG" remote
site:wellfound.com "contract" full stack
```

## Query Categories

Queries are grouped by priority. Write **each category in every language from your Languages table** (see Language scope above). Combine each query with your location terms (e.g. your city, region, or metro area) where the site supports it.

**Organize by function, not job title.** The same underlying work carries different titles across companies and markets (a "Data Scientist" role at one employer may be posted as "Insights Analyst" or "Data Consultant" at another). Name each priority category after the function it covers, and list several plausible job titles as query variants within that category rather than betting an entire priority tier on one exact title string.

### Priority 1: Full-Stack Product Engineering (TypeScript + Python)

Full-time remote roles that match your strongest direction. Secondary to Priority 0; prefer postings that mention contract, part-time or fast hiring.

```
site:linkedin.com/jobs "Full Stack Engineer" remote Latin America
site:linkedin.com/jobs "Full-Stack Developer" React Python remote
site:linkedin.com/jobs "Software Engineer" Next.js FastAPI remote
site:weworkremotely.com "Full Stack" TypeScript Python
site:remoteok.com "full stack" react python
site:getonbrd.com "Full Stack" remoto
site:linkedin.com/jobs "Desarrollador Full Stack" remoto Venezuela OR Latinoamérica
site:linkedin.com/jobs "Ingeniero de Software" React Python remoto
```

### Priority 2: AI / LLM Engineering over documents

These match your domain expertise.

```
site:linkedin.com/jobs "AI Engineer" RAG remote
site:linkedin.com/jobs "LLM Engineer" OR "Applied AI Engineer" Python remote
site:linkedin.com/jobs "AI Engineer" "document" OR "OCR" OR "GraphRAG" remote
site:wellfound.com "AI Engineer" RAG
site:weworkremotely.com "AI Engineer" OR "LLM" Python
site:linkedin.com/jobs "Ingeniero de IA" OR "AI Engineer" RAG remoto Latinoamérica
site:getonbrd.com "Inteligencia Artificial" Python remoto
```

### Priority 3: Frontend / Mobile Product Engineering

Adjacent roles you could pivot into.

```
site:linkedin.com/jobs "Frontend Engineer" React Next.js remote
site:linkedin.com/jobs "React Native Developer" OR "Expo" remote
site:linkedin.com/jobs "Product Engineer" React remote
site:weworkremotely.com "Frontend" React Next.js
site:linkedin.com/jobs "Desarrollador Frontend" React remoto Latinoamérica
site:getonbrd.com "Frontend" React remoto
```

### Priority 4: Broader Technical / Backend / Consulting

Wider net for general technical roles.

```
site:linkedin.com/jobs "Backend Engineer" Python FastAPI remote
site:linkedin.com/jobs "Software Engineer" Azure Kubernetes remote
site:remoteok.com python developer
site:linkedin.com/jobs "technical consultant" AI OR "machine learning" remote
site:linkedin.com/jobs "Desarrollador Backend" Python remoto
site:torre.ai "Software Engineer" remote
```

## Location Filter

When evaluating results, verify the job location is within reasonable commute distance from your home. Define acceptable areas:
- Fully remote (worldwide, LATAM, or Americas time zones) - ideal
- Remote from Venezuela explicitly allowed, or "remote - Latin America" - ideal
- Maracaibo, Venezuela (on-site or hybrid) - acceptable
- Remote requiring EU working hours - borderline (UTC-4 vs UTC+1/+2, ~5-6h offset)
- Caracas on-site - borderline (~10h by road from Maracaibo; only for relocation-worthy roles) <!-- VERIFY -->
- On-site anywhere outside Venezuela, or "remote - US only" with residency requirement - too far / excluded

## Language Filter

Your working languages and levels are in CLAUDE.md's Languages table. When filtering scraped results, apply `04-job-evaluation.md`'s Language Gate: a posting requiring a language you haven't declared at all is excluded; a posting requiring a higher level than you declared in a language you do work in is not excluded, flag it clearly instead (see `job-scraper/SKILL.md`'s Step 3 "Quick Fit Assessment" for how the flag surfaces in `/scrape` output). Postings simply *written* in a language you don't work in, that don't require it on the job, are fine.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
