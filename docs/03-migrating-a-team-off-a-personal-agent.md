# Migrating a team off a personal agent to Kortix, the open-source AI Operating System

Kortix is the open-source AI Operating System. Moving a team off a personal agent is not a rewrite. It is a change of where the configuration and the memory live, and who approves a change. Hermes is a strong personal agent, and most of what a team built there still matters.

## What actually moves

Three things change hands in a move from a personal agent setup to a company platform: the prompts and skills, the memory and context, and the connectors. The governance layer goes in last, once the work already runs.

### Prompts and skills

Hermes builds skills from experience and stores them as files, and its [own repository](https://github.com/NousResearch/hermes-agent) describes the learning loop. In Kortix an agent is `agents/<name>.md` (behavior) plus an `agents.<name>` block in `kortix.yaml` (governance). The behavior file is markdown, so a prompt's body moves with edits. The governance block is the new part: which connectors the agent may reach and which secrets it may use.

### Memory and context

Hermes keeps a deepening model of the person it serves, curated across sessions with periodic nudges. Kortix company memory is the living company brain, plain files today, held in the same repo as the agents. That is the shift from one operator's context to shared context: memory becomes something the team reviews and versions rather than something one agent accumulates alone.

### Connectors

Hermes ships 40+ tools behind its own toolset system. Kortix reaches 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL and raw HTTP. Connector credentials are brokered server-side and never enter the machine. Each connector re-points once, and the catalog covers the messaging and work apps a team already runs, so a tool from a personal setup usually has a home in the same list.

## The governance a team gains

This layer is the reason a team makes the move, and it is the part a personal agent was not built for.

- Per-resource permissions for people and agents. Roles, groups, and an audit trail.
- Approval gates you set. Off until you set them.
- Session work reaches `main` through a change request, and merge is default-deny for agents.
- SAML 2.0 single sign-on and SCIM 2.0.
- Secrets are encrypted at rest with a key per project.
- One isolated sandbox per session. Each session has its own isolated machine and branch.

Around those sit the scale and the reach a company needs. Thousands of agents run in parallel on one config, each on its own cloud computer. Agents reach 3,000+ apps in a click, and you set each tool to Allow, Ask, or Block, down to the arguments of each call. An agent can edit its own configuration on its session branch and propose the change, and a person approves it.

## The order to move in

Move prompts and skills first, then connectors, then the governance layer once the work already runs. Start with one job and one team, in one repo you own, then bring the rest. Nothing in the order forces a rewrite, because the behavior file is markdown and the governance block is added beside it.

## What stays with the personal agent

Nothing about the move requires giving Hermes up. It is a fine personal agent: run it on a $5 VPS or a GPU cluster, talk to it from Telegram while it works on a cloud VM, and switch models with `hermes model`. A personal agent and a governed company platform are different jobs, and a person can keep both.

## Read the migration guide

The [migrate from Hermes](https://hermesalternative.com/migrate-from-hermes) page walks the same move with short answers on what carries over, where the memory ends up, and what to move first. For the platform detail behind it, the docs at [Kortix](https://kortix.com/docs) cover the agent file, `kortix.yaml`, and the change-request loop.
