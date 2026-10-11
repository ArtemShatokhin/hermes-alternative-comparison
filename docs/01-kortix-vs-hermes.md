# Kortix vs Hermes: the open-source AI Operating System and the self-hosted personal agent

Kortix is the open-source AI Operating System. Hermes is a self-hosted personal agent with persistent memory, built by Nous Research and released in February 2026. Both are open source, both run on hardware you choose, and both let you bring your own model. The difference is scale: Hermes is built for one operator, and Kortix is built for a team that owns and governs its agents.

## What each one is

Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector in one git repo you own, with the agents working on real cloud computers. Each session runs on its own isolated sandbox and its own branch, and session work reaches `main` through a change request a person approves.

Hermes is a self-improving AI agent from Nous Research with a built-in learning loop. Its [own repository](https://github.com/NousResearch/hermes-agent) describes an agent that creates skills from experience, keeps agent-curated memory with periodic nudges, and searches its own past sessions for context. It is a personal agent: one operator, a private and always-on companion on a machine that person controls.

## Feature by feature

| Dimension | Kortix | Hermes |
| --- | --- | --- |
| Open source | Yes. Read it, fork it, audit it. | Yes, under the MIT license. |
| Designed for | Teams and companies. | One person. |
| Where the config lives | A git repo you own. | The machine you run it on. |
| Isolation | One isolated sandbox per session. | A Docker, SSH, or Modal backend. |
| Tool control | Each tool set to Allow, Ask, or Block. | Command approval and DM pairing. |
| Review and history | Work lands through a change request a person approves. | Personal memory and skills, kept by the operator. |
| Model choice | Any model provider with your own keys. | Any model, switched with one command. |
| Hosting | Kortix Cloud, your VPC, or your own on-prem network. | A $5 VPS, a GPU cluster, or serverless. |

Hermes facts come from its [own repository](https://github.com/NousResearch/hermes-agent) and [site](https://www.hermes-agent.org), checked October 2026. Kortix facts come from the [Kortix documentation](https://kortix.com/docs).

## Where Hermes fits

Hermes is the right answer when the user is one person. It reaches that person across Telegram, Discord, Slack, WhatsApp, Signal, email, and the CLI from a single gateway process, runs its agents on seven terminal backends that include Docker, SSH, Singularity, Modal, Daytona, and Vercel Sandbox, and switches models with `hermes model` and no code changes. It runs on a $5 VPS, a GPU cluster, or serverless infrastructure that costs little when idle. For a private, always-on agent on your own machine, Hermes is built for exactly that.

## Where Kortix takes over

The shape changes the moment more than one person steers the agents. A team has to answer questions a personal agent leaves to its operator. Who may reach which tool? Kortix sets each tool to Allow, Ask, or Block, and an Ask holds a call until a person approves it. Where does the work run? One isolated sandbox per session, each session with its own isolated machine and branch. What happened, and who signed off? Session work reaches `main` through a change request a person approves, and around it sit per-resource permissions for people and agents, with roles, groups, and an audit trail. Who is allowed in? SAML 2.0 single sign-on and SCIM 2.0.

Kortix also keeps the whole configuration in one place a team owns. Agents, skills, memory, connectors, and triggers are files in a git repo, versioned and diffable. Thousands of agents run in parallel on one config, each on its own cloud computer. An agent can edit its own configuration on its session branch and propose the change, and a person approves it.

## The decision, stated plainly

Choose Hermes when the user is a person: a private agent on their own machine, in their own chat apps, improving its own skills. Choose Kortix when the user is a team or a company: shared projects with roles, scoped tools, isolation per session, and a reviewed history. A person can run Hermes while the team runs Kortix, because the two do not compete for the same seat.

Kortix is the open-source platform for the team side. Run it on Kortix Cloud, in your VPC, or on your own on-prem network, and self-host is free.

## Read the full comparison

The [Kortix vs Hermes](https://hermesalternative.com/kortix-vs-hermes) page carries the same head-to-head with a short decision path. The session, sandbox, and change-request loop is described at [Kortix](https://kortix.com/docs).
