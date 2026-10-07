---
name: OpenCode
description: Configure and use OpenCode agents, commands, tools, skills, providers, permissions, and session workflows
---

# OpenCode

Use this skill when configuring OpenCode or explaining how its agents, tools,
skills, providers, permissions, integrations, and session workflows work.

## Workflow

1. Identify the OpenCode feature involved and read the matching reference below.
2. Check whether the setting belongs in project configuration, global configuration,
	 an agent definition, a command, or a skill.
3. Apply the smallest configuration or documentation change that satisfies the task.
4. Verify the resulting paths, frontmatter, JSON/JSONC structure, permissions, and
	 provider availability as applicable.
5. Consult related references when the feature crosses configuration boundaries.

## Reference Map

Use these references as the source of truth for the corresponding OpenCode areas:

- [Agents](references/agents.md): create reusable primary and subagent definitions.
- [Attachments](references/attachments.md): attach local files and use them in prompts.
- [Commands](references/commands.md): define reusable TUI slash commands and arguments.
- [Compaction](references/compaction.md): understand context compaction in long sessions.
- [Formatters](references/formatters.md): configure formatting after file edits.
- [Instructions](references/instructions.md): add persistent project guidance with `AGENTS.md`.
- [MCP servers](references/mcp-servers.md): configure Model Context Protocol servers and connections.
- [Models](references/models.md): select models available through providers and configuration.
- [Network](references/network.md): configure proxy variables and loopback exclusions.
- [Permissions](references/permissions.md): define ordered per-agent action and resource rules.
- [Plugins](references/plugins.md): configure published, scoped, versioned, and local plugins.
- [Policies](references/policies.md): configure global binary restrictions that tighten permissions.
- [Providers](references/providers.md): connect provider accounts and select their models.
- [References](references/references.md): expose named directories outside the current project.
- [Snapshots](references/snapshots.md): undo recent conversation and file changes together.
- [Skills](references/skills.md): create, discover, configure, and load reusable skills.
- [Themes](references/themes.md): configure the terminal UI theme.
- [Tools](references/tools.md): choose and invoke tools for file, shell, and code tasks.
- [Warming](references/warming.md): preserve provider-side prompt caches during pauses.
- [Websearch](references/websearch.md): search current information and include source links.

## Configuration Boundaries

- Put project-specific commands, agents, skills, plugins, MCP servers, references,
	and instructions in the project configuration or `.opencode/` directories.
- Put user-wide commands, agents, skills, and themes in the global configuration
	directories described by the relevant reference.
- Treat permissions and policies as separate controls: permissions govern an
	agent's available actions, while policies only tighten what is allowed.
- Keep credentials out of project files and use the provider connection flow.

## Skills

For reusable task guidance, create `.opencode/skills/<skill-id>/SKILL.md` with
frontmatter containing a clear `description`. Keep supporting scripts,
references, and templates beside the skill file, and use relative paths from
that directory. Use a lowercase kebab-case ID and avoid duplicate IDs unless
the later source is intentionally overriding the earlier one.
