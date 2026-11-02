# PRD (brief, internal): Overseas User Knowledge Hub

| | |
|---|---|
| **Owner** | Product (me) |
| **Status** | Released and deployed on the company's internal server |
| **Audience** | Product, operations, after-sales, brand |
| **Version** | v1.2 (released) → deployed |

## 1. Background

User feedback about overseas products lives in three disconnected places: community-group posts, e-commerce orders, and support email. Nobody can answer “what do users of model X say, and what did they buy?” without manual work. Product decisions about improvements, selection and marketing lack a shared evidence base.

## 2. Goals and non-goals

**Goals**
1. Link user, post, purchase and product in one searchable place.
2. Surface each product's strengths, weaknesses, common questions and known solutions.
3. Cut the time to answer a user-voice question from a day to minutes.

**Non-goals (this release):** public access, real-time sentiment alerts, replying to users from the tool.

## 3. Users and key use cases

| User | Question | View |
|---|---|---|
| Product manager | What do owners of this model complain about most? | Model × Topic |
| Product manager | Why did this buyer choose the product? | User trajectory |
| After-sales | Has this problem been seen before? What fixed it? | Search, Q&A |
| Operations / brand | What are people asking before they buy? | Overview, Search |

## 4. Scope and requirements

| ID | Requirement | Priority | Status |
|---|---|---|---|
| F1 | Import community posts (text, author, date) and orders | P0 | Done |
| F2 | Full-text search with filters: model, intent, topic, sentiment, purchase stage, source | P0 | Done |
| F3 | Original and translated text shown together | P0 | Done |
| F4 | Model × Topic heat map with click-through to posts | P0 | Done |
| F5 | User trajectory timeline (why bought, what bought, usage, feedback) | P0 | Done |
| F6 | Match posts to orders (by username, then email) with a visible match source | P0 | Done |
| F7 | Unified labels: 10 intents, 14 topic tags, 4 sentiments, purchase stage, model + confidence | P0 | Done |
| F8 | Support tickets and group-join forms imported and linked | P1 | Done |
| F9 | Historical backfill and de-duplication by post link; label only new posts | P1 | Done |
| F10 | Natural-language Q&A with source links | P1 | Done |
| F11 | Change log for every data and site update | P1 | Done |
| F12 | Masked (name and email hidden) version for wider sharing | P2 | Planned |
| F13 | Comments and solutions structured from support replies | P2 | In progress |

## 5. Data and quality

- **Sources:** community posts; e-commerce orders (US, three months); support-ticket mailbox; group-join forms.
- **Matching:** username first; email once the mailbox is available; same-name cases flagged for manual review.
- **Labeling:** rule-based and LLM-assisted; model labels carry a confidence level (high / medium / low), and inferred models are marked.
- **QA:** spot-check about 30 labels per release; fix rules, then re-run on affected posts.
- **Known limits:** posts only (no comments), name-based matching can be wrong, orders have no refund reason.

## 6. Privacy and compliance

- Customer names, emails and addresses are stored only on the internal server, behind company-network access.
- The mailbox export was approved by the manager before use.
- Order details exclude street address and phone number.
- Any version shown outside the team masks names and emails (F12).

## 7. Success metrics

| Metric | Target | Result |
|---|---|---|
| Time to answer a user-voice question | < 10 minutes | Achieved for common questions |
| Share of posts with a model label | > 90% | Achieved; “unspecified” kept explicit |
| Share of posts linked to orders | Track | About 20% in the first release |
| Weekly active internal users | Track | Product and after-sales teams adopted |

## 8. Milestones and progress

| Phase | Content | Status |
|---|---|---|
| 1. MVP | Posts + orders; search, heat map, trajectory, overview | Done |
| 2. Data expansion | Support tickets, group-join forms, historical backfill, unified labels, matching by email | Done |
| 3. Quality and Q&A | Label spot-check, rule fixes, natural-language Q&A, change log | Done |
| 4. **Internal deployment** | Moved from a prototype to the company's internal server; access control; scheduled refresh | **Done** |
| 5. Next | Masked version, comments and solutions, wider rollout | Planned |

**Release log**

| Version | Highlights |
|---|---|
| v1.0 | First release: posts + orders, four views |
| v1.1 | Unified labels, extra sources, matching improvements |
| v1.2 | Backfill and de-duplication, Q&A, change log; ready for deployment |

## 9. Risks and open questions

| Risk | Mitigation |
|---|---|
| Wrong name-based matches | Show match source; manual review of collisions; add email matching |
| Label drift as products change | Spot-check each release; keep rules versioned |
| Personal data exposure | Internal network only; masked version for sharing |
| Sample skew (active community members are not all users) | Always show posts-vs-orders share next to volume |

**Open:** when to open the tool beyond product and after-sales; how to structure support replies as “solutions”.
