# Hi, I'm Nick

Backend software engineer, 9 years in enterprise software. I build event-driven microservices in Java/Spring Boot on Kubernetes and own them end-to-end: design, delivery, observability, incident response and infrastructure-as-code. Outside work I build Flutter apps and run a fully automated homelab.

**Java 25 · Spring Boot 4 · Kafka (MSK, Avro) · PostgreSQL · Kubernetes · ArgoCD · Terraform · AWS · GitHub Actions**

---

## At work

Selected results from my current role in a ~45-service microservice platform:

- **Cut Kafka broker CPU ~17% avg / ~13% peak** on a shared cluster by re-tuning a producer's compression codec and batching (linger/batch/buffer). That fixed a capacity problem the team had previously solved by scaling the cluster.
- **Shrank payloads ~86%** by migrating a high-volume topic from JSON to Avro with a schema registry. Rolled out with dual-write and verified 1:1 message parity.
- **Led a ~45-service CI/CD migration** from duplicated ~300-line inline pipelines to a shared, versioned reusable-workflow pattern.
- **Re-architected a blocking core workflow into async, event-driven processing** across 6 services. Kafka consumers/producers and dead-letter handling replaced a fragile retry loop, and two god classes were split into focused domain services.
- **Moved a shared library to Spring Boot 4 / Java 25**, unblocking modernization for every service that depends on it.
- **Resolved production incidents end-to-end**: fleet-wide Kafka auth misconfiguration, health-check timeouts causing crash-loops, a cache-key mismatch silently routing events to a DLQ, and an expired TLS bundle breaking an external integration.
- **Built AI developer tooling**: MCP servers for Kafka administration, log search and issue tracking, adopted across the team to streamline ticket → PR → deploy.

<details>
<summary>Career path</summary>

| Years | Role | Focus |
|---|---|---|
| 2022 – now | Senior Backend Engineer | Event-driven microservices, Kafka, AWS, platform reliability |
| 2021 – 2022 | DevOps Lead | Git platform and CI/CD migrations |
| 2019 – 2021 | Full-Stack Developer | Mobile front-ends + Spring Boot backends |
| 2017 – 2019 | Mobile Developer | Customer-facing mobile app features |

</details>

---

## Projects

### [Arr Client](https://github.com/Nicktronix/arr-client) · Flutter · MIT

Cross-platform client for Sonarr and Radarr: library browsing, release search, unified download queue, manual import, multi-instance support. Builds for Android, iOS, web and desktop, with APKs on [Releases](https://github.com/Nicktronix/arr-client/releases).

- Credentials encrypted with AES-256-GCM in a background isolate (PBKDF2, 600k iterations), stored in the platform keychain, with optional biometric lock
- Optimistic UI with automatic rollback; instance-aware caching without a state-management library
- CI on GitHub Actions: analyze, test, Codecov coverage, semantic-versioned releases

### Homelab (private)

GitLab monorepo running 38 Docker Compose services on Proxmox and TrueNAS, run like a production platform.

- **Infrastructure as code:** OpenTofu for Proxmox, Cloudflare (DNS with DNSSEC, Tunnel, Zero Trust, WAF, email routing) and clustered Technitium DNS; Ansible for host hardening and storage; the UniFi zone firewall managed declaratively through its API
- **Supply chain:** every image pinned by version and digest, self-hosted Renovate merge requests, secret scanning in CI, and Trivy scans that fail the pipeline on HIGH/CRITICAL findings
- **Security:** network segmentation into firewall zones, admin UIs restricted to trusted zones and VPN, internal PKI with expiry monitoring, SOPS + age encrypted secrets
- **Reliability:** 43 Prometheus alert rules, including a dead-man-switch Watchdog and alerts for missing backups; Loki/Alloy log pipeline including the gateway's syslog
- **Disaster recovery:** borgmatic offsite backups with database dumps, a written DR runbook, and a tested restore drill
- **Docs:** ADRs and runbooks for decisions and operations

### [mashigi.com](https://mashigi.com) (private repo)

Astro + Tailwind static site with Cloudflare Pages Functions for live Twitch/social data. KV caching cuts upstream API calls by over 99%. DNS, security headers and email routing are managed in Terraform, with deploys from GitHub Actions.

### Anidarr (private, in progress)

Python service that replaces Sonarr for anime: MyAnimeList metadata via Jikan, fansub-aware release parsing, and Prowlarr search.

### Dotfiles (private)

GNU Stow configs for an Arch/KDE workstation and a macOS laptop: zsh, tmux, Neovim, Alacritty and Starship in Catppuccin Mocha throughout. Also includes:

- a Claude Code `PreToolUse` guard hook that blocks destructive commands (forced recursive deletes, force pushes, disk tools) and always prompts before pushes or hard resets, even in auto mode
- a recovery runbook, reference `/etc` and boot configs, and package lists, so the machine can be rebuilt from scratch

---

## Contact

nicktronix@gmail.com
