# Portfolio Improvement Plan — Product Engineer Positioning

## Recruiter Review Summary

### What's working

- **Clear positioning.** "Frontend Lead & Product Engineer" is immediately visible. The role chips in the About section reinforce this.
- **Shipped work at a real company.** All four projects are features shipped at Xano, not toy projects. Recruiters value this.
- **Demo videos exist** for Query Wizard and Workspace Search. Video is high-signal for product engineers because it shows you can communicate what you built.
- **Concise, opinionated voice.** The copy has personality ("eliminating friction to unlock maximum flow-state") without being unprofessional.

### What's hurting

1. **No case studies.** The showcase cards are surface-level — a title, one sentence, and a YouTube link. A recruiter scanning this portfolio cannot answer: *What problem did she solve? How did she approach it? What was the measurable outcome?* Without that narrative, the portfolio reads as a feature list, not proof of product thinking.
2. **Two of four projects say "coming soon."** Half the showcase feeling incomplete undermines credibility. Either add substance or remove the cards until they're ready.
3. **No quantified impact beyond one metric.** Workspace Search mentions "under 10% search churn," which is the strongest line on the page. The other three projects have zero metrics. Product engineer roles live and die by outcomes.
4. **About section is generic.** "Building intuitive software end-to-end" and "sharp product sense" are claims without evidence. The case studies should provide that evidence; the About section should summarize it.
5. **Tech stack is underspecified.** Only Angular is named. Recruiters searching for Elasticsearch, TypeScript, Node, or other keywords won't find matches. Case studies are the natural place to surface this.
6. **No description of the product context.** A recruiter who doesn't know Xano has no frame of reference. One line ("Xano is a no-code backend platform used by X users") would anchor everything.
7. **Resume is a Google Drive link.** This is fragile (permissions, load time) and not indexable. Consider hosting a PDF directly or embedding key resume content.

---

## Improvement Plan: Atomic Tasks

The core improvement is **adding dedicated case study pages** for each project, then linking them from the showcase cards. Below is the full breakdown.

---

### Phase 0: Content gathering (you provide the raw material)

Before any code is written, you need to fill in the details for each project. For each of the four projects, answer the prompts below. Write rough notes — they don't need to be polished. I'll shape them into case study content.

---

#### Task 0.1 — Query Wizard: answer content prompts

Fill in these fields:

| Prompt | Your answer |
|--------|-------------|
| **Company context:** What is Xano in one sentence? Who are its users? | |
| **Problem:** What specific pain point did users face with Elasticsearch/OpenSearch queries before this feature existed? How did you discover this problem (support tickets, user interviews, analytics, your own frustration)? | |
| **Your role:** Were you the sole engineer? Did you work with a designer, PM, or other engineers? What did YOU specifically own? | |
| **Constraints:** Any technical constraints, timeline pressure, or business requirements that shaped the solution? | |
| **Solution approach:** Walk through the key design decisions. Why an interface that generates QueryDSL? What alternatives did you consider and reject? | |
| **Technical details:** What technologies did you use (Angular, TypeScript, Elasticsearch client, etc.)? Any interesting architectural decisions? | |
| **Key interaction flows:** Describe 2-3 core user flows. What does a user do step-by-step? | |
| **Results:** What happened after launch? Metrics (adoption %, support ticket reduction, time saved)? Qualitative feedback? | |
| **Iteration:** Did you ship a v2? What would you change? What did you learn? | |
| **Screenshot/demo assets:** Do you have screenshots, GIFs, or the YouTube demo already linked? Can you get 3-5 annotated screenshots showing key states? | |

---

#### Task 0.2 — Performance Insights: answer content prompts

| Prompt | Your answer |
|--------|-------------|
| **Company context:** (same as above, or anything specific to this product area) | |
| **Problem:** What pain did users have identifying backend inefficiencies? What were they doing before this feature? | |
| **Your role:** What did you own — research, design, frontend, backend, all of the above? | |
| **Constraints:** Timeline, technical debt, backward compatibility, etc.? | |
| **Solution approach:** How does the feature pinpoint inefficiencies? What does the "function stack" view look like conceptually? Why this approach? | |
| **Technical details:** Profiling implementation, data visualization approach, Angular components involved, API design? | |
| **Key interaction flows:** Walk through the user journey of finding and fixing a bottleneck. | |
| **Results:** Metrics? Adoption? Feedback? Performance improvements users achieved? | |
| **Iteration:** Current status, future plans, lessons learned? | |
| **Screenshot/demo assets:** Any screenshots or recordings available? | |

---

#### Task 0.3 — Workspace Search: answer content prompts

