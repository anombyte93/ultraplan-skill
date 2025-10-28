# UltraPlan Skill for Claude Code

> Expert-level feature planning workflow with integrated research (Context7 + Perplexity)

Transform vague feature requests into comprehensive, research-backed implementation plans with automated Context7 documentation lookup and Perplexity industry research.

## What It Does

UltraPlan is a systematic planning workflow that:

1. **Researches** official documentation (Context7) and industry best practices (Perplexity)
2. **Analyzes** your project structure and existing patterns
3. **Creates** comprehensive planning documents with user stories, acceptance criteria, and task breakdowns
4. **Clarifies** requirements through interactive questions
5. **Implements** features following the approved plan with incremental testing

## Features

- 🔍 **Automated Research** - Context7 for official docs, Perplexity for FAANG patterns and community practices
- 📋 **Comprehensive Planning** - Requirements, user stories, implementation approaches, risk assessment
- 🤔 **Interactive Clarification** - Smart questions based on feature complexity
- ✅ **Task Breakdown** - Detailed, actionable tasks with time estimates
- 📝 **Living Documentation** - Plans evolve during implementation with notes and learnings
- 🧪 **Testing Strategy** - Includes test planning and Playwright E2E guidance

## Installation

### Prerequisites

1. **Claude Code CLI** - Install from [claude.com/claude-code](https://claude.com/claude-code)
2. **MCP Servers** (required for full functionality):
   - Context7 MCP - Official documentation research
   - Perplexity MCP - Industry research

### Install the Skill

```bash
# Install from GitHub
claude skill install github:anombyte93/ultraplan-skill

# Or install from local directory
git clone https://github.com/anombyte93/ultraplan-skill.git
claude skill install ./ultraplan-skill
```

### Configure MCP Servers

Add to your `.mcp.json` or `~/.claude/mcp.json`:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@context7/mcp-server"]
    },
    "perplexity-free": {
      "command": "npx",
      "args": ["-y", "@perplexity-mcp/server"],
      "env": {
        "PERPLEXITY_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

**Get API Keys:**
- **Context7:** No API key needed (uses npx)
- **Perplexity:** Get from [perplexity.ai/settings/api](https://www.perplexity.ai/settings/api)

## Usage

### Basic Usage

```bash
# From Claude Code
/ultraplan Build a user authentication system with OAuth
```

### Detailed Example

```bash
/ultraplan Build a real-time collaborative editing feature with conflict resolution using operational transforms. Should integrate with our existing WebSocket infrastructure and support 10+ concurrent users per document.
```

### What Happens Next

1. **Planning Mode Activates** - Claude enters planning mode
2. **Research Phase** - Queries Context7 and Perplexity for best practices
3. **Project Analysis** - Examines your codebase structure
4. **Document Creation** - Creates comprehensive plan in `.taskmaster/docs/plans/pending/`
5. **Clarifying Questions** - Asks 3-4 questions about scope, approach, timeline, testing
6. **Approval** - Asks if you're ready to implement
7. **Implementation** - Creates TodoWrite checklist and begins coding

## Planning Document Structure

Plans are saved in `.taskmaster/docs/plans/`:

```
.taskmaster/docs/plans/
├── pending/
│   └── user-auth-plan-2025-10-29.md      # Active planning
└── complete/
    └── user-auth-plan-2025-10-29.md      # Implemented features
```

Each plan includes:

- **Executive Summary** - Quick overview
- **Requirements** - Functional and non-functional requirements
- **User Stories** - With acceptance criteria
- **Research Findings** - Industry standards, community practices, official docs
- **Implementation Approaches** - Multiple options with pros/cons
- **Tools & Resources** - Libraries, frameworks, project utilities
- **Success Criteria** - Definition of done and quality gates
- **Risk Assessment** - Potential issues and mitigation strategies
- **Task Breakdown** - Detailed, actionable tasks with estimates
- **References** - All research sources

## Configuration

### Project-Specific Plans Directory

By default, plans are saved to `.taskmaster/docs/plans/`. To customize:

Edit `skill.json` in your local skill installation:

```json
{
  "configuration": {
    "default_plan_directory": "docs/planning"
  }
}
```

### Customize Question Flow

The skill asks 3-4 questions by default. You can modify `main.md` to add custom questions for your team's workflow.

## Examples

### Example 1: Web Feature

```bash
/ultraplan Add infinite scroll to the product listing page with lazy loading and skeleton states
```

**Result:**
- Researches React infinite scroll patterns
- Checks Intersection Observer API docs
- Finds FAANG performance best practices
- Creates plan with performance metrics
- Asks about pagination strategy and UX preferences

### Example 2: Backend API

```bash
/ultraplan Implement rate limiting middleware with Redis for our Express API
```

**Result:**
- Researches Express middleware patterns
- Checks Redis rate limiting strategies
- Finds industry standard rate limit algorithms (token bucket, sliding window)
- Creates plan with scalability considerations
- Asks about rate limit thresholds and error responses

### Example 3: CLI Tool

```bash
/ultraplan Build a CLI tool for database migrations with rollback support
```

**Result:**
- Researches migration tool patterns (Alembic, Flyway, etc.)
- Checks Node.js CLI best practices
- Finds database versioning strategies
- Creates plan with migration file structure
- Asks about database targets and rollback scenarios

## Tips for Best Results

### ✅ Good Feature Requests

- **Specific:** "Add JWT authentication with refresh tokens"
- **Contextual:** "...integrate with our existing user service"
- **Scoped:** "...support email/password and Google OAuth"
- **Constrained:** "...must work with PostgreSQL user table"

### ❌ Vague Feature Requests

- ~~"Add authentication"~~ → Too broad
- ~~"Make it faster"~~ → No measurable goal
- ~~"Fix the bug"~~ → Not a feature plan

### Pro Tips

1. **Mention existing patterns** - "...following our repository pattern"
2. **State priorities** - "...prioritize developer experience over performance"
3. **Include constraints** - "...must not require database migration"
4. **Specify scale** - "...support 1000 concurrent users"

## Troubleshooting

### "Context7 MCP not found"

Install Context7 MCP:

```bash
# Add to .mcp.json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@context7/mcp-server"]
    }
  }
}
```

### "Perplexity MCP not configured"

Get a Perplexity API key and add to `.mcp.json`:

```json
{
  "mcpServers": {
    "perplexity-free": {
      "command": "npx",
      "args": ["-y", "@perplexity-mcp/server"],
      "env": {
        "PERPLEXITY_API_KEY": "pplx-xxxxx"
      }
    }
  }
}
```

### "Planning directory not found"

UltraPlan will create `.taskmaster/docs/plans/` automatically. If you prefer a different location, update `skill.json`.

### Research queries failing

Check your MCP server logs:

```bash
# In Claude Code, enable MCP debug mode
claude --mcp-debug
```

## How It Works

### Research Strategy

**Context7 Queries:**
- Identifies libraries/frameworks in feature request
- Resolves library IDs automatically
- Fetches official documentation with focused topics
- Extracts code examples and best practices

**Perplexity Queries (3 queries):**
1. **Industry Standards** - FAANG companies, production patterns
2. **Community Practices** - GitHub trends, popular libraries
3. **Current Research** - 2024-2025 papers, conference talks

### Decision Framework

The skill uses research findings to:
- Recommend proven patterns over experimental approaches
- Suggest libraries with strong community adoption
- Identify performance bottlenecks before coding
- Propose test strategies based on feature complexity

## Comparison

### vs Traditional Planning

| Traditional | UltraPlan |
|-------------|-----------|
| Manual research | Automated Context7 + Perplexity |
| Static documents | Living docs with implementation notes |
| Vague requirements | User stories with acceptance criteria |
| Unknown risks | Research-backed risk assessment |
| No task breakdown | Detailed, actionable tasks |

### vs Other Skills

- **More comprehensive** than simple task breakdown
- **Research-backed** unlike template-based planning
- **Interactive** with clarifying questions
- **Integrated** with TaskMaster workflow

## Contributing

Found a bug or have a suggestion?

1. Open an issue: https://github.com/anombyte93/ultraplan-skill/issues
2. Submit a PR with improvements
3. Share your experience in discussions

## License

MIT License - see LICENSE file

## Credits

Created by [@anombyte93](https://github.com/anombyte93)

Powered by:
- [Claude Code](https://claude.com/claude-code)
- [Context7 MCP](https://github.com/context7)
- [Perplexity AI](https://www.perplexity.ai/)

## Changelog

### v1.0.0 (2025-10-29)

- Initial release
- Context7 and Perplexity integration
- Interactive clarification questions
- Comprehensive planning documents
- Task breakdown with time estimates
- Living documentation during implementation

---

**Ready to plan like an expert?**

```bash
claude skill install github:anombyte93/ultraplan-skill
cd your-project
/ultraplan Build an amazing feature
```
