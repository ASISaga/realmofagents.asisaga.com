# Agent Ecosystem - Realm of Agents Subdomain

This directory contains agent-specific guidance and workflows for the Realm of Agents subdomain.

## Agent Files

### Prompts (`.github/prompts/`)

These are MCP-compatible prompts that define how specialized agents should operate:

- **subdomain-evolution-agent.prompt.md** - Local intelligence for identifying semantic gaps and creating ontological propositions to the theme repository

### Future Agents

As the subdomain evolves, additional agent prompts may be added:

- **scss-refactor-agent.prompt.md** - Migration specialist for converting legacy CSS to ontological mixins
- **accessibility-agent.prompt.md** - WCAG AA compliance checker and remediation specialist
- **content-agent.prompt.md** - Content structure and semantic HTML validator

## How Agents Work

### Subdomain Evolution Agent

**Purpose**: Maintains semantic consistency while facilitating ontology evolution

**When to Use**:
- Implementing new SCSS for pages/components
- Discovering patterns not covered by existing ontology
- Need to propose new ontological variants to theme

**How to Invoke**:
- Copilot will automatically consult this agent when working on SCSS
- Manual invocation via MCP tools when proposing changes to theme

**Key Responsibilities**:
1. Ensure zero raw CSS in subdomain SCSS
2. Map HTML classes to ontological roles
3. Identify genuine semantic gaps
4. Create well-formed ontological propositions
5. Implement approved variants locally

### Integration with Theme

All agents in this subdomain coordinate with the theme repository agents:

- **Theme Genome Agent** - Reviews ontological propositions, maintains semantic purity
- **SCSS Refactor Agent** - Helps migrate legacy patterns to ontology
- **HTML Template Agent** - Ensures semantic HTML structure

## Agent Workflow Example

### Scenario: Adding New Agent Showcase Page

1. **Content Creation** (Human/Copilot)
   - Write semantic HTML with meaningful class names
   - Example: `.agent-showcase`, `.capability-grid`, `.demo-section`

2. **SCSS Implementation** (Subdomain Evolution Agent)
   - Create `_sass/pages/_agent-showcase.scss`
   - Import ontology: `@import "ontology/index";`
   - Map classes to ontological roles:
     ```scss
     .agent-showcase {
       @include genesis-environment('distributed');
       
       .capability-grid {
         @include genesis-environment('manifest');
         
         .capability-card {
           @include genesis-entity('primary');
         }
       }
     }
     ```

3. **Gap Identification** (Subdomain Evolution Agent)
   - Notice: need to represent "agent status" (active/idle/training)
   - Check existing `genesis-state` variants
   - Determine: current states don't fit agent operational context
   - **Gap identified**: Need agent-specific operational states

4. **Proposition Creation** (Subdomain Evolution Agent)
   - Draft ontological proposition using template
   - Document use cases, universal applicability
   - Submit PR to theme repository

5. **Theme Review** (Theme Genome Agent)
   - Evaluates semantic purity
   - Checks for redundancy
   - Approves or suggests alternatives

6. **Implementation** (Subdomain Evolution Agent)
   - Pull approved changes from theme
   - Implement new variant in subdomain SCSS
   - Test and validate
   - Document usage

## Resources

- **Theme Agent Ecosystem**: https://github.com/ASISaga/theme.asisaga.com/.github/AGENTS.MD
- **Local Instructions**: `../.github/instructions/`
- **Ontology Reference**: Theme `_sass/ontology/INTEGRATION-GUIDE.md`

## Contributing

When adding new agent prompts:

1. Follow the MCP prompt format (YAML frontmatter + markdown)
2. Define clear responsibilities and scope
3. Provide examples specific to Realm of Agents context
4. Link to relevant theme agent documentation
5. Include quality gates and validation checklists
