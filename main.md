# UltraPlan: Expert-Level Feature Planning & Implementation

**Feature Request:** $ARGUMENTS

---

## Pre-Flight Check

Before proceeding, verify required MCP servers are configured:

1. **Context7 MCP** - For official documentation research
2. **Perplexity MCP** - For industry standards and best practices

If either is missing, the skill will provide guidance on setup.

**ENABLE PLANNING MODE NOW**

---

## Phase 1: Context Gathering (Agentic RAG Approach)

### Step 1.1: Official Documentation Research (Context7)

Use the `mcp__context7__resolve-library-id` and `mcp__context7__get-library-docs` tools to research relevant libraries, frameworks, and tools for: **$ARGUMENTS**

**What to extract:**
- Core APIs and methods
- Best practices from official docs
- Common patterns and examples
- Type definitions and interfaces
- Gotchas and common pitfalls

**Context7 Query Strategy:**
1. Identify key libraries/frameworks mentioned in the feature request
2. For each library, resolve the library ID
3. Fetch documentation with focused topics (e.g., "authentication", "state management")
4. Extract actionable patterns and code examples

### Step 1.2: Industry Standards Research (Perplexity)

Use the `mcp__perplexity-free__search` tool with `mode: "pro"` to research the "Big 4" areas for: **$ARGUMENTS**

**Query 1: Industry Standards & FAANG Patterns**
```
What are the current industry standards, widely-adopted patterns, and production best practices for implementing [feature from $ARGUMENTS] in 2025? Include examples from FAANG companies and leading tech organizations. Focus on: architecture patterns, scalability considerations, and proven production implementations.
```

**Query 2: Community Best Practices & Open Source**
```
What are the community-recommended approaches, popular open-source implementations, and developer best practices for [feature from $ARGUMENTS] in 2025? Include GitHub trends, Stack Overflow insights, npm/PyPI statistics, and developer surveys. Highlight production-ready libraries and frameworks.
```

**Query 3: Current Research & Performance Studies**
```
What are the latest academic research papers, performance studies, and technical analyses related to [feature from $ARGUMENTS]? Include 2024-2025 publications, recent conference talks (React Conf, Node.js Interactive, PyCon), and benchmark comparisons. Focus on measurable performance insights and emerging best practices.
```

### Step 1.3: Project Context Analysis

Analyze the current project structure to understand integration points:

**Use Glob and Read tools to examine:**
- `/scripts/` - Available automation tools
- `.taskmaster/` - Task management configuration
- `.claude/` - Available skills and commands
- `package.json` or `requirements.txt` - Technology stack
- Source code structure - Architecture patterns

**Document:**
- Existing patterns to follow
- Available utilities to leverage
- Constraints to respect
- Integration points

---

## Phase 2: Planning Document Creation

Create a comprehensive planning document at:
**`.taskmaster/docs/plans/pending/[feature-name]-plan-[YYYY-MM-DD].md`**

If `.taskmaster/docs/plans/` doesn't exist, create it first.

### Document Template:

Use the following structure (adapt based on feature complexity):

