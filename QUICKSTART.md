# UltraPlan Skill - Quick Start Guide

Get up and running with UltraPlan in 5 minutes.

## Step 1: Install the Skill

```bash
# Clone to your Claude skills directory
cd ~/.claude/skills
git clone https://github.com/anombyte93/ultraplan-skill.git

# Or use Claude CLI (if available)
claude skill install github:anombyte93/ultraplan-skill
```

## Step 2: Verify MCP Servers

Check that required MCP servers are configured in your `.mcp.json`:

```bash
# Check your MCP configuration
cat .mcp.json  # or ~/.claude/mcp.json
```

You should see:

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
        "PERPLEXITY_API_KEY": "pplx-your-key-here"
      }
    }
  }
}
```

**Don't have these?** Add them now:

```bash
# Get Perplexity API key
# Visit: https://www.perplexity.ai/settings/api

# Add to your .mcp.json
```

## Step 3: Test with a Simple Feature

In your project directory:

```bash
# Launch Claude Code
claude

# Try ultraplan with a simple feature
/ultraplan Add a user profile page with avatar upload
```

## Step 4: Verify It Works

You should see:

1. ✅ Planning mode activated
2. ✅ Context7 researching documentation
3. ✅ Perplexity querying industry best practices
4. ✅ Planning document created in `.taskmaster/docs/plans/pending/`
5. ✅ Interactive questions appear
6. ✅ Ready to implement after approval

## Expected Output Example

```
Planning mode activated.

## Phase 1: Context Gathering

Researching official documentation via Context7...
- Querying for: file upload libraries
- Querying for: user profile patterns
- Querying for: avatar storage solutions

Researching industry best practices via Perplexity...
- Query 1: Industry standards for profile pages
- Query 2: Community best practices for avatar uploads
- Query 3: Current research on image optimization

## Phase 2: Document Creation

Creating comprehensive plan at:
.taskmaster/docs/plans/pending/user-profile-page-plan-2025-10-29.md

Plan created with:
- 3 functional requirements
- 2 non-functional requirements
- 5 user stories with acceptance criteria
- Research findings from 8 sources
- 2 implementation approaches
- Detailed task breakdown (12 tasks, ~8 hours estimated)

## Phase 3: Interactive Clarification

I have a few questions to refine the plan...

[Questions appear here]
```

## Step 5: Explore the Plan

```bash
# View the generated plan
cat .taskmaster/docs/plans/pending/user-profile-page-plan-2025-10-29.md
```

## Common Issues

### Issue: "Context7 MCP not found"

**Solution:** Add to `.mcp.json`:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@context7/mcp-server"]
    }
  }
}
```

### Issue: "Perplexity queries failing"

**Solution:**

1. Check API key is valid
2. Verify key has credits
3. Check `.mcp.json` env variable is set correctly

```bash
# Test Perplexity directly
npx @perplexity-mcp/server
```

### Issue: "Skill not found"

**Solution:**

1. Verify installation:
```bash
ls ~/.claude/skills/ultraplan-skill/
# Should show: skill.json, main.md, README.md
```

2. Restart Claude Code:
```bash
# Exit and restart
/exit
claude
```

3. List available skills:
```bash
/skills
```

### Issue: "Planning directory not created"

**Solution:** UltraPlan creates `.taskmaster/docs/plans/` automatically. If it fails:

```bash
# Create manually
mkdir -p .taskmaster/docs/plans/{pending,complete}
```

## Next Steps

### Try More Complex Features

```bash
# Web feature with performance constraints
/ultraplan Build infinite scroll with virtualization for 10k+ items

# Backend API with scale requirements
/ultraplan Create rate-limited REST API supporting 1000 req/sec

# CLI tool with specific constraints
/ultraplan Build database migration CLI with zero-downtime rollbacks
```

### Customize the Workflow

1. Edit `~/.claude/skills/ultraplan-skill/main.md`
2. Modify question templates
3. Adjust research query prompts
4. Change planning document template

### Share Your Experience

- ⭐ Star the repo: https://github.com/anombyte93/ultraplan-skill
- 🐛 Report issues: https://github.com/anombyte93/ultraplan-skill/issues
- 💬 Share feedback: GitHub Discussions

## What's Next?

After ultraplan creates your plan:

1. **Review the plan** - Check research findings and approaches
2. **Answer questions** - Clarify scope, approach, timeline
3. **Approve implementation** - Say "Yes, start now"
4. **Watch it code** - UltraPlan creates TodoWrite checklist and implements
5. **Test incrementally** - E2E tests run in --headed mode for visibility

## Tips for Power Users

### Use with TaskMaster

```bash
# Let ultraplan create the plan
/ultraplan Build feature X

# After approval, ultraplan will:
# 1. Create TodoWrite with tasks
# 2. Move plan to /complete/
# 3. Start implementation
# 4. Update plan with implementation notes
```

### Customize for Your Team

Create a project-specific `.ultraplan.config.json`:

```json
{
  "default_priorities": ["performance", "security"],
  "required_sections": ["accessibility", "monitoring"],
  "test_coverage_target": 95,
  "complexity_threshold": 7
}
```

(Feature coming in v1.1)

### Chain Multiple Plans

```bash
# Plan the whole epic
/ultraplan Build user authentication system

# After approval, plan next feature
/ultraplan Add role-based access control

# Keep going
/ultraplan Implement audit logging
```

---

**Ready?**

```bash
/ultraplan Build your next amazing feature
```

🚀 Happy planning!
