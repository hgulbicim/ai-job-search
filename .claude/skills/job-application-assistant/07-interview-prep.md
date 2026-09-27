---
framework_version: 1.0.0
---

# Interview Preparation Guide

<!-- SETUP: STAR examples are personalized by running /setup based on your actual experience -->

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## Ready-Made STAR Examples

<!-- These are populated by /setup from your actual experience. Below are templates showing the format. -->

### 1. Customer Service Platform at Scale - Hepsiburada (architecture under load)
**S:** Hepsiburada's customer-service platform served millions of daily interactions across IVR,
live chat, WhatsApp, ticketing, and agent tooling. Peak campaign days pushed the system far
past what its original design assumed.
**T:** As Principal Software Developer I owned the architecture and technical direction of the
whole portfolio, with availability and latency as the hard constraints.
**A:** Decomposed the platform into .NET microservices communicating asynchronously over
RabbitMQ and MassTransit, pushed read paths onto Redis and Elasticsearch, moved workloads onto
Kubernetes, and instrumented everything with ELK, Prometheus, and Grafana so bottlenecks were
visible before they became incidents.
**R:** Services in the portfolio sustained over 250 million requests per day with real-time
processing and high availability through peak load.
**Use for:** "Tell me about a system you designed", "How do you handle scale?", "Describe your
biggest technical challenge", "How do you approach observability?"

