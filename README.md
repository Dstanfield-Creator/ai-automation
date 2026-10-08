# AI & Automation

> AI agents with real operational reach into a homelab, held to the same controls you would demand of a junior admin's service account, plus the workflow automation that runs alongside them. This is the AI & Automation department of my GitHub.

**Status:** Active · **Updated:** 2026-10-08

## Structure

```
├── paperclip-ai-agents/   # Self-hosted Paperclip: scoped Proxmox/PBS tokens, protected VMs, hardened host
├── CONTRIBUTING.md        # Sanitisation rules
└── LICENSE
```

## Contents

| Item | Summary | Status |
|---|---|---|
| [Paperclip AI Agents](./paperclip-ai-agents/) | A self-hosted [Paperclip](https://github.com/paperclipai/paperclip) instance where agents inspect the lab, build and retire VMs and read logs through least-privilege API tokens that cannot touch the backup server or themselves: custom roles, path-scoped ACLs, `protection=1` on the crown jewels, UFW, and an SSH-tunnel-only UI | Active |

## Automation elsewhere

- **n8n** runs on the [Docker Services Host](https://github.com/Dstanfield-Creator/lab-ops/tree/main/docs/docker-services-host/) and is defined in the [lab-ops Compose services stack](https://github.com/Dstanfield-Creator/lab-ops/tree/main/compose/services). Workflows: lab notifications, log enrichment, scheduled checks, alert-to-notification for [monitoring](https://github.com/Dstanfield-Creator/cyber-resources/tree/master/monitoring).
- **Lab lifecycle scripts** (`lab-up`, `lab-down`, `lab-ssh-check`) live in [lab-ops/scripts](https://github.com/Dstanfield-Creator/lab-ops/tree/main/scripts); the agents call the same Proxmox API they do, with a narrower token.

## Roadmap

- Publish the agents' rules-of-engagement file (`LAB.md`) as a sanitised template.
- Export the n8n workflows, sanitised, into this repo.
- An agent activity audit: what the agents actually did, reconstructed from Proxmox task logs and PBS access logs.

## Conventions

- Real IPs, MACs, usernames, tailnet names and secrets are replaced with documentation placeholders (RFC 5737 `192.0.2.0/24`, `example.ts.net`). VM IDs, hostnames and token *names* are real; token secrets never appear.

See [CONTRIBUTING.md](./CONTRIBUTING.md) for the full sanitisation rules.

---

**Author:** Danny Stanfield · Perth, WA  
**License:** MIT
