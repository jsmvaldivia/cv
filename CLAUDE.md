# CV Repository - Claude Code Documentation

## Repository Overview

**Purpose:** Personal CV/resume for Juan Valdivia, software engineer with 9+ years experience in distributed systems and platform engineering.

**Target Audience:** Technical hiring managers and recruiters across IC (Staff/Principal Engineer) and management (Tech Lead, Engineering Manager, Director) tracks.

**Philosophy:** ATS-friendly, one-page resume with quantifiable achievements and modern cloud-native positioning.

---

## ⚠️ CRITICAL: Accuracy Requirement

**Claude must NEVER fabricate, embellish, or assume information about experience, achievements, or technical details.**

- **Only use information explicitly provided by the user**
- **Never invent metrics, project details, or technologies used**
- **Never enhance achievements with made-up specifics**
- **When adding new experience, ask the user for exact details:**
  - What was the actual impact? (ask for numbers)
  - What technologies were used?
  - What was the timeline?
  - What were the measurable outcomes?

**If uncertain about any detail, ask rather than guess.**

---

## Primary Use Case

The main work in this repository is **updating CV content** (experience, skills, achievements). Most interactions will involve:
- Adding new roles or achievements
- Updating existing experience descriptions
- Refining impact statements
- Keeping content current and relevant

---

## Content Strategy

### Writing Principles

When updating CV content, follow these principles:

1. **Quantifiable achievements:** Always use metrics where possible
   - ✅ "reduced 600+ security vulnerabilities to zero"
   - ✅ "99.98% availability (2 hours total downtime)"
   - ✅ "scaled to 10 European markets within 18 months"
   - ❌ "improved security significantly"

2. **Active voice with strong action verbs:**
   - Lead with: Led, Built, Architected, Implemented, Drove, Achieved
   - Avoid: Responsible for, Worked on, Helped with

3. **Impact over responsibilities:**
   - ✅ "Reengineered release process, cutting deployment lead time from 14 days to near real-time"
   - ❌ "Managed the release process"

4. **Balance technical depth with business impact:**
   - Mention specific technologies when they differentiate or demonstrate expertise
   - Always connect technical work to business outcomes

5. **ATS-friendly formatting:**
   - No graphics, tables, or complex formatting
   - Simple, scannable structure
   - Keywords naturally integrated

### Length Constraints

**Hard requirement: Keep the CV to ONE PAGE.**

When adding new content:
- **Always ask before making compression decisions**
- Prioritize recent roles (Bose, Carlsberg) over older experience
- Older roles (STEF-IT, TIMWE) can be further compressed or removed
- Each new achievement may require cutting something else

### Current Section Strategy

**Professional Summary & Skills sections:**
- Keep both short (current length is acceptable)
- Do not expand these sections for now
- Future direction: may embed skills in experience and compress further
- When adding new content, prefer enriching experience descriptions over expanding these sections

### Technical Detail Level

**Ask the user before deciding how much technical detail to include.**

When proposing updates:
- Present options: high-level business impact vs. technical specificity
- Consider: Does this technology differentiate me? Is it relevant to target roles?
- Avoid: Exhaustive lists of every tool or library used

---

## Career Positioning

### Target Roles

This CV should work for both tracks:
- **IC track:** Staff Engineer, Principal Engineer, Platform Engineering Lead
- **Management track:** Tech Lead, Engineering Manager, Director of Engineering

Focus on **distributed systems, platform engineering, and B2B/e-commerce domains**.

### Geographic Flexibility

Optimize for all markets:
- Local Lisbon/Portugal opportunities
- European remote (emphasize language skills, cross-market experience)
- Global remote (emphasize distributed team experience)

**Keep location visible but not limiting.**

### Technology Positioning

**De-emphasize legacy enterprise tech:**
- AEM, Hybris, GWT, legacy SOA
- Only mention when critical for context (e.g., current Bose role)

**Emphasize modern cloud-native stack:**
- Kubernetes, microservices, event-driven architecture
- Go and Java (Spring Boot)
- AWS, platform engineering, API design
- Infrastructure as Code, observability, DevOps practices

---

## LaTeX Formatting Guidelines

Follow these conventions (guidelines, not strict rules - can suggest alternatives):

### Date Formats
- Running text: Use en-dash `–` for date ranges ("Mar 2025–Present")
- LaTeX fields: Double-hyphen `--` ("2011--2015")

### Structure Commands
- Use `\CVItem{date/role}{description}` for job entries
- Use `\CVSection{Title}` for major sections
- Use `\textbf{}` sparingly, only for sub-headings within experience

### Color and Emphasis
- `\color{RoyalBlue}` for headings and key emphasis
- Keep color usage consistent with existing style

### Spacing
- `\Sep` between major sections
- `\SmallSep` within sections
- Review spacing to maintain one-page constraint

---

## Build & Testing Workflow

### File Structure

