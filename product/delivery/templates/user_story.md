# [ID] — User story title

> **Epic:** <epic name>
> **Priority:** <Must / Should / Could / Won't>

## Context

**As a** <relevant persona>
**I want to** <action>
**In order to** <benefit / business value>

The objective of this user story is <short but literal description of what must be done>.

## Business rules
- [ ] <business rule>
- [ ] <business rule>

## Acceptance tests

### Nominal scenario — <scenario name>
```gherkin
Given <initial context>
And <additional context>
When <triggering event>
Then <expected result>
And <additional result>
```

### Alternative scenario — <scenario name>
```gherkin
Given <context>
When <event>
Then <expected result>
```

### Error scenario — <scenario name>
```gherkin
Given <context>
When <invalid event>
Then <expected error message or behavior>
```

## Documentation
- [Confluence link to the PRD](url)
- [Link to the Figma mockup](url)
- [If available: screenshot or link to a prototype]

## Technical notes
- [Notes useful to the dev team, by the tech lead]

## Definition of Done — *(to be validated with the team)*
- [ ] Acceptance criteria met
- [ ] Code reviewed and merged
- [ ] Unit and integration tests passing
- [ ] Documentation updated
- [ ] PO validation
