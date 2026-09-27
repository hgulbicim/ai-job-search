# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`; Danish demos and any skill you add with `/add-portal` are included the same way. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

**Language scope:** write every query category in every language listed in your CLAUDE.md Languages table (typically 1-2, sometimes more). A posting requiring a language you have *not* declared, as a job condition, is excluded before scoring; a posting requiring a *higher level* than you declared in a language you *do* work in is flagged for your own judgment, not excluded — see `04-job-evaluation.md`'s Language Gate, the single source of truth for this rule. Translate each category's keywords rather than machine-translating word-for-word (e.g. "Frontend Developer" -> "Desarrollador Frontend", not a literal word-for-word translation) if you work in more than one language.

## Search Sites

Primary (Austrian market - no CLI installed yet, so these run as WebSearch fallback. Scaffold
`karriere.at` with `/add-portal` to turn it into a proper CLI):
- **karriere.at** - Austria's largest general job board, the main source for this search
- **linkedin.com/jobs** - LinkedIn job listings (filter: Austria / Salzburg); also covered by the `linkedin-search` CLI
- **devjobs.at** - Austrian developer-only board, high signal for .NET roles
- **stepstone.at** - second large general board, good Vienna and remote coverage
- **willhaben.at/jobs** - broad Austrian coverage, weaker on senior engineering
- **AMS eJob-Room (jobs.ams.at)** - public employment service, occasional postings the private boards miss

The Danish demo CLIs shipped with this framework (`jobindex-search`, `jobnet-search`,
`jobdanmark-search`, `jobbank-search`) are **not relevant to this profile** and should be skipped
during `/scrape`.

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for known target companies

## Query Categories

Queries are grouped by priority. Write **each category in every language from your Languages table** (see Language scope above). Combine each query with your location terms (e.g. your city, region, or metro area) where the site supports it.

**Organize by function, not job title.** The same underlying work carries different titles across companies and markets (a "Data Scientist" role at one employer may be posted as "Insights Analyst" or "Data Consultant" at another). Name each priority category after the function it covers, and list several plausible job titles as query variants within that category rather than betting an entire priority tier on one exact title string.

### Priority 1: Senior / Staff Backend Engineering (.NET)

These match your strongest and most desired career direction.

Title variants to rotate: Senior Software Engineer, Senior Backend Developer, Senior .NET
Developer, Staff Engineer, Softwareentwickler, Senior Software Developer, Backend Engineer,
Senior Full Stack Developer. German-language titles must stay in the rotation: many Austrian ads
are written in German for roles whose working language is English.

```
site:karriere.at "Senior Software Engineer" Salzburg
site:karriere.at "Senior .NET" Salzburg
site:karriere.at "Backend Developer" C# Salzburg
site:karriere.at "Softwareentwickler" C# Salzburg
site:devjobs.at ".NET" Salzburg
site:stepstone.at "Senior Software Engineer" Salzburg
site:linkedin.com/jobs "Senior Backend Engineer" Austria
site:linkedin.com/jobs ".NET" Salzburg Austria
```

### Priority 2: Architecture and Technical Leadership

These match your domain expertise.

This is the target band (EUR 90-110k). Title variants: Solution Architect, Software Architect,
Principal Engineer, Lead Developer, Engineering Lead, Team Lead, Tech Lead, Softwarearchitekt,
Entwicklungsleiter.

```
site:karriere.at "Software Architect" Salzburg OR Oberösterreich
site:karriere.at "Solution Architect" Austria
site:karriere.at "Principal" Engineer Austria
site:karriere.at "Lead Developer" .NET Austria
site:karriere.at "Softwarearchitekt" Salzburg
site:devjobs.at Architect Salzburg
site:linkedin.com/jobs "Solution Architect" Salzburg Austria
site:linkedin.com/jobs "Engineering Lead" Austria remote
```

### Priority 3: Payments / Fintech and High-Scale Platforms (domain edge)

Adjacent roles you could pivot into.

Six years of payments and banking experience is the strongest differentiator, and fintech is
the highest-paying Austrian sector for this stack. Weight these even when the employer is
Vienna-based, provided the role is remote-friendly.

**Excluded sector: gambling / betting / casino / iGaming** (ADMIRAL, NOVOMATIC, Greentube,
Sportsbook Software, Entain/bwin and similar). Drop these results before presenting, whatever
the fit.

```
site:karriere.at payment .NET Austria
site:karriere.at fintech backend Austria remote
site:karriere.at "high traffic" OR "microservices" .NET Austria
site:linkedin.com/jobs payments backend engineer Austria remote
```

### Priority 4: Broader Technical / Consulting

Wider net for general technical roles.

```
site:karriere.at C# Entwickler Salzburg
site:karriere.at "Full Stack" .NET Angular Austria
site:karriere.at Homeoffice .NET Entwickler Österreich
site:linkedin.com/jobs "C# developer" Salzburg
site:stepstone.at .NET Entwickler Österreich remote
```

## Location Filter

When evaluating results, verify the job location is within reasonable commute distance from your home. Define acceptable areas:
Home base: **Salzburg city (5020)**. No relocation under any circumstances.

- **Salzburg city and the immediate belt** - Anif, Wals-Siezenheim, Grödig, Bergheim, Hallein,
  Puch, Eugendorf, Seekirchen, Elsbethen, Koppl. Onsite and hybrid both fine.
- **Salzburg Land, wider** - Bischofshofen, St. Johann, Golling. Roughly 45-60 minutes. Acceptable
  only for hybrid roles with 2 or fewer office days.
- **Austria-wide (Vienna, Linz, Graz, Innsbruck)** - acceptable **only** at 80-100% remote with
  occasional onsite. Vienna fintech employers belong here and are worth the flag.
- **Upper Austria (Wels, Marchtrenk, Linz)** - borderline, 1 to 1.5 hours. Include only with a
  strong remote component. Not a daily commute.
- **Germany / Bavaria (Freilassing, Munich, Traunstein)** - out of scope this round, and most
  postings there require German anyway.
- **Anything requiring relocation** - hard FAIL.

## Language Filter

Your working languages and levels are in CLAUDE.md's Languages table. When filtering scraped results, apply `04-job-evaluation.md`'s Language Gate: a posting requiring a language you haven't declared at all is excluded; a posting requiring a higher level than you declared in a language you do work in is not excluded, flag it clearly instead (see `job-scraper/SKILL.md`'s Step 3 "Quick Fit Assessment" for how the flag surfaces in `/scrape` output). Postings simply *written* in a language you don't work in, that don't require it on the job, are fine.

**Concretely for this profile:** working languages are Turkish (native) and English (B2).
**German is not spoken.** A posting that requires German as a job condition is excluded. A posting
merely *written* in German, for a role whose working language is English, is **not** excluded, and
this distinction matters enormously in Austria: a large share of karriere.at ads are German-
language for English-speaking engineering teams. When a German ad is silent on the required
language, check the employer's English careers page before excluding it, and flag rather than drop
when it stays ambiguous.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