\`\`\`markdown
---
title: [Feature Name] Implementation Plan
created: [YYYY-MM-DD HH:MM:SS]
last_modified: [YYYY-MM-DD HH:MM:SS]
status: pending
confidence_level: [high/medium/low - to be updated after user questions]
estimated_complexity: [1-10 scale]
---

# [Feature Name] Implementation Plan

## Executive Summary

[2-3 sentence overview of what we're building and why]

## Requirements

### Functional Requirements
1. [REQ-001] User must be able to...
2. [REQ-002] System must support...
3. [REQ-003] Feature should provide...

### Non-Functional Requirements
1. [NFR-001] Performance: [specific metrics]
2. [NFR-002] Security: [specific requirements]
3. [NFR-003] Scalability: [specific targets]
4. [NFR-004] Accessibility: [WCAG compliance level if applicable]

## User Stories

### Primary User Stories
- **[US-001]** As a [user type], I want to [action], so that [benefit]
  - Acceptance Criteria:
    - [ ] Given [context], when [action], then [expected result]
    - [ ] Given [context], when [action], then [expected result]

- **[US-002]** As a [user type], I want to [action], so that [benefit]
  - Acceptance Criteria:
    - [ ] ...

### Edge Case User Stories
- **[US-E01]** As a [user type], when [edge case scenario], I need [behavior]

## Research Findings

### Industry Standards (FAANG-Level)
[Summarize Perplexity Query 1 results]

- **Pattern 1:** [Description]
  - Used by: [Companies/Projects]
  - Pros: [List]
  - Cons: [List]
  - Source: [Link]

### Community Best Practices
[Summarize Perplexity Query 2 results]

- **Approach 1:** [Description]
  - Popularity: [GitHub stars, npm downloads, etc.]
  - Community feedback: [Summary]
  - Source: [Link]

### Official Documentation Insights (Context7)
[Summarize Context7 results]

- **Library/Framework:** [Name]
  - Recommended pattern: [Code example]
  - Key APIs: [List with descriptions]
  - Gotchas: [Common pitfalls]

### Current Research
[Summarize Perplexity Query 3 results]

- **Study/Paper:** [Title]
  - Key finding: [Summary]
  - Applicability: [How it relates to our feature]
  - Source: [Link]

## Implementation Approaches

### Approach A: [Name] (Recommended)
**Complexity:** [Low/Medium/High]
**Timeline:** [Estimate]
**Risk:** [Low/Medium/High]

#### Architecture Overview
\`\`\`
[ASCII diagram or description of system architecture]
\`\`\`

#### Key Components
1. **Component 1:** [Name]
   - Responsibility: [What it does]
   - Dependencies: [What it needs]
   - Interface: [Key methods/props]

#### Expert Implementation Pattern
[Include actual code example showing expert-level structure from research]

\`\`\`typescript
// Example: Production-ready pattern from research

interface FeatureConfig {
  // Type-safe configuration based on Context7 docs
}

class FeatureImplementation {
  // Pattern from FAANG companies (if found in research)
  constructor(private readonly deps: Dependencies) {}

  async execute(): Promise<Result> {
    // Implementation with error handling from best practices
    try {
      // Step 1: Validate inputs
      // Step 2: Process
      // Step 3: Return result
    } catch (error) {
      // Error handling pattern from research
    }
  }
}
\`\`\`

#### Pros & Cons
**Pros:**
- [List advantages based on research]

**Cons:**
- [List disadvantages based on research]

### Approach B: [Alternative Name]
[Similar structure - only if multiple viable approaches exist]

## Tools & Resources

### From Current Project
[Based on Step 1.3 project analysis]

- **Tool:** \`scripts/[tool-name].sh\`
  - Purpose: [What it does]
  - Usage: [How we'll use it]

- **Available Agent:** [If applicable]
  - Purpose: [What it does]
  - Usage: [How we'll use it]

### External Tools/Libraries
[Based on Context7 and Perplexity research]

- **Library:** [name@version]
  - Purpose: [Why we need it]
  - Installation: \`npm install [name]\` or \`pip install [name]\`
  - Documentation: [link]
  - Justification: [Why this library - from research]

### Testing Strategy
- **Framework:** [Based on project's existing setup]
- **Test files:** \`tests/[feature]/**.spec.ts\`
- **Coverage target:** [percentage based on project standards]
- **E2E testing:** Playwright with --headed mode for visible validation

## Success Criteria

### Definition of Done
- [ ] All functional requirements met (REQ-001 through REQ-N)
- [ ] All user stories implemented with passing acceptance criteria
- [ ] Unit tests written and passing (coverage target met)
- [ ] E2E tests written and passing (visible in --headed mode)
- [ ] Accessibility audit passed (if applicable)
- [ ] Performance benchmarks met (specific metrics)
- [ ] Documentation updated
- [ ] Code reviewed and approved

### Quality Gates
1. **Code Quality:** Linter passes with zero errors
2. **Type Safety:** Strict mode (if TypeScript/typed language)
3. **Test Coverage:** [percentage] for critical paths
4. **Performance:** [Specific metrics from research]
5. **Accessibility:** [Standard if UI feature]

## Risk Assessment

### High-Risk Areas
1. **Risk:** [Based on research findings]
   - Likelihood: [Low/Medium/High]
   - Impact: [Low/Medium/High]
   - Mitigation: [Strategy from best practices]

### Dependencies & Blockers
1. **Dependency:** [What we need]
   - Status: [Available/Pending/Blocked]
   - Owner: [Who's responsible]

## Task Breakdown

### Phase 1: Setup & Infrastructure
- [ ] **Task 1.1:** Initialize project structure
  - Subtask: [Specific action]
  - Estimated time: [hours]

### Phase 2: Core Implementation
- [ ] **Task 2.1:** Implement [Component 1]
  - Subtask: [Specific action]
  - Estimated time: [hours]

### Phase 3: Testing & Validation
- [ ] **Task 3.1:** Write unit tests
  - Subtask: [Specific action]
  - Estimated time: [hours]

- [ ] **Task 3.2:** Write E2E tests (Playwright --headed)
  - Subtask: [Specific action]
  - Estimated time: [hours]

### Phase 4: Documentation & Deployment
- [ ] **Task 4.1:** Update documentation
- [ ] **Task 4.2:** Deploy to staging
- [ ] **Task 4.3:** Validate and monitor

## Questions for User

[This section will be populated by AskUserQuestion tool]

## Implementation Notes

[This section will be populated during implementation]

## References

### Documentation (Context7)
- [List Context7 sources]

### Research Papers & Articles (Perplexity)
- [List Perplexity sources]

### Code Examples
- [GitHub repos, CodeSandbox links from research]

---

**Status:** Pending User Approval
**Next Step:** Interactive clarification session
\`\`\`

---

## Phase 3: Interactive Clarification

Use the **AskUserQuestion** tool to ask 3-4 critical questions (max 4 questions per call):

### Question Set 1: Scope & Approach

\`\`\`javascript
{
  questions: [
    {
      question: "What is the primary use case you want to optimize for?",
      header: "Priority",
      options: [
        { label: "Performance", description: "Fastest execution, aggressive optimization" },
        { label: "Developer Experience", description: "Easy to use, intuitive API" },
        { label: "Flexibility", description: "Highly configurable, extensible" },
        { label: "Simplicity", description: "Minimal complexity, straightforward" }
      ],
      multiSelect: false
    },
    {
      question: "Which implementation approach do you prefer?",
      header: "Approach",
      options: [
        { label: "Approach A", description: "[Summary from planning doc]" },
        { label: "Approach B", description: "[Alternative if exists]" },
        { label: "Hybrid", description: "Combination of both approaches" }
      ],
      multiSelect: false
    },
    {
      question: "What's your preferred implementation timeline?",
      header: "Timeline",
      options: [
        { label: "MVP Fast", description: "Core features only, 2-4 hours" },
        { label: "Balanced", description: "Full features, 1-2 days" },
        { label: "Production Ready", description: "Enterprise-grade, 3-5 days" }
      ],
      multiSelect: false
    },
    {
      question: "What testing level do you want?",
      header: "Testing",
      options: [
        { label: "Unit Only", description: "Fast component-level tests" },
        { label: "Integration", description: "Unit + API integration tests" },
        { label: "Full E2E", description: "Unit + Integration + Playwright" },
        { label: "TDD", description: "Write tests first, implement after" }
      ],
      multiSelect: false
    }
  ]
}
\`\`\`

### Question Set 2 (if needed): Technical Details

Based on feature complexity, ask additional questions about:
- Error handling preferences
- Accessibility requirements
- Dependency constraints
- Security considerations

**IMPORTANT:** AskUserQuestion tool accepts max 4 questions per call. If you need more than 4 questions, make multiple calls.

---

## Phase 4: Finalization & Confidence Check

After user answers:

1. **Update the planning document** with user decisions in "Questions for User" section
2. **Adjust implementation approach** based on answers
3. **Refine task breakdown** to match chosen approach and timeline
4. **Update confidence level** in frontmatter:
   - high: Clear requirements, well-researched, proven patterns
   - medium: Some unknowns, moderate complexity
   - low: High uncertainty, experimental approach

5. **Final confirmation question:**

\`\`\`javascript
{
  questions: [
    {
      question: "Are you ready to proceed with implementation?",
      header: "Ready?",
      options: [
        { label: "Yes, start now", description: "Begin implementation immediately" },
        { label: "Revise plan", description: "I want to adjust something first" },
        { label: "More research", description: "Need additional context" }
      ],
      multiSelect: false
    }
  ]
}
\`\`\`

---

## Phase 5: Implementation

If user selects "Yes, start now":

1. **Move document** from `.taskmaster/docs/plans/pending/` to `.taskmaster/docs/plans/complete/`
2. **Update status** in document frontmatter to `status: in-progress`
3. **Create TodoWrite** with tasks from the "Task Breakdown" section
4. **Begin implementation** following the approved plan:
   - Mark first task as `in_progress`
   - Implement according to research-backed patterns
   - Write tests incrementally (use --headed mode for E2E Playwright tests)
   - Update planning document's "Implementation Notes" section with:
     - Actual approaches used
     - Deviations from plan (with reasons)
     - Challenges encountered
     - Solutions found
   - Mark tasks as `completed` when done
   - Move to next task
5. **Never commit untested code** - all tests must pass before committing

---

## Phase 6: Continuous Documentation

During implementation:
- **Update "Implementation Notes"** section regularly
- **Update "last_modified"** timestamp
- **Track progress** by checking off tasks in breakdown
- **Document deviations** from plan with rationale
- **Add learnings** for future reference

---

## Error Handling

### If Context7 MCP is unavailable:
Provide setup instructions:
\`\`\`json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@context7/mcp-server"]
    }
  }
}
\`\`\`

### If Perplexity MCP is unavailable:
Provide setup instructions for perplexity-free MCP server with cookie authentication.

### If planning directory doesn't exist:
Create `.taskmaster/docs/plans/pending/` and `.taskmaster/docs/plans/complete/` directories automatically.

---

## Tips for Best Results

1. **Be specific** in your feature request - include use cases, constraints, technologies
2. **Mention existing patterns** if you want consistency with current codebase
3. **State priorities** upfront (performance vs simplicity vs features)
4. **Include context** about your project type (web app, CLI tool, library, etc.)

## Example Usage

\`\`\`
/ultraplan Build a real-time collaborative editing feature with conflict resolution using operational transforms. Should integrate with our existing WebSocket infrastructure and support 10+ concurrent users per document.
\`\`\`

---

**This is a comprehensive planning workflow. Take time in each phase to ensure the best possible implementation approach.**