- **cv.tex** - Main CV content (edit this file for content updates)
- **structure.tex** - LaTeX template and styling (rarely needs changes)
- **cv.pdf** - Generated output (auto-committed by CI, do not edit manually)
- **index.html** - GitHub Pages landing page
- **CNAME** - Custom domain configuration

### Immutable Content

**Only update these with explicit user instruction:**
- Contact information (email, phone, LinkedIn URL)
- Name and professional title structure
- Location

### CI/CD Pipeline

**GitHub Actions workflow:** `.github/workflows/ci.yml`

**How it works:**
1. Manually triggered via `workflow_dispatch` (not automatic on push)
2. Runs on `ubuntu-latest`
3. Deletes old `cv.pdf`
4. Compiles `cv.tex` using `xu-cheng/latex-action@v4`
5. Uploads PDF as artifact
6. Auto-commits `cv.pdf` back to repository

**To trigger a build:**
1. Go to GitHub Actions tab
2. Select "Build new CV version" workflow
3. Click "Run workflow"
4. Wait for completion (~1-2 minutes)

### Testing Process

After making LaTeX changes:
1. Review the diff in `cv.tex`
2. Suggest triggering the GitHub Actions workflow
3. Once built, review the generated `cv.pdf` for:
   - One-page constraint maintained
   - No formatting issues
   - Content renders correctly
   - No orphaned text or awkward breaks

**Local testing (if available):**
- User can compile locally with `pdflatex cv.tex`
- Requires LaTeX distribution installed

---

## Interaction Preferences

### How to Work Together

1. **Be concise:** Propose changes clearly without over-explaining LaTeX syntax
2. **Ask before major decisions:**
   - Compression or removal of content
   - Level of technical detail
   - Significant tone or structure changes
3. **Provide context:** When suggesting changes, briefly explain the reasoning
4. **Show before/after:** Use code blocks to show proposed changes

### When to Ask vs. Proceed

**Ask first:**
- Compressing or removing experience entries
- Changing technical detail level
- Modifying Professional Summary or Skills
- Any changes to contact information or structure

**Can proceed directly:**
- Fixing typos or grammar
- Updating dates for current role
- Minor LaTeX formatting consistency fixes
- Adding user-provided content with clear direction

### Achievement Documentation

When the user adds new achievements, always push for:
- **Quantifiable metrics:** Numbers, percentages, timeframes
- **Scope:** How many people/teams/markets impacted?
- **Outcome:** What was the measurable result?
- **Context:** What was the business impact?

**Template questions:**
- "What was the measurable outcome?" 
- "How many [users/teams/systems/markets] were affected?"
- "What improved and by how much?"
- "What was the timeline?"

---

## Example Workflows

### Workflow 1: Adding a New Achievement

```
User: "Add that I migrated the payment service to the new platform"

Claude: 
"I'd like to add this achievement to your Bose role. To write it effectively, I need some details:
- What was the impact? (latency improvement, cost reduction, reliability gain?)
- What was the timeline?
- What technologies were involved?
- Was there a measurable outcome? (% improvement, incidents reduced, etc.)"

User: [provides specifics]

Claude: [proposes exact text with metrics]
```

### Workflow 2: Updating for a New Role

```
User: "I'm leaving Bose and joining Company X as Staff Engineer"

Claude:
"I'll update your CV for the new role. A few questions:
1. Should the Bose section be compressed to make room? (It's currently detailed)
2. What should I highlight about the Bose tenure now that it's complete?
3. For Company X: what's the team size, tech stack, and initial focus areas?
4. Any achievements from Bose we should add before moving it to 'previous roles'?"

[User provides details, Claude proposes changes, shows impact on one-page constraint]
```

### Workflow 3: Compression Decision

```
Claude: 
"Adding this new achievement will exceed one page. Options:

A) Compress the TIMWE entry (2016-2017) to a single line
B) Remove the TIMWE entry entirely  
C) Compress parts of the Carlsberg section
D) Trim the Professional Summary

I recommend A - TIMWE is oldest and least relevant.
What's your preference?"
```

---

## Privacy & Security

- **Never commit sensitive information:** passwords, API keys, private contact details
- **Be cautious with personal data:** the CV is public on GitHub Pages
- **Contact information is intentionally public** (professional email, LinkedIn)

---

## Quick Reference

| Task | Command | Notes |
|------|---------|-------|
| Edit CV content | Edit `cv.tex` | Main content file |
| Trigger build | GitHub Actions → workflow_dispatch | Manual trigger only |
| View PDF | Check `cv.pdf` after build | Auto-committed by CI |
| Test locally | `pdflatex cv.tex` | Requires LaTeX installed |

---

## Summary

When working on this CV repository:
1. ✅ **Accuracy first** - never fabricate details
2. ✅ **Ask before compression** - one-page is sacred
3. ✅ **Quantify everything** - numbers tell the story
4. ✅ **De-emphasize legacy tech** - focus on modern cloud-native
5. ✅ **Balance IC and management positioning** - keep options open
6. ✅ **Test the PDF** - always verify after LaTeX changes

The goal: A compelling, accurate, one-page CV that works for technical leadership roles globally.
