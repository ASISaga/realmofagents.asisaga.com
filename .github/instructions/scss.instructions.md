---
applyTo: "**/_sass/**,**/*.scss,**/_sass/**/_*.scss"
description: "SCSS guidance for subdomain: Genesis ontological design system, semantic mapping, zero raw CSS, and evolution mechanism."
---

# Genesis Ontological SCSS Design System

This subdomain uses the **Genesis Semantic SCSS Engine** from the theme repository. All SCSS must follow ontological principles.

## Core Principle: Zero Raw CSS

Subdomain SCSS files must contain **NO raw CSS properties**. All styling comes from ontological mixins.

❌ **Wrong (Old Way):**
```scss
.my-card {
  padding: 2rem;
  background: oklch(0.20 0.04 245 / 0.85);
  border-radius: 12px;
}
```

✅ **Correct (Ontology Way):**
```scss
.my-card {
  @include genesis-entity('primary');  // All styling from engine
}
```

## SCSS File Locations & Structure

- Subdomain SCSS lives under `/_sass/`.
- Page-specific styles: `/_sass/pages/`.
- Section-specific styles: `/_sass/sections/`.
- Component partials: `/_sass/components/` (if needed).
- Vendor partials: `/_sass/vendor/` — keep vendor code isolated and document the vendor source and version.

## Import Chain & Entry Points

- Entry point: `_sass/_main.scss`
- **MUST** import ontology first: `@import "ontology/index";`
- Then import page/section partials
- Keep imports at the top level minimal

Example:
```scss
---
---
@import "ontology/index";

@import "pages/realm-of-agents";
@import "sections/realm-of-agents";
```

## Ontological API - Six Categories

### 1. `genesis-environment($logic)` - Layout & Spatial Organization
- `'distributed'` - Card grid layouts (Bento auto-fit)
- `'focused'` - Reading-optimized (centered, max-width)
- `'associative'` - Network/connection layouts
- `'chronological'` - Timeline/sequential layouts
- `'manifest'` - Dashboard/high-density layouts

### 2. `genesis-entity($nature)` - Visual Presence & Weight
- `'primary'` - Main content blocks (elevated, glassmorphism)
- `'secondary'` - Supporting content (lighter presence)
- `'imperative'` - Critical/urgent elements (alerts, CTAs)
- `'latent'` - Backgrounded content (reduced opacity)
- `'aggregate'` - Container/summary blocks
- `'ancestral'` - Historical/archived content

### 3. `genesis-cognition($intent)` - Typography & Information Intent
- `'axiom'` - Headlines/titles (large, bold)
- `'discourse'` - Body text/prose (readable, serif)
- `'protocol'` - Code/technical content (monospace)
- `'gloss'` - Small annotations/metadata
- `'motive'` - Persuasive/instructional text (accent)
- `'quantum'` - Tags/chips (small, uppercase)

### 4. `genesis-synapse($vector)` - Interaction & Navigation
- `'navigate'` - Links to other pages
- `'execute'` - Primary action buttons
- `'inquiry'` - Search/expand actions
- `'destructive'` - Dangerous actions (delete, reset)
- `'social'` - Social sharing buttons

### 5. `genesis-state($condition)` - Temporal State
- `'stable'` - Normal state
- `'evolving'` - Updating/streaming content
- `'deprecated'` - Outdated information
- `'locked'` - Restricted access
- `'simulated'` - Preview/projection data

### 6. `genesis-atmosphere($vibe)` - Sensory Texture
- `'neutral'` - Standard appearance
- `'ethereal'` - Light, minimal, bright
- `'void'` - Dark, immersive, focused
- `'vibrant'` - Colorful, energetic, data-rich

## Best Practices

### Semantic Purity
- Use meaningful class names: `.research-paper`, not `.blue-box`
- Think WHAT it is, not HOW it looks
- One semantic class per element in HTML

### Mirrored Structure
SCSS nesting must mirror HTML DOM hierarchy exactly:

```html
<main class="research-hub">
  <section class="paper-grid">
    <article class="paper-card">
```

```scss
.research-hub {
  @include genesis-environment('focused');
  
  .paper-grid {
    @include genesis-environment('distributed');
    
    .paper-card {
      @include genesis-entity('primary');
    }
  }
}
```

### Single Responsibility
Apply appropriate mixins from each category:
- One `genesis-environment` per layout container
- One `genesis-entity` per content block
- One `genesis-cognition` per text element
- One `genesis-synapse` per interactive element
- Optional `genesis-state` and `genesis-atmosphere` modifiers

## Vendor & Third-party CSS

- Vendors should be placed in `/_sass/vendor/`
- Import after ontology but before local overrides
- Verify vendor license and document origin
- Minimize vendor usage; prefer ontological solutions

## Forbidden Patterns

### NO @extend
- Do NOT use `@extend` - it breaks ontological purity
- Use mixins from ontology instead

### NO Raw CSS Properties
- NO `padding`, `margin`, `color`, `font-size`, `display`, etc.
- NO custom CSS properties (`--custom-var`)
- NO raw measurements (`px`, `rem`, `em`, `%`)

### NO Deep Specificity
- Avoid selectors >4 levels deep
- Avoid global element selectors in component partials
- Keep selectors focused and semantic

## Evolution Mechanism

Found a semantic gap? The ontology evolves!

### Before Creating a PR to Theme:
1. Review all 31 ontological variants
2. Try combining existing mixins creatively
3. Check if your need is semantic (WHAT) or visual (HOW)
   - Visual = use existing mixins
   - Semantic = potential ontological proposition

### Creating an Ontological Proposition:
1. Identify the semantic gap clearly
2. Create a proposition using the template in `.github/prompts/subdomain-evolution-agent.prompt.md`
3. Submit PR to theme repository with:
   - Clear intent (WHAT the semantic role is)
   - Strong context (WHY it's needed)
   - Universal applicability (WHO else might use it)
   - Proper category fit (WHERE it belongs)
4. Theme Genome Agent will review and approve/refine

### Resources:
- **Theme Repository**: https://github.com/ASISaga/theme.asisaga.com
- **Integration Guide**: `_sass/ontology/INTEGRATION-GUIDE.md`
- **Agent Ecosystem**: `.github/AGENTS.MD`
- **Evolution Philosophy**: `evolution.md`

## Validation Checklist

Before committing SCSS:
- [ ] NO raw CSS properties anywhere
- [ ] NO @extend usage
- [ ] Imports `@import "ontology/index";` first
- [ ] SCSS nesting mirrors HTML DOM
- [ ] Semantic class names (content-focused)
- [ ] Appropriate ontological mixins used
- [ ] Comments explain semantic intent, not visual details

## Automation & Linting

- Run stylelint in CI with shared config
- Fixable issues can be suggested as edits
- Require maintainer approval before committing
- CI should enforce zero raw CSS policy

## Do Not

- Do not copy theme `_sass` files into the subdomain
- Do not override ontological mixins locally
- Do not add visual-only customizations
- Do not break the three-tier architecture (Content → Interface → Engine)