### 2. C++ to .NET Core Migration - Softtech (legacy modernisation)
**S:** Softtech (İşbank's technology arm) ran critical payment functionality on legacy C++
applications that were expensive to change and increasingly hard to staff.
**T:** As the architect on the programme I was responsible for the migration design and the
technology decisions, with zero tolerance for payment downtime.
**A:** Mapped the legacy behaviour, carved it into .NET Core microservices, and migrated
incrementally rather than attempting a big-bang rewrite, running old and new in parallel while
traffic shifted. Re-architected the notification infrastructure as event-driven microservices in
the same programme, and planned the WinForms-to-Angular conversion of the operator UIs.
**R:** Legacy payment applications moved onto a modern, maintainable .NET Core stack without a
production outage, and the resulting services were far cheaper to extend.
**Use for:** "Tell me about a legacy modernisation", "How do you de-risk a big migration?",
"Describe a technical decision you had to defend", "Walk me through an architecture you own"

### 3. Leading an 11-Person Cross-Functional Team - Hepsiburada (leadership)
**S:** The Customer Services team combined backend, frontend, QA, and product under constant
delivery pressure, with 11 people across four disciplines.
**T:** As Software Development Team Lead I was accountable for delivery throughput and for the
technical health of the platform at the same time.
**A:** Ran the team on Agile practices, kept ownership clear across the four disciplines, set
code review and quality standards (SonarQube gates, testing expectations), and stayed hands-on in
architecture and code so technical decisions were made with real context. Worked directly with
Product Owners and the Product Lead so scope negotiations happened on evidence, not opinion.
**R:** Sustained delivery on a high-traffic platform, and I was promoted to Principal Software
Developer out of the role.
**Use for:** "Tell me about leading a team", "How do you handle conflict with product?",
"Describe a time you had to balance speed and quality", "How do you mentor engineers?"

### 4. Bank VPOS Payment Gateways - İnnova (regulated, high-stakes delivery)
**S:** Turkish banks including İş Bankası, VakıfBank, Ziraat Bankası, and Akbank needed Virtual
POS payment gateways, systems where a defect is a financial and regulatory incident.
**T:** Build and maintain the gateways and the merchant-facing integration layer, under PCI DSS.
**A:** Implemented 3D Secure flows, tokenization, and multi-bank routing; built VPOS Client so
merchants could reach multiple VPOS servers through one interface; used RabbitMQ and MassTransit
for asynchronous transaction processing; added reconciliation logic for recurring and
instructional payments; delivered both cloud and on-premise deployments with full transaction
monitoring and alerting.
**R:** Production payment gateways for four major banks, plus tax, customs, and social-security
collection integrations via GİB, SGK, and the Ministry of Customs.
**Use for:** "Tell me about working under compliance constraints", "How do you ensure
correctness in critical systems?", "Describe integration work", "What's your security mindset?"

<!-- Add more STAR examples as needed. Aim for 4-6 covering different competencies. -->

## Common Tough Questions

### "Why are you looking to leave Axess AG after about a year?"
> Honest, forward-looking, no criticism of Axess. Something close to: "Axess gave me a solid
> landing in the Austrian market and I've enjoyed the access-control domain. What I'm looking for
> is scope closer to what I had at Hepsiburada, owning architecture for systems where scale and
> technical direction are the core of the job, and a package that reflects a principal-level
> remit. That's what drew me to this role specifically." Do **not** lead with money in the first
> interview even though it is the real driver. Raise compensation once mutual interest is clear.

### "You don't speak German. How will that work?"
> Straight answer, no apology: "I work in English, and I have for years. At Hepsiburada I worked
> remotely from Salzburg with an İstanbul-based team entirely in English, and my current work is
> in an international product context. I'm settled in Salzburg long term." Never claim a German
> level. If the role genuinely requires German, it should have been filtered before applying.

### "Your degrees are in economics and business, not computer science."
> "That's right. I've been building production software for 13 years, including payment gateways
> for four Turkish banks under PCI DSS and platforms serving 250 million requests a day. The MBA
> is actually why I'm comfortable in the architecture conversations that are half business
> case, half system design." No defensiveness. It is a differentiator, not a gap.

### "What's your salary expectation?"
> Target band is EUR 90,000-110,000 gross per year on the Austrian 14-salary basis. Anchor at the
> upper half when the role is Principal, Architect, or Lead. Ask for the posting's band first
> where possible. Austrian ads state a legal collective-agreement minimum (KV-Mindestgehalt) that
> is routinely below the real offer, so never treat the stated minimum as the ceiling.

### "You don't have [specific skill/experience]."
> [PREPARE YOUR ANSWER - acknowledge the gap, bridge to adjacent experience, show willingness to learn]

### "Where do you see yourself in 5 years?"
> [PREPARE YOUR ANSWER - show ambition aligned with the role's growth path]

### "What's your biggest weakness?"
> [PREPARE YOUR ANSWER - genuine weakness with concrete mitigation strategy]

### "Why this company specifically?"
> Customize per company. Must reference: specific projects, company values, market position, or team structure. Never give a generic answer.

## Questions You Should Ask Interviewers

### About the Role
- "What does a typical week look like in this role?"
- "What would success look like in the first 6 months?"
- "What's the biggest challenge the team is facing right now?"

### About the Team
- "How big is the team, and how do you divide work?"
- "What does the development/project lifecycle look like, from idea to production?"
- "How do you onboard new team members?"

### About Tech & Growth
- "What's your current tech stack for [relevant area]?"
- "Is there room to grow into more architectural or strategic decisions?"
- "How does the team stay current with new tools and methods?"

### About Culture (use these to prevent disappointment)
- "How would you describe the team culture?"
- "What does professional development look like here?"
- "Is there flexibility for remote/hybrid work?"
- "What's the balance between development/new projects and maintenance work?"
- "How would you describe the leadership style in this team?"
- "What do people who thrive here have in common?"

## Phone/Video Interview Tips
- Have STAR examples written out (use this file)
- Keep a glass of water nearby
- Smile when speaking (it changes your tone)
- Ask for clarification if a question is vague
- It's OK to take 5 seconds to think before answering
- End with: "Is there anything else you'd like to know about my background?"

## After the Application (Best Practice)

### Follow-Up Etiquette
- **Don't call to "stand out"** or to learn more about the role post-submission - this risks a negative impression
- If the employer specified a timeline, respect it and wait
- If no timeline was given and significant time has passed (2+ weeks), a brief call to ask about status is acceptable
- If you have genuinely new, relevant information to share, a short follow-up is fine

### Thank-You Notes
- When you receive any update (interview invitation, rejection, or status update), send a brief thank-you message
- Express appreciation for their time and the process
- Keep it short (2-3 sentences)

## Roleplay Guidelines
When the user asks for interview practice:
1. Ask which role/company to simulate
2. Start with easy warm-up questions ("Tell me about yourself")
3. Progress to role-specific technical questions
4. Include 1-2 behavioral questions using the competencies from the job posting
5. End with a tough question or curveball
6. After each answer, give brief feedback: what worked, what to sharpen
7. Suggest which STAR example would work best for each question
