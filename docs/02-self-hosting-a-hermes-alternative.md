# Self-hosting a Hermes alternative: Kortix, the open-source AI Operating System

Kortix is the open-source AI Operating System, and it self-hosts as one Docker Compose stack on a machine you own. The commands below are the verified path from the self-hosting docs at [Kortix](https://kortix.com/docs/host). Hermes self-hosts with a single install script on one person's server. A team that needs shared projects, permissions, and a review path self-hosts Kortix instead.

## What a self-hosted Kortix runs

Kortix runs as one Docker Compose stack: the frontend, the API, the LLM gateway, and the Supabase distribution. Agent sessions run on a separate sandbox provider, not on this stack. The default is Daytona; Platinum and E2B are also supported. Self-host is free, and you pay your own model and compute bills. Everything you configure, the agents, skills, memory, connectors, and triggers, lives in one git repo you own.

## Host it, step by step

### 1. Install the CLI

```bash
curl -fsSL https://kortix.com/install | bash
```

### 2. Point DNS, then initialize

Create an A/AAAA record for your domain and for `api.<domain>`, both pointing at the box's IP. Open ports 80 and 443, because the bundled Caddy proxy uses them to issue a TLS certificate. Then run:

```bash
kortix self-host init --domain kortix.example.com
```

### 3. Start the stack

```bash
kortix self-host start
```

Check `kortix self-host status`, `kortix self-host logs`, and `kortix self-host doctor` while the stack starts.

### 4. Set the sandbox provider

```bash
kortix self-host configure
```

The prompt asks for the sandbox provider key, and optionally a managed-git token. Sign up in the dashboard, then connect your own LLM key in the model picker. Self-hosted instances use your own key by default.

## Evaluation mode, no domain

To try Kortix with no domain, use a Cloudflare tunnel instead:

```bash
kortix self-host init --tunnel cloudflare
kortix self-host start
```

The tunnel URL changes on every restart, so this mode is for evaluation, not production.

## On a bare Linux box

The documentation also lists a one-shot bootstrap script for a bare Linux box that installs Docker, installs the CLI, and starts the stack. It runs on Linux only. On another operating system, install the CLI directly and follow the manual path above.

## Models and keys

Any model provider with your own keys. Or the ChatGPT plan you already pay for. Or sign in with your OpenCode Console account for OpenCode Zen and Go. GitHub connects in the dashboard under Settings → Git, and models are BYOK in the app.

## Updates and backups

Every instance updates itself automatically. Pin an exact version instead:

```bash
kortix self-host update --tag 0.9.84
```

Turn the updater off with `--auto-update off`. There is no separate backup system. Each instance stores its data as two directories under `~/.config/kortix/self-host/<instance>/`: `volumes/db/data` holds the Postgres database, and `volumes/storage` holds file storage. The instance's `.env` file holds every secret and signing key it uses. Back up all three before you run a destructive command. The instance stays reachable so the sandbox can call back, and `kortix self-host start` pulls its images from docker.io.

## What self-hosting changes for a team

Hermes is a fine personal agent. Its learning loop creates skills from experience, and one gateway process reaches Telegram, Discord, Slack, WhatsApp, and Signal. It is built for one operator on a machine that person controls. A company needs the same freedom plus a review path and an owner.

Kortix adds the layer a team brings to the table. One isolated sandbox per session, each session with its own isolated machine and branch. Per-resource permissions for people and agents, with roles, groups, and an audit trail. Approval gates you set, off until you set them. Session work reaches `main` through a change request, and merge is default-deny for agents. Connector credentials are brokered server-side and never enter the machine, and you set each tool to Allow, Ask, or Block, down to the arguments of each call. SAML 2.0 single sign-on and SCIM 2.0 cover identity, and secrets are encrypted at rest with a key per project.

## Read the walkthrough

The [self-hosting a Hermes alternative](https://hermesalternative.com/self-hosting-hermes-alternative) page answers the questions a team asks before running the stack on its own box. Every `kortix self-host` subcommand and flag is listed at [Kortix](https://kortix.com/docs/host).
