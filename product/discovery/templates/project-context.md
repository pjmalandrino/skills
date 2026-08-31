# Project Context — [Project name]

> **Status:** ACTIVE  
> **Version:** 1.0.0  
> **Maintainer:** @First Last  
> **Creation date:** DD/MM/YYYY  
> **Last update:** DD/MM/YYYY  

> ⚠️ Keeping an outdated context produces outdated PRDs and US.

> **How to use it at kickoff:** first fill in the sections marked *Mandatory* (1, 2, 3, 4, 7, 8). The *Optional* sections may stay empty if not relevant. The *Evolving* sections (9 and 10) get enriched over the course of the project and start empty.

---

## 1. Project identity — *Mandatory*

- **Project name:** [Commercial product name]
- **Client:** [Full client name]
- **Mission type:** [From scratch / Migration / Run / Framing only / Mixed]
- **Current phase:** [Framing / MVP / Scale / Migration / Run / Maintenance]
- **Start date:** DD/MM/YYYY
- **Key milestones:** [Structuring deadlines, production releases, client
  validation steps]

## 2. Product — *Mandatory*

### Pitch

[3 to 5 lines describing what the product does, who it is for, and what it
brings. "Elevator pitch" level, readable by someone discovering the
project.]

### Value proposition

[Why the product exists, what business pain it solves, what it does better
than the existing solution — or than no solution at all.]

### Target audience

[Quick description of the product's users. Named personas are in
section 3.]

## 3. Personas — *Mandatory (at least one)*

> **SCUB conventions:**
> - If the client has an official label for the role, use that label rather than inventing one.
> - The persona **identifier** is fixed here and reused as-is in all PRDs and US for the project.
> - A reasonable number of personas is between 3 and 5; fewer indicates that not all personas have been identified, more means the persona breakdown is too fine-grained.

### [Persona name]

- **Identifier:** (e.g., `administrator`)
- **Role:** [Business function, level of responsibility in the organization]
- **Usage context:** [When, where, in what situation they use the product]
- **Functional expertise level:** [Novice / Regular / Expert — in the functional domain]
- **Tool expertise level:** [Novice / Regular / Expert — on the existing tool if there is one]
- **Main pain points:** *(optional)* [What they suffer with the current setup and what the product must solve]

### [Next persona]

[Same structure]

## 4. Business glossary — *Mandatory*

> Terms specific to the client's domain + acronyms. This section matters most for vertical domains (insurance, healthcare, legal, finance, transportation…). On a consumer product, it can be short but must exist, if only for the client's internal acronyms.

| Term / Acronym | Definition |
|----------------|------------|
| [Term] | [Short definition, 1-2 lines] |
| [Acronym] | [Expansion + definition] |

## 5. Technical ecosystem — *Optional*

[To be filled in if the stack or integrations have an impact on PRD/US
drafting. Skip if the project is purely functional at this stage.]

- **Frontend stack:** [Framework, UI lib]
- **Backend stack:** [Language, framework, DB]
- **AI stack:** [RAG, model]
- **Hosting / infra:** [Cloud provider, containerization]
- **External integrations:** [List of third-party systems the product talks
  to, and what for]
- **Authentication:** [Keycloak, other]

## 6. Design system & mockups — *Optional*

[To be filled in as soon as there is at least one master Figma file.]

- **Master Figma file:** [Link]
- **Design system / component library:** [Figma link + library name]
- **Main tokens:** [Primary/secondary colors, fonts — only the tokens that
  recur in specs]
- **Screen naming conventions:** [How Figma frames are named so you can find
  your way around]
- **Project-specific components:** [Recurring custom components: e.g.,
  "project card", "history panel"]

## 7. Tooling conventions — *Mandatory*

- **PRD numbering scheme:** `PRD-YYYYMMDD-XX` where
  `YYYYMM` matches the year (`YYYY`) and month (`MM`) the PRD was initialized and where `XX` is an integer ranging from 01 to 99 according to PRD numbering within the month
- **US numbering scheme:** [Jira format, e.g., `PROJ-X` where `X` is an integer ranging from 1 to n according to user story numbering (this numbering is automatically managed by Jira)]
- **Product documentation tool:** Confluence + space URL
- **Delivery tool:** Jira
- **PRD validation workflow:** [Who drafts? → Who reviews on the SCUB side? (optional) → Who validates
  on the client side]
- **Cadence of problem framing sessions:** [Weekly, bi-weekly, on demand]

## 8. Team & stakeholders — *Mandatory*

> Names can be anonymized (`anonymous`) for widely shared contexts, but the role structure must remain readable.

### SCUB side

| Role | Person | Confluence @mention |
|------|--------|---------------------|
| Product Manager | [Name] | @First Last |
| Tech Lead | [Name] | @First Last |
| UX/UI Designer | [Name] | @First Last |

### Client side

| Role | Person | Scope |
|------|--------|-------|
| Sponsor / decision-maker | [Name or anonymous] | [Final validation, arbitration] |
| Business owner | [Name or anonymous] | [PRD validation, prioritization] |
| Subject matter expert | [Name or anonymous] | [Reference on domain X] |

## 9. PRD index — *Evolving*

> Grows with each delivered PRD. Lets a reader or a new Claude thread know what has already been specified on the project and avoid overlaps or contradictions.

| ID | Title | Status | Link |
|----|-------|--------|------|
| [PRD-YYYYMM-XX] | [Title] | DRAFT / VALIDATED / DELIVERED | [Confluence URL] |

---

## Maintenance

- **Update at every:** new persona identified, major product decision, new technical integration, delivery of a new PRD (⚠️ remember to add the PRD in section 10), change of stakeholder on the client or SCUB side.
- **Versioning:** semver `x.y.z.` where `x = MAJOR` (e.g., change of stakeholder on the client side), `y = MINOR` (e.g., delivery of a new PRD) and `z = PATCH` (e.g., semantic fix)
- **Date format:** `DD/MM/YYYY` in the header and in change history tables (consistent with SCUB PRD conventions).

### Change history

| Date | Author | Nature of the change |
|------|--------|----------------------|
| DD/MM/YYYY | @First Last | Document initialization |