| Prompt | Your answer |
|--------|-------------|
| **Company context:** What does "workspace" mean in Xano? What are users searching for? | |
| **Problem:** What was search like before? What does "search churn" mean specifically in this context (user searches, doesn't find, searches again)? How was the <10% churn measured? | |
| **Your role:** Sole owner, or collaborative? Frontend only, or full stack? | |
| **Constraints:** Data volume, response time requirements, existing search infrastructure? | |
| **Solution approach:** What approach did you take to reduce churn? Better ranking, better UI, better indexing, autocomplete, filters? | |
| **Technical details:** Search implementation (client-side, API-driven, Elasticsearch?), debouncing, ranking algorithm, UI components? | |
| **Key interaction flows:** Describe the search experience step by step. What makes it fast and accurate? | |
| **Results:** The <10% churn number — what was it before? Any other metrics (search latency, completion rate, user satisfaction)? | |
| **Iteration:** What would you improve next? What surprised you? | |
| **Screenshot/demo assets:** Screenshots of the search UI, before/after if possible? | |

---

#### Task 0.4 — Database Copilot: answer content prompts

| Prompt | Your answer |
|--------|-------------|
| **Company context:** What database operations do Xano users need to perform? What's their technical skill level? | |
| **Problem:** Why is a chat interface needed? What's hard about database management for Xano's users today? | |
| **Your role:** What did you own? Was AI/LLM integration involved? If so, what model/approach? | |
| **Constraints:** Safety requirements (preventing destructive queries), accuracy requirements, latency? | |
| **Solution approach:** How does the copilot ensure "safety & clarity"? What guardrails exist? How does it translate natural language to database operations? | |
| **Technical details:** LLM integration, prompt engineering, schema awareness, Angular chat UI, backend validation layer? | |
| **Key interaction flows:** Show a conversation example — user asks something, copilot responds, user confirms, action executes. | |
| **Results:** Metrics? Adoption? Error rate? User feedback? | |
| **Iteration:** What's next? What's the hardest unsolved problem? | |
| **Screenshot/demo assets:** Chat interface screenshots, example conversations? | |

---

### Phase 1: Astro infrastructure for case study pages

#### Task 1.1 — Create a case study layout component

- [ ] Create `src/layouts/CaseStudyLayout.astro`
- [ ] Accept props: `title`, `description`, `project` (for meta tags and OG data)
- [ ] Include shared head content (fonts, meta, favicon) via BaseLayout or a shared partial
- [ ] Add a sticky/fixed back-to-home navigation link
- [ ] Add a consistent header structure: project title (h1), subtitle/tagline, role chip, timeline chip

#### Task 1.2 — Create reusable case study section components

- [ ] Create `src/components/case-study/CaseStudyHero.astro` — project title, one-line summary, role, timeline, hero image/screenshot
- [ ] Create `src/components/case-study/CaseStudySection.astro` — generic section block with heading + body slot (reused for Problem, Approach, Solution, Results)
- [ ] Create `src/components/case-study/MetricCard.astro` — big number + label for impact stats (e.g., "<10% churn", "3x faster")
- [ ] Create `src/components/case-study/ImageBlock.astro` — responsive image with optional caption, used for screenshots and diagrams
- [ ] Create `src/components/case-study/TechStack.astro` — horizontal list of technology chips/tags

#### Task 1.3 — Add case study routes

- [ ] Create `src/pages/case-study/query-wizard.astro`
- [ ] Create `src/pages/case-study/performance-insights.astro`
- [ ] Create `src/pages/case-study/workspace-search.astro`
- [ ] Create `src/pages/case-study/database-copilot.astro`
- [ ] Each page imports `CaseStudyLayout` and composes the section components with project-specific content

#### Task 1.4 — Update ShowcaseCard to link to case studies

- [ ] Add optional `caseStudyLink` prop to `ShowcaseCard.astro`
- [ ] When `caseStudyLink` is provided, render a "Read the case study" link alongside or instead of "Watch the demo"
- [ ] Update the `projects` array in `Showcase.astro` to include `caseStudyLink: '/case-study/query-wizard'` etc.
- [ ] Remove `comingSoon: true` from projects once their case study pages exist

---

### Phase 2: Write case study content (per project)

Each case study page follows the same narrative structure. Tasks are broken down per section so you can review and refine incrementally.

#### Task 2.1 — Query Wizard case study content

- [ ] 2.1.1 Write the Context section (1-2 paragraphs: what is Xano, who are the users, what's Elasticsearch's role)
- [ ] 2.1.2 Write the Problem section (the pain point, how it was discovered, what users were doing before)
- [ ] 2.1.3 Write the Approach section (exploration, design decisions, alternatives considered)
- [ ] 2.1.4 Write the Solution section (how the feature works, key interaction flows, 2-3 screenshots)
- [ ] 2.1.5 Write the Technical Details section (stack, architecture, interesting engineering decisions)
- [ ] 2.1.6 Write the Results section (metrics, feedback, before/after)
- [ ] 2.1.7 Write the Reflection section (lessons learned, what you'd do differently)
- [ ] 2.1.8 Add screenshots/images to `public/images/case-studies/query-wizard/`
- [ ] 2.1.9 Embed or link the existing YouTube demo video

#### Task 2.2 — Workspace Search case study content

- [ ] 2.2.1 Write the Context section
- [ ] 2.2.2 Write the Problem section (especially define "search churn" and the before-state)
- [ ] 2.2.3 Write the Approach section
- [ ] 2.2.4 Write the Solution section
- [ ] 2.2.5 Write the Technical Details section
- [ ] 2.2.6 Write the Results section (anchor around the <10% churn stat, add more if possible)
- [ ] 2.2.7 Write the Reflection section
- [ ] 2.2.8 Add screenshots/images to `public/images/case-studies/workspace-search/`
- [ ] 2.2.9 Embed or link the existing YouTube demo video

#### Task 2.3 — Performance Insights case study content

- [ ] 2.3.1 Write the Context section
- [ ] 2.3.2 Write the Problem section
- [ ] 2.3.3 Write the Approach section
- [ ] 2.3.4 Write the Solution section
- [ ] 2.3.5 Write the Technical Details section
- [ ] 2.3.6 Write the Results section
- [ ] 2.3.7 Write the Reflection section
- [ ] 2.3.8 Add screenshots/images to `public/images/case-studies/performance-insights/`

#### Task 2.4 — Database Copilot case study content

- [ ] 2.4.1 Write the Context section
- [ ] 2.4.2 Write the Problem section
- [ ] 2.4.3 Write the Approach section
- [ ] 2.4.4 Write the Solution section
- [ ] 2.4.5 Write the Technical Details section
- [ ] 2.4.6 Write the Results section
- [ ] 2.4.7 Write the Reflection section
- [ ] 2.4.8 Add screenshots/images to `public/images/case-studies/database-copilot/`

---

### Phase 3: Landing page refinements

#### Task 3.1 — Add a one-liner about Xano

- [ ] Add a brief context line in the Showcase section header or as a subtitle: something like "Features I shipped at Xano — the scalable no-code backend platform for 100K+ builders." (adjust to reality)

#### Task 3.2 — Strengthen the About section

- [ ] Replace generic claims with specific evidence pulled from the case studies (e.g., "Reduced search churn to under 10% by rethinking Xano's workspace navigation" is stronger than "sharp product sense")
- [ ] Add 2-3 more technology keywords that appear in the case studies (TypeScript, Elasticsearch, etc.)

#### Task 3.3 — Update meta tags and OG data

- [ ] Ensure each case study page has unique `<title>` and `<meta description>` for SEO/sharing
- [ ] Add OG image meta tags if screenshot assets are available

---

### Phase 4: Navigation and discoverability

#### Task 4.1 — Add case study navigation within pages

- [ ] Add "Next case study" / "Previous case study" links at the bottom of each case study page
- [ ] Add a "Back to showcase" link

#### Task 4.2 — Update the main Nav

- [ ] Consider whether the Nav should gain a "Case Studies" link now that there are dedicated pages (optional — the showcase cards may be sufficient)

---

## Recommended execution order

1. **Phase 0 first.** Content gathering is the bottleneck. No code should be written until at least one project's prompts are fully answered.
2. **Phase 1 next.** Build the page infrastructure with placeholder content so you can iterate on layout.
3. **Phase 2, one project at a time.** Start with Query Wizard or Workspace Search (the two with existing demos). Ship one complete case study before starting the next.
4. **Phase 3 after at least two case studies are live.** The landing page updates depend on having real content to reference.
5. **Phase 4 last.** Navigation polish only matters once there are pages to navigate between.

---

## Case study page structure (reference)

Each case study page should follow this narrative arc:

```
1. Hero          → Project name, one-line summary, role, timeline, hero screenshot
2. Context       → What is Xano? Who are the users? Why does this problem space matter?
3. Problem       → The specific pain point. Evidence of the problem. Stakes.
4. Approach      → How you explored the problem. Research, ideation, alternatives.
5. Solution      → What you built. Key flows. Screenshots. Demo video embed.
6. Tech Stack    → Technologies used, architectural decisions.
7. Results       → Metrics. Before/after. User feedback. Business impact.
8. Reflection    → What you learned. What you'd do differently. What's next.
```

This structure maps directly to what product engineer interviewers evaluate: problem identification, solution design, execution, and impact measurement.
