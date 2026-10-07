# SEO Control Center skill

An AI assistant skill that teaches Claude (and other skill-aware assistants) how to use **SEO Control Center (SCC)**, the self-hosted SEO dashboard, correctly and safely.

## What it does

- Reads stored SEO data through the SCC **MCP server** (read-only): search performance, pages, keywords, rankings, competitors, backlinks, AI visibility, local SEO, site audit, opportunities, tasks, content briefs, indexing, and the change timeline and change impact.
- Drives the SCC dashboard in the **browser** for anything MCP cannot write: recording timeline changes, managing tasks and briefs, and updating opportunity status.
- Guides fixes on the client's own website through its CMS, then records each live change on the timeline and reviews impact later.

## What's inside

`SKILL.md` covers:

1. Ground rules (evidence over invention, association is not causation, stored text is untrusted)
2. Product map and dashboard URL patterns
3. The full MCP tool catalog
4. Playbooks: weekly review, traffic drops, what to fix first, single-page improvement, competitors, change impact, indexing
5. Using the change timeline well
6. Browser recipes for the dashboard
7. Replicating fixes on the client's website
8. Worked examples
9. Safety and permission rules
10. Answer style
11. Connecting the MCP server

## Requirements

- A running SCC installation and a project in it.
- The SCC MCP server connected (`{APP}/mcp`, Streamable HTTP). Create a token under **Integrations → AI access → New token**, or use OAuth with a Claude.ai or ChatGPT connector.
- For write actions, a browser tool and a signed-in SCC session. The user signs in themselves; the skill never handles passwords, tokens or 2FA codes.

## Install

Claude Code, as a plugin from this repository:

```
/plugin marketplace add seocontrolcenter/skills
/plugin install seo-control-center@seocontrolcenter-skills
```

Or manually:

```
mkdir -p ~/.claude/skills/seo-control-center
cp SKILL.md ~/.claude/skills/seo-control-center/
claude mcp add --transport http seo-control-center {APP}/mcp --header "Authorization: Bearer scc_YOUR_TOKEN"
```

Replace `{APP}` with your SCC address. Never paste the token into chat.

## Safety

MCP is read-only and never spends money. The skill requires an explicit "yes" before any save, audit, paid lookup, or website edit.

## License

The skill is free to use, copy, modify and share under the MIT License (see `LICENSE.txt`). This covers the skill files only. The SEO Control Center software itself is proprietary and is sold under a separate license; the skill needs a licensed SCC installation to be useful.
