---
applyTo: "**/*"
description: "Repository architecture, companion-file roles, integration points, agent responsibilities, and ontological evolution mechanism for the subdomain."
---

# Companion File Structure & Repository Architecture

This file documents the companion-file codex and how agents should interpret the repository structure.

- **README.md** — Human-facing entry point. Quick start, project overview, and contribution guide.
- **.github/instructions/scss.instructions.md** — Genesis ontological SCSS design system guidance, semantic mapping, zero raw CSS policy, and evolution mechanism.
- **.github/instructions/html.instructions.md** — Template and Jekyll/Liquid guidance, include rules, and accessibility checks.
- **.github/instructions/js.instructions.md** — JS entry, asset ordering, vendor rules, and HTML-in-JS scans.
- **.github/instructions/testing.instructions.md** — Testing philosophy, conventions, and CI/CD hooks.
- **.github/instructions/architecture.instructions.md** — This file: repository architecture, integration points, and evolution mechanism.
- **.github/prompts/** — MCP prompts for automated testing and subdomain evolution agent.
- **.github/agents/** — Role-focused agent files (subdomain-evolution-agent, scss-refactor-agent, etc.).

Each file is atomic: it covers one domain of guidance. Together, they form a codex for both humans and Copilot agents.

## Repository layout (agent interpretation)

- Root directory contains subdomain-specific content and configuration
- `_sass/` — Subdomain SCSS files using Genesis ontological design system
  - `_sass/_main.scss` — Entry point, must import `@import "ontology/index";` first
  - `_sass/pages/` — Page-specific semantic mappings
  - `_sass/sections/` — Section-specific semantic mappings
  - `_sass/components/` — Component-specific mappings (if needed)
  - `_sass/vendor/` — Third-party CSS (isolated, documented)
- `_includes/`, `_layouts/` — Jekyll templates and components
- `assets/` — Static assets (JS, images, fonts)
- `_data/` — Data files for Jekyll
- `.github/` — Repository guidance and automation

## Theme Integration

This subdomain uses the **ASI Saga Genesis Theme** from https://github.com/ASISaga/theme.asisaga.com

### Remote Theme Configuration
- Theme is loaded via Jekyll's `remote_theme` in `_config.yml`
- Theme provides the Genesis Ontological SCSS Engine
- Subdomain SCSS imports ontology via `@import "ontology/index";`

### Three-Tier Architecture

The Genesis Semantic SCSS Engine uses a three-tier architecture:

1. **Tier 1: Content (Subdomain HTML)**
   - Responsibility: Defines WHAT the data is
   - Constraint: No style attributes; semantic classes only
   - Location: This repository's HTML/templates

2. **Tier 2: Interface (Ontological API)**
   - Responsibility: Defines the ROLE of content
   - Constraint: Agnostic; no CSS properties
   - Location: Theme `_sass/ontology/_interface.scss`

3. **Tier 3: Engine (Visual Implementation)**
   - Responsibility: Defines the LOOK (OKLCH, Bento, Glassmorphism)
   - Constraint: Only place for raw CSS properties
   - Location: Theme `_sass/ontology/_engines.scss`

**Critical Rule**: Subdomain SCSS must NEVER contain raw CSS properties. All styling comes from ontological mixins.

## Integration points (high level)

### SCSS Integration
- Subdomain imports ontology: `@import "ontology/index";`
- All styling uses semantic mixins (genesis-environment, genesis-entity, etc.)
- Zero raw CSS properties in subdomain SCSS
- SCSS structure mirrors HTML DOM hierarchy

### Theme Coordination
- **For breaking changes**: Create coordination issue, link PRs across theme and subdomain repos
- **For new ontological variants**: Follow evolution mechanism (see below)
- **For design tokens**: Changes happen in theme; subdomains consume
- Prefer additive changes in theme with gradual deprecation

### Vendor Flow
- Vendor artifacts prepared locally and committed under `_sass/vendor/`
- Document vendor source, version, and license
- Minimize vendor usage; prefer ontological solutions

### CI Hooks
- Automated checks via GitHub Actions
- MCP tools for heavier audits (Playwright, accessibility)
- Prompts in `.github/prompts/` invoke MCP capabilities

## Ontological Evolution Mechanism - Living Genome

The Genesis Semantic Design System is a **Living Genome** that evolves through intelligent collaboration.

### For This Subdomain (Local Intelligence)

**When you discover a semantic gap:**

1. **Review existing ontology** - Check all 31 variants across 6 categories
2. **Try combinations** - Mix existing mixins creatively first
3. **Identify genuine gap** - Is this semantic (WHAT) or visual (HOW)?
   - Visual preference → Use existing mixins
   - Semantic pattern → Potential ontological proposition

4. **Create proposition** - Use template in `.github/prompts/subdomain-evolution-agent.prompt.md`
5. **Submit to theme** - PR to theme repository with:
   - Clear intent (WHAT the semantic role is)
   - Strong context (WHY it's needed)
   - Universal applicability (WHO else might use it)
   - Proper category fit (WHERE it belongs)

6. **Theme review** - Theme Genome Agent evaluates:
   - Redundancy check (can existing mixins solve this?)
   - Generalization check (universal vs. unique pattern?)
   - Ontological purity (semantic vs. visual?)

7. **Implementation** - If approved:
   - Theme adds variant to `_engines.scss`
   - Documents in GENOME.md with origin story
   - Subdomain pulls updated theme and implements

### Resources for Evolution

- **Theme Repository**: https://github.com/ASISaga/theme.asisaga.com
- **Integration Guide**: Theme `_sass/ontology/INTEGRATION-GUIDE.md`
- **Agent Ecosystem**: Theme `.github/AGENTS.MD`
- **Evolution Philosophy**: Theme `evolution.md`
- **Genome History**: Theme `GENOME.md`
- **Subdomain Evolution Agent**: `.github/prompts/subdomain-evolution-agent.prompt.md`

### Philosophy

Every ontological variant has an **origin story**. The system documents:
- Which subdomain requested it
- What semantic gap it filled
- How the system evolved

This creates **design with memory** - future developers understand not just WHAT exists, but WHY.

## Agent responsibilities (architecture-specific)

### Subdomain Evolution Agent
- Identifies semantic gaps in ontology
- Creates well-formed ontological propositions
- Submits PRs to theme with proper documentation
- Implements approved variants locally
- Maintains semantic consistency

### SCSS Refactor Agent
- Converts legacy CSS to ontological mixins
- Audits HTML for semantic structure
- Creates mirrored SCSS hierarchy
- Removes raw CSS properties
- Validates zero-CSS policy

### General Copilot Agent
- Consults domain-specific instruction files
- Validates site structure and intentional overrides
- Ensures cross-repo coordination for breaking changes
- Invokes MCP tooling for heavy audits
- Provides invocation artifacts in `.github/prompts/` when required

## Change coordination guidance

### For SCSS Changes
- **New page/section**: Add semantic SCSS file in `_sass/pages/` or `_sass/sections/`
- **Semantic gap**: Follow evolution mechanism to propose to theme
- **Visual tweak**: Use existing ontological mixins; do not add raw CSS
- **Vendor addition**: Document in `_sass/vendor/` with license and source

### For Breaking Theme Changes
- Create coordination issue in both repositories
- Link PRs: theme PR ↔ subdomain PR
- Assign reviewers from both teams
- Document migration path in PR bodies
- Test across all subdomains before merge

### For HTML/Template Changes
- Maintain semantic class names (content-focused)
- Ensure SCSS structure mirrors new DOM hierarchy
- Update corresponding SCSS files with ontological mappings
- Validate accessibility (WCAG AA)

## Validation & Quality Gates

Before committing changes:

### SCSS Validation
- [ ] Zero raw CSS properties
- [ ] No @extend usage
- [ ] Imports `@import "ontology/index";` first
- [ ] SCSS nesting mirrors HTML DOM
- [ ] Semantic class names used
- [ ] Appropriate ontological mixins applied

### Semantic Purity
- [ ] HTML uses semantic tags appropriately
- [ ] Class names describe WHAT, not HOW
- [ ] Styling comes from ontological roles, not visual preferences
- [ ] No inline styles or inline event handlers

### Documentation
- [ ] Comments explain semantic intent, not implementation
- [ ] Vendor sources documented with license
- [ ] Ontological propositions follow template
- [ ] Migration notes for breaking changes

## Quick Reference Links

- **Theme Docs**: https://github.com/ASISaga/theme.asisaga.com
- **SCSS Instructions**: `.github/instructions/scss.instructions.md`
- **HTML Instructions**: `.github/instructions/html.instructions.md`
- **JS Instructions**: `.github/instructions/js.instructions.md`
- **Testing Instructions**: `.github/instructions/testing.instructions.md`
- **Evolution Agent**: `.github/prompts/subdomain-evolution-agent.prompt.md`