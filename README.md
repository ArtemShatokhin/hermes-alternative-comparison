# Kortix, the open-source AI Operating System, and the personal agents beside it

Kortix is the open-source AI Operating System. It gives a team one git repo it owns for every agent, skill, memory file, and connector, with each session running on its own isolated cloud computer and work landing through a change request a person approves. Hermes is a self-hosted personal agent with persistent memory: one operator, one machine, an agent that grows with them. Kortix is open source: read it, fork it, audit it. See [Kortix on GitHub](https://github.com/kortix-ai/suna).

Hermes is good at exactly what it is built for. A single person who wants an always-on agent on a server they control, in the chat apps they already use, learning as it runs, gets that from Hermes without running a company platform. Kortix is the other shape on purpose: the platform a team owns and governs once more than one person steers the agents. The two solve different sizes of the same problem. These notes are written so you can pick the size that fits.

## The open-source field, side by side

Kortix comes first because it is the one built for a whole team. Hermes, OpenClaw, and OpenHands are strong open-source options for one person or one engineering team, and each is listed with the source it came from.

| Project | What it is | Where it runs | Who owns the config | How work is reviewed | Source URL |
| --- | --- | --- | --- | --- | --- |
| Kortix | The open-source AI Operating System: a workforce for a whole team. | Kortix Cloud, your VPC, or your own on-prem network. | You. Agents, skills, and memory in one git repo. | Work reaches main through a change request a person approves. | https://kortix.com/docs |
| Hermes | A self-hosted personal agent with a learning loop and memory. | Your own server, a $5 VPS, a GPU cluster, or serverless. | You, on the machine you run it on. | Reviewed by the one operator who runs it. | https://github.com/NousResearch/hermes-agent |
| OpenClaw | An open-source AI assistant that meets you in your chat apps. | Your own computer or a server, with native apps. | You. State, memory, and credentials stay on your hardware. | Reviewed by the operator, or the team that shares the install. | https://github.com/openclaw/openclaw |
| OpenHands | A self-hosted control center for coding agents and automations. | Your laptop, Docker, a VM, or a cloud backend. | You. Agent backends run on infrastructure you choose. | Code review of agent changes in your Git workflow. | https://github.com/OpenHands/OpenHands |

Hermes, OpenClaw, and OpenHands facts come from each project's own repository, checked October 2026. Kortix facts come from the Kortix documentation.

## Start here

- [Kortix vs Hermes](https://hermesalternative.com/kortix-vs-hermes): the head-to-head for one operator and one team.
- [Open-source Hermes alternatives](https://hermesalternative.com/hermes-alternatives): who each open-source agent fits, and what each one is not.
- [Self-hosting a Hermes alternative](https://hermesalternative.com/self-hosting-hermes-alternative): the platform a team owns, on one Docker Compose stack.

## The notes in this repository

- [01 Kortix vs Hermes](docs/01-kortix-vs-hermes.md): the same open-source values at two different scales, feature by feature.
- [02 Self-hosting a Hermes alternative](docs/02-self-hosting-a-hermes-alternative.md): the verified Kortix self-host commands, from install to backup.
- [03 Migrating a team off a personal agent](docs/03-migrating-a-team-off-a-personal-agent.md): what a shared repo, permissions, and change-request review replace.
