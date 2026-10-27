
# My Personalized DevOps Engineer Roadmap

> **Owner:** 1337 student (Morocco) — strong C, solid Python, intermediate Linux, basic networking, Git/GitHub user, Docker beginner.
> **Goal:** Become a junior DevOps engineer who can build, containerize, test, automate, deploy, secure, and monitor real applications — demonstrated through a portfolio, not certificates.
> **Philosophy:** Project-first, break-it-to-understand-it, 1337-style independent problem solving. No topic is "learned" until it has been built, broken, and fixed by hand.

---

## Table of Contents

1. [Profile & Starting-Point Assessment](#1-profile--starting-point-assessment)
2. [Roadmap Philosophy & Scope Control](#2-roadmap-philosophy--scope-control)
3. [Phase Overview Table](#3-phase-overview-table)
4. [Dependency Graph](#4-dependency-graph)
5. [Phase 0 — Diagnostic Assessment (Days 1–7)](#phase-0--diagnostic-assessment-days-17)
6. [Phase 1 — Linux, Networking, Bash & Python Automation](#phase-1--linux-networking-bash--python-automation)
7. [Phase 2 — Docker Fundamentals](#phase-2--docker-fundamentals)
8. [Phase 3 — Docker Compose & Multi-Container Applications](#phase-3--docker-compose--multi-container-applications)
9. [Phase 4 — Automated Testing & CI/CD](#phase-4--automated-testing--cicd)
10. [Phase 5 — Cloud Fundamentals & Practical Deployment (AWS)](#phase-5--cloud-fundamentals--practical-deployment-aws)
11. [Phase 6 — Infrastructure as Code with Terraform](#phase-6--infrastructure-as-code-with-terraform)
12. [Phase 7 — Configuration Management with Ansible](#phase-7--configuration-management-with-ansible)
13. [Phase 8 — Cloud Security, IAM & Secrets Management](#phase-8--cloud-security-iam--secrets-management)
14. [Phase 9 — Monitoring, Logging & Observability](#phase-9--monitoring-logging--observability)
15. [Phase 10 — Kubernetes & Container Orchestration](#phase-10--kubernetes--container-orchestration)
16. [Phase 11 — Helm, GitOps & Advanced Delivery](#phase-11--helm-gitops--advanced-delivery)
17. [Phase 12 — Capstone & Portfolio Readiness](#phase-12--capstone--portfolio-readiness)
18. [Advanced & Optional Topics](#18-advanced--optional-topics)
19. [IBM Course Mapping](#19-ibm-course-mapping)
20. [freeCodeCamp Video Mapping](#20-freecodecamp-video-mapping)
21. [The Progressive Portfolio Project: "Pulse"](#21-the-progressive-portfolio-project-pulse)
22. [Final Capstone Project Specification](#22-final-capstone-project-specification)
23. [Weekly Study Plan (8–10 h/week)](#23-weekly-study-plan-810-hweek)
24. [GitHub Portfolio Checklist](#24-github-portfolio-checklist)
25. [Junior DevOps Skills Matrix](#25-junior-devops-skills-matrix)
26. [What To Do First — Exact Tasks for Day 1–7](#26-what-to-do-first--exact-tasks-for-day-17)

---

## 1. Profile & Starting-Point Assessment

| Area | Current Level | Roadmap Treatment |
|---|---|---|
| C programming | Comfortable with memory, pointers, processes, threads, sync | **Not re-taught.** Used as the mental model for understanding how containers, processes, and the kernel behave (cgroups, namespaces, signals). |
| Python | Can build real projects using APIs/libraries | **Not re-taught as a language.** Used immediately for automation, test suites, and as the application being deployed. |
| Linux | Intermediate (shell, filesystem, permissions, processes) | **Audited, not restarted.** Phase 1 fills gaps only (systemd, cgroups/namespaces, process/resource limits, advanced permissions, performance tools). |
| Networking | Basic | **Primary growth area in Phase 1**, then continuously reinforced through real troubleshooting in every later phase (containers, cloud, Kubernetes). |
| Git/GitHub | Working user | Upgraded from "I can commit and push" to "I run team workflows": branching strategy, PR review discipline, protected branches, conventional commits, release tagging — folded into Phase 1 and Phase 4 (CI triggers on Git events). |
| Docker | Beginner | **Deep dive in Phase 2–3.** This is the real starting line of DevOps-specific work. |
| Software engineering | Project-experienced | Leveraged to avoid "toy tutorial" syndrome — every exercise is tied to a real, evolving codebase (see Section 21). |

**Conclusion:** You are *not* starting as a beginner. You are starting as a backend-capable engineer who needs to acquire the operational half of software delivery: packaging, automating, provisioning, securing, and observing systems in production-like conditions. The roadmap below assumes this and skips re-teaching things you already know, except where a networking/Linux concept must be revisited *because it blocks a DevOps concept* (e.g., you must understand DNS resolution order before debugging container-to-container DNS).

---

## 2. Roadmap Philosophy & Scope Control

### Non-negotiable rules

1. **One tool per category, first.** You will not learn two clouds, two CI/CD systems, or two IaC tools simultaneously. Alternatives are mentioned for context only.
   - Cloud: **AWS** (largest market share, most learning material, free tier sufficient for this roadmap).
   - CI/CD: **GitHub Actions** (you already use GitHub; zero extra infrastructure to run pipelines).
   - IaC: **Terraform** before any other IaC tool (Pulumi, CDK, CloudFormation are mentioned only as "know they exist").
   - Configuration management: **Ansible** (agentless, Python-based under the hood — matches your background).
   - Orchestration: **Kubernetes**, learned locally first (kind/minikube) before any managed service (EKS).
   - Monitoring: **Prometheus + Grafana** (the de-facto open-source standard, vendor-neutral, used in almost every job description).
2. **Depth before breadth.** You will not move to Kubernetes before Docker is second nature, and you will not touch Docker before you can explain what a Linux process, namespace, and cgroup are.
3. **Everything is a project artifact.** No isolated "hello world" tutorials that get thrown away. One core application evolves through nearly every phase (Section 21), so each new tool is applied to something you already understand, instead of learning a new app and a new tool at the same time.
4. **Breakage is mandatory.** Each phase includes deliberately broken scenarios. If you can only make things work, you are not yet a DevOps engineer — you become one when you can explain *why* something failed, and in which layer (app, container, network, infra, platform) it failed.
5. **Courses are references, not goals.** Finishing an IBM course or a freeCodeCamp video is not a milestone. Building and defending the related project is.

### Explicit scope decisions (and why)

| Decision | Reason |
|---|---|
| AWS over Azure/GCP | Largest job market share; freeCodeCamp + most docs target it; once you know one cloud's IAM/VPC/compute model, switching clouds is a vocabulary problem, not a conceptual one. |
| GitHub Actions over Jenkins/GitLab CI as the primary pipeline | No separate server to run/maintain, directly integrated with the repositories you already use, YAML model transfers conceptually to GitLab CI/Jenkins later. Jenkins is still covered briefly in Phase 4 because many existing companies run it — you only need to *recognize and read* a Jenkinsfile, not master it. |
| Kubernetes only after Docker Compose, CI/CD, and cloud fundamentals | Kubernetes assumes you already understand containers, networking between containers, environment-based configuration, image registries, and health checks. Teaching Kubernetes earlier produces people who can `kubectl apply` but cannot explain what's happening — exactly what you want to avoid. |
| Helm + GitOps placed after raw Kubernetes manifests | You must be able to hand-write and debug plain YAML before a templating/automation layer hides it from you. |
| Service mesh, serverless, multi-cloud, OpenStack, KCNA cert study | Placed in "Advanced/Optional" (Section 18). They are valuable conceptually but not required to be hireable as a *junior* DevOps engineer, and adding them earlier dilutes focus. |
| Terraform before Ansible | Terraform answers "what infrastructure exists" (declarative, immutable), Ansible answers "what state is a machine in" (configuration, idempotent). Provisioning conceptually precedes configuring. |

---

## 3. Phase Overview Table

| # | Phase | Duration (at 8–10h/week) | Core Output |
|---|---|---|---|
| 0 | Diagnostic Assessment | 2–4 days | Personal gap list; environment ready |
| 1 | Linux, Networking, Bash & Python Automation | 2–3 weeks | Hardened dev VM, networking lab notebook, automation scripts |
| 2 | Docker Fundamentals | 2–3 weeks | "Pulse" app containerized, custom image published |
| 3 | Docker Compose & Multi-Container Apps | 2 weeks | Full local stack: app + DB + cache + reverse proxy |
| 4 | Automated Testing & CI/CD | 2–3 weeks | GitHub Actions pipeline: test → build → push → deploy |
| 5 | Cloud Fundamentals & Deployment (AWS) | 3 weeks | App running on a real AWS VM, reachable publicly |
| 6 | Infrastructure as Code (Terraform) | 2–3 weeks | Entire AWS environment defined as code, reproducible |
| 7 | Configuration Management (Ansible) | 1–2 weeks | Server bootstrap & app deployment fully automated |
| 8 | Cloud Security, IAM & Secrets | 1–2 weeks | Least-privilege IAM, secrets out of code/Git, hardened network |
| 9 | Monitoring, Logging & Observability | 2 weeks | Prometheus + Grafana dashboards + alerting on "Pulse" |
| 10 | Kubernetes & Orchestration | 3–4 weeks | "Pulse" running on a local K8s cluster with self-healing |
| 11 | Helm, GitOps & Advanced Delivery | 2 weeks | Helm chart + ArgoCD auto-sync from Git |
| 12 | Capstone & Portfolio Readiness | 3–4 weeks | Final production-style system + documented portfolio |

**Total estimated time:** ~28–35 weeks of focused, part-time study (roughly 7–9 months at 8–10 h/week). This is an estimate, not a deadline — difficult phases (Networking, Kubernetes, Terraform/IAM) deserve extra time rather than being rushed.

---

## 4. Dependency Graph

```
Linux/Networking/Bash/Python (1)
        │
        ▼
     Docker (2) ──────────────┐
        │                     │
        ▼                     │
  Docker Compose (3)          │   (container & networking knowledge
        │                     │    required for everything below)
        ▼                     │
 Testing & CI/CD (4) ◄────────┘
        │
        ▼
 Cloud Fundamentals (5)
        │
        ├──────────────┐
        ▼              ▼
  Terraform (6)   Security/IAM (8) (IAM concepts needed before
        │              │            Terraform touches real infra
        ▼              │            safely — introduced lightly in 5,
  Ansible (7)◄──────────┘            formalized in 8)
        │
        ▼
 Monitoring/Observability (9)
        │
        ▼
   Kubernetes (10)
        │
        ▼
 Helm & GitOps (11)
        │
        ▼
 Capstone & Portfolio (12)
```

Networking is not a single phase — it is reinforced at every arrow above (container DNS in Phase 2–3, pipeline network access in Phase 4, VPC/subnets/security groups in Phase 5–6, service networking/Ingress/DNS in Phase 10).

---

## Phase 0 — Diagnostic Assessment (Days 1–7)

### A. Phase Overview
- **Duration:** 2–4 days (part of Week 1).
- **Purpose:** Confirm what you actually know vs. assume you know, and set up the tooling you'll use for the rest of the roadmap. Avoids wasted time re-studying fundamentals, and avoids false confidence on networking.
- **Prerequisites:** None.
- **Outcome:** A written self-assessment (commit it to a `learning-log` repo) listing confirmed strengths and real gaps, plus a working Linux dev environment.

### B. Diagnostic Tasks (do these without searching first; research only after attempting)

1. **Linux:** On a fresh VM or container, create a non-root user, give it `sudo` only for `systemctl` commands via `/etc/sudoers.d`, and explain why editing `/etc/sudoers` directly is dangerous.
2. **Processes:** Start a long-running Python script, find its PID, inspect its open file descriptors (`/proc/<pid>/fd`), send it `SIGSTOP`/`SIGCONT`, then `SIGTERM`, and explain the difference from `SIGKILL`.
3. **Networking:** Explain, in your own words and without notes: the difference between a MAC address, an IP address, and a port; what a TCP 3-way handshake is; how DNS resolves `example.com` into an IP (resolver → root → TLD → authoritative); the difference between TCP and UDP; what TLS adds on top of TCP. Write this down — you will reference it constantly.
4. **Bash:** Write a one-line pipeline using `grep`, `awk`, and `sort` to find the top 5 IPs hitting a sample Apache/Nginx log.
5. **Python:** Write a script using `subprocess` that runs `df -h`, parses the output, and exits with a non-zero code if any filesystem is over 90% used.
6. **Git:** From memory, explain `git rebase` vs `git merge`, when you'd use each, and what a force-push does to a shared branch.

### C. Resources
- Skim **IBM "Hands-on Introduction to Linux Commands and Shell Scripting"** only for topics above you're unsure about (likely: process signals, `/proc`, sudoers) — **optional/selective**, skip shell basics you already know.
- Skim **IBM "Getting Started with Git and GitHub"** only for branching/PR workflow sections — **optional**, skip basic `git add/commit/push`.

### D. Completion Checklist
- [ ] You can explain DNS resolution, TCP handshake, and TLS handshake out loud, unaided.
- [ ] You have a dedicated Linux environment (VM, WSL2, or cloud free-tier instance) you control as root.
- [ ] You have a GitHub repo named `devops-learning-log` with your diagnostic answers committed.
- [ ] You know your 3 weakest areas and will prioritize them in Phase 1.

---

## Phase 1 — Linux, Networking, Bash & Python Automation

### A. Phase Overview
- **Duration:** 2–3 weeks.
- **Purpose:** Close networking and systems gaps that will otherwise sabotage every later phase (you cannot debug a container that "can't reach the database" without understanding DNS, routing, and ports; you cannot write a Terraform security group without understanding firewalls).
- **Prerequisites:** Phase 0 complete.
- **You should already know:** Shell navigation, permissions, basic scripting, basic process concepts.
- **You should be able to, at the end:** Diagnose "why can't machine A reach service B" using a structured method (L1→L7), write non-trivial Bash and Python automation, and explain how the Linux kernel isolates processes (the foundation of containers).

### B. Detailed Syllabus

**1. Linux internals that matter for DevOps (new material)**
- **Processes vs. threads vs. namespaces vs. cgroups.** What it is: namespaces isolate *what a process can see* (PID, net, mount, UTS, IPC, user); cgroups limit *what a process can use* (CPU, memory, I/O). Why it matters: this is literally what Docker is built on — a container is just a process with namespaces + cgroups + a layered filesystem. How it works: `unshare`, `nsenter`, inspecting `/sys/fs/cgroup`. Common mistakes: believing containers are VMs; forgetting that containers share the host kernel (so a kernel-level exploit crosses container boundaries).
- **systemd**: units, `systemctl status/enable/start`, writing a custom `.service` file, journald logs (`journalctl -u`, `-f`, `--since`). Why: you'll run agents (node_exporter, Docker daemon, your own app) as services; CI/CD runners and cloud VMs are managed via systemd.
- **Filesystem & disk**: inodes, mount points, `df`/`du`, disk full scenarios, log rotation (`logrotate`). Why: "disk full" is one of the most common production incidents.
- **Resource limits**: `ulimit`, OOM killer behavior, `dmesg` after an OOM kill. Why: directly explains container crashes with exit code 137 later.
- **Package & process management recap (only gaps):** `systemctl`, `ps aux --forest`, `lsof -i`, `strace` basics (why a process is hanging / which syscalls it's making).

**2. Networking (the biggest intentional investment of this phase)**
- **The OSI/TCP-IP model as a troubleshooting tool**, not theory: for every failure, ask "Is this L1/2 (link), L3 (IP/routing), L4 (TCP/UDP/port), or L7 (HTTP/app)?"
- **IP addressing & subnetting**: CIDR notation, subnet masks, private vs. public ranges, NAT. Why: required to design VPCs in Phase 5/6.
- **Routing**: `ip route`, default gateway, how a packet decides where to go.
- **DNS in depth**: record types (A, AAAA, CNAME, MX, TXT, NS), `/etc/resolv.conf`, `dig`/`nslookup`, TTL and caching, how container/K8s DNS differs from host DNS (preview for Phase 2/10).
- **Ports & sockets**: well-known ports, `ss -tulpn`, what "binding" a port means, the difference between a port being closed, filtered, and refused.
- **HTTP/HTTPS**: request/response structure, headers, status codes, keep-alive, the TLS handshake (certificates, chain of trust), what a reverse proxy/load balancer changes about headers (`X-Forwarded-For`, `Host`).
- **Firewalls & security groups (concept now, cloud-specific later):** stateful vs. stateless filtering, `iptables`/`nftables` basics, default-deny thinking.
- **SSH in depth**: key-based auth, `~/.ssh/config`, agent forwarding, port forwarding/tunneling (`-L`, `-R`, `-D`), why password auth should be disabled on servers.
- **Troubleshooting toolkit**: `ping`, `traceroute`/`mtr`, `curl -v`, `dig`, `ss`, `tcpdump` (capture and read a basic handshake), `nc` for manual port testing.

**3. Bash scripting for automation (gap-filling, not "intro to bash")**
- Functions, arrays, traps (`trap ... EXIT`), `set -euo pipefail` and why every script should start with it, exit codes and `$?`, process substitution, here-docs.
- Idempotency: writing scripts safe to re-run (check-before-create patterns) — this is the same principle behind Ansible and Terraform, introduced here deliberately.

**4. Python for operations (building on your existing Python skill, not re-teaching the language)**
- `subprocess` (replacing shell scripts when logic gets complex), `os`/`pathlib`, `argparse` for real CLI tools, `logging` module (never use `print` for tooling), working with `requests` against real APIs (prep for cloud SDK usage and health-check scripts), basic `paramiko`/`fabric` or plain SSH invocation for remote automation.
- Writing a script that is testable (functions, not top-level script logic) — foundation for Phase 4 testing discipline.

**5. Git workflows (upgrade, not re-teach)**
- Feature branches, Conventional Commits, meaningful PR descriptions, protecting `main`, tagging releases (`git tag -a vX.Y.Z`), `.gitignore` discipline, resolving merge conflicts deliberately created.

### C. Practical Exercises (simple → hard)
1. Use `ss -tulpn` to identify every listening service on your machine and justify whether each should be exposed.
2. Deliberately misconfigure `/etc/resolv.conf` and diagnose why `curl https://github.com` fails — identify it as a DNS issue, not a connectivity issue, using `dig` vs `ping <ip>` as the distinguishing test.
3. Use `tcpdump -i any port 80` while curling a local server; identify the SYN, SYN-ACK, ACK packets.
4. Write a Bash script that checks whether a given TCP port is open on a host without using `nc` (pure `/dev/tcp`), with proper timeout handling.
5. Set up SSH key auth to a VM, then disable password authentication, then **lock yourself out on purpose** by misconfiguring `sshd_config`, and recover via your cloud/hypervisor console — document the recovery steps.
6. **Troubleshooting scenario (no step-by-step given):** You are told "service X on port 8080 is unreachable from another machine on the same network, but `curl localhost:8080` works locally." Find and fix the cause (candidates to rule out yourself: service bound to `127.0.0.1` instead of `0.0.0.0`, host firewall rule, wrong port). Document your diagnostic steps in order.
7. Write a Python script (`healthcheck.py`) that pings a list of hosts/ports from a config file, logs results with the `logging` module, and returns a non-zero exit code if any check fails — this script will be reused literally in later phases.

### D. Project: "Pulse" — Application Baseline
See Section 21 for the full specification; Milestone 1 (local run + full dependency documentation) belongs to this phase.

### E. Resources
| Resource | Priority | What to use it for |
|---|---|---|
| IBM: *Hands-on Introduction to Linux Commands and Shell Scripting* | Supplementary | Only the sections on `systemd`, process signals, and scripting patterns you're unsure of. Skip basic navigation/permissions. |
| IBM: *Getting Started with Git and GitHub* | Supplementary | Only branching workflows/PR review if your current usage is solo-only. |
| freeCodeCamp: *DevOps Prerequisites Course — Getting Started with DevOps* | Supplementary | General orientation; useful once, skip if it only repeats Linux basics you know. |
| Official docs: `man ss`, `man tcpdump`, `man systemd.service` | Essential | Primary reference, not tutorials — build the habit of reading man pages. |
| *TCP/IP Illustrated* concepts via any current networking primer (e.g., Cloudflare Learning Center articles on DNS/TLS/HTTP) | Essential | Best modern, free, accurate explanations of DNS/TLS/HTTP internals. |

### F. Completion Criteria
- [ ] Can explain, from memory, the full path of a browser request to `https://example.com` (DNS → TCP → TLS → HTTP → response).
- [ ] Can diagnose a "connection refused" vs. "connection timed out" vs. "DNS not resolving" and state what each implies.
- [ ] Can write a Bash script with proper error handling (`set -euo pipefail`, trapped errors, meaningful exit codes).
- [ ] Can write a Python automation script with logging, argument parsing, and a non-zero exit code on failure.
- [ ] Has recovered from a self-inflicted SSH lockout at least once.
- [ ] "Pulse" app runs locally with a documented `requirements.txt`/dependency list and a README describing exactly how to run it from a clean machine.

---

## Phase 2 — Docker Fundamentals

### A. Phase Overview
- **Duration:** 2–3 weeks.
- **Purpose:** This is where "DevOps" tooling truly begins. Containers are the unit of deployment for everything that follows (CI/CD artifacts, Kubernetes pods, cloud deployments).
- **Prerequisites:** Phase 1 (namespaces/cgroups mental model, networking fundamentals, Linux processes).
- **At the end you can:** Containerize any application you understand, explain image layering and caching, run multi-container setups manually with `docker network`/`docker volume`, and diagnose common container failures.

### B. Detailed Syllabus
- **Images vs. containers:** an image is a read-only, layered filesystem + metadata; a container is a running (or stopped) instance of an image, i.e., a namespaced process with a writable layer on top. Relate explicitly to Phase 1's namespaces/cgroups.
- **Dockerfile instructions in depth:** `FROM`, `RUN`, `COPY` vs `ADD`, `WORKDIR`, `ENV` vs `ARG`, `EXPOSE` (documentation only, doesn't publish ports), `USER` (why running as root in a container is a security risk), `ENTRYPOINT` vs `CMD` and how they combine, multi-stage builds (why: smaller, more secure final images — critical for Python apps with build-time dependencies).
- **Layer caching:** why instruction order matters (`COPY requirements.txt` + `RUN pip install` *before* `COPY . .`), how changing one line invalidates all layers below it, `.dockerignore`.
- **Image tagging & versioning:** `latest` is not a version, semantic tags, immutable tags by digest (`image@sha256:...`), why "it worked yesterday" bugs often trace to a moved `latest` tag.
- **Container lifecycle:** `create` → `start` → `running` → `paused`/`stopped` → `removed`; `docker run` vs `exec` vs `attach`; restart policies (`no`, `on-failure`, `always`, `unless-stopped`) and when each is appropriate.
- **Logs & inspection:** `docker logs`, `docker inspect`, `docker stats`, `docker top`, exit codes (0 = clean, 1 = app error, 137 = SIGKILL/OOM, 143 = SIGTERM) — ties directly back to Phase 1 resource limits.
- **Networking between containers:** default bridge vs. user-defined bridge networks, container-to-container DNS resolution by container/service name (and why default bridge network does **not** give you this), `docker network inspect`, port publishing (`-p host:container`) vs. `EXPOSE`, why `localhost` inside a container is not the host.
- **Volumes & persistence:** named volumes vs. bind mounts vs. tmpfs, when to use each, volume lifecycle (`docker volume ls/rm`), data loss scenarios when containers are removed without volumes.
- **Health checks:** `HEALTHCHECK` instruction, how orchestrators (Compose/Kubernetes) use health status, the difference between "running" and "ready."
- **Image registries:** Docker Hub vs. private registries (preview of ECR in Phase 5), `docker login/push/pull`, image naming conventions (`registry/namespace/image:tag`).
- **Container security basics:** running as non-root, read-only root filesystem (`--read-only`), not baking secrets into images (`docker history` exposes build-time env leaks), scanning images (`docker scout` or `trivy`), minimal base images (`-slim`/`-alpine`/distroless) and trade-offs (musl vs glibc issues with Python wheels — a real gotcha).

### C. Practical Exercises
1. Containerize "Pulse" with a **single-stage** Dockerfile first; measure image size.
2. Rebuild using a **multi-stage** Dockerfile; compare size and explain the difference.
3. Break caching on purpose: put `COPY . .` before `RUN pip install -r requirements.txt`, rebuild after changing an unrelated file, and observe/explain the unnecessary reinstall.
4. Run the container, then `docker exec` into it and kill the main process manually — observe what happens to the container depending on `PID 1` behavior and restart policy.
5. Create two containers on the **default bridge** network and show that they cannot resolve each other by name; then create a **user-defined bridge network**, attach both, and show DNS resolution now works. Explain why, referencing Docker's embedded DNS server.
6. Deliberately misconfigure the port mapping (`-p 8080:8080` while the app listens on `5000`) and diagnose "connection refused" using the troubleshooting steps from Phase 1.
7. Remove a container that was using a bind mount vs. one using no persistence at all; show the data outcome differs.
8. Force an OOM kill: run the container with `--memory=20m` against a workload that needs more, observe exit code `137` in `docker inspect`, and correlate with `dmesg`.
9. **Independent challenge (no steps given):** Make the container's health check correctly report "unhealthy" when the database dependency (to be added in Phase 3) is unreachable, using only `HEALTHCHECK` and a script you write.
10. Scan your built image with `trivy image` and fix at least one real reported vulnerability by changing the base image or a dependency version.

### D. Project
See **Section 21, Milestone 2** ("Pulse" containerized + published to a registry).

### E. Resources
| Resource | Priority | Notes |
|---|---|---|
| Official Docker docs (docs.docker.com) — "Get Started", "Build", "Engine" sections | **Essential** | Primary technical reference; always current. |
| IBM: *Introduction to Containers with Docker, Kubernetes & OpenShift* | **Essential** (Docker portion), **Postpone** (Kubernetes/OpenShift portions until Phase 10) | Good conceptual overview of why containers exist; do the Docker labs now, skip/delay the K8s and OpenShift modules until Phase 10 so they land on already-built Docker knowledge. |
| freeCodeCamp: *Docker Tutorial for Beginners — Full DevOps Course* | **Essential** | Strong hands-on coverage of images, volumes, networking, Compose intro; skip any section that only repeats basic Linux commands you already know. |
| freeCodeCamp: *Docker with Node.js and Express* | **Optional** | Concepts transfer directly even though it's Node — watch only if you want a second worked example; not required since "Pulse" is your real exercise. |
| freeCodeCamp: *Learn Docker — Full DevOps Course for Deploying Containerized Apps* | **Supplementary** | Overlaps with the beginner course; use only for the deployment-oriented back half (publishing images, basic Compose) to avoid duplicate content. |
| `trivy` / `docker scout` docs | **Essential** | For the image-scanning exercise. |

### F. Completion Criteria
- [ ] Can write a production-sane multi-stage Dockerfile from scratch for a Python app, with no notes.
- [ ] Can explain layer caching and demonstrate it changing a Dockerfile's instruction order.
- [ ] Can explain, precisely, why two containers on the default bridge network can't resolve each other by name and how a user-defined network fixes it.
- [ ] Can diagnose a container exit code (0/1/137/143) and state the likely cause.
- [ ] Has pushed a tagged image to a registry (Docker Hub is fine for now).
- [ ] Has fixed at least one vulnerability found by an image scanner.

---

## Phase 3 — Docker Compose & Multi-Container Applications

### A. Phase Overview
- **Duration:** 2 weeks.
- **Purpose:** Real applications are never a single container. This phase teaches you to declaratively define and operate a multi-service stack — the direct conceptual ancestor of Kubernetes manifests.
- **Prerequisites:** Phase 2 fully complete (manual `docker network`/`docker volume` experience is required to appreciate what Compose automates).
- **At the end you can:** Stand up "Pulse" + PostgreSQL + Redis + a reverse proxy with one command, manage environment-specific configuration, and debug inter-service failures.

### B. Detailed Syllabus
- **Compose file anatomy:** `services`, `networks`, `volumes`, `depends_on` (and its real limitation: it waits for container start, not application readiness — a critical, commonly-misunderstood gotcha), `environment` vs `env_file`, `build` vs `image`.
- **Service discovery:** Compose auto-creates a network where services reach each other by service name — connect this directly back to Phase 2's user-defined bridge network exercise.
- **Startup ordering & readiness:** why you need an explicit wait-for-it/healthcheck pattern instead of relying on `depends_on` alone; `condition: service_healthy`.
- **Environment-based configuration:** `.env` files, overriding with `docker-compose.override.yml`, separating dev vs. prod compose files, never committing real secrets to `.env` in Git.
- **Persistent storage for stateful services:** named volume for PostgreSQL data directory, understanding what happens on `docker compose down` vs `down -v`.
- **Reverse proxy & load balancing concept (introduced now, expanded in cloud phase):** add Nginx (or Caddy/Traefik) in front of "Pulse" to understand `proxy_pass`, header forwarding, and why this pattern exists (TLS termination, single entry point, future horizontal scaling).
- **Logs across services:** `docker compose logs -f <service>`, aggregated view, why centralized logging will matter later (Phase 9).
- **Resource constraints in Compose:** `deploy.resources.limits` (even outside Swarm, useful for local testing of limits).

### C. Practical Exercises
1. Convert "Pulse" + PostgreSQL into a Compose file using only `depends_on` (no health check) and prove the race condition: restart the stack repeatedly until the app crashes because the DB wasn't ready yet.
2. Fix it properly with a healthcheck + `condition: service_healthy`, and explain why this is more correct than a `sleep` hack.
3. Add Redis for caching; implement and verify an actual cache-hit/cache-miss path in "Pulse."
4. Add Nginx as a reverse proxy in front of "Pulse"; verify `X-Forwarded-For` is correctly set and explain why the app must trust this header only from the proxy.
5. **Break it on purpose:** change the DB service name in the app's connection string but not in the Compose network, and diagnose the resulting DNS failure using the same method from Phase 1/2.
6. **Break it on purpose:** set a wrong environment variable (e.g., wrong `DATABASE_URL` port) and walk through the full diagnostic chain: app logs → container inspect → network test (`docker exec` + `nc`/`curl`) → config review.
7. Run `docker compose down -v` and confirm data loss; then redesign the compose file so an operator must pass an explicit flag to delete data (defense against accidental destruction — a real production lesson).
8. **Independent challenge:** Add a second instance of "Pulse" behind Nginx acting as a basic load balancer (round robin) and prove both instances serve traffic by adding an instance-ID to each response.

### D. Project
See **Section 21, Milestone 3** (full local multi-container stack with persistence and a reverse proxy).

### E. Resources
| Resource | Priority | Notes |
|---|---|---|
| Official Docker Compose docs (compose spec) | **Essential** | Authoritative reference for the compose file schema. |
| freeCodeCamp: *Docker Tutorial for Beginners* (Compose sections) | **Essential** | Already partially covered in Phase 2; revisit the Compose-specific portions now. |
| Nginx official docs — reverse proxy guide | **Essential** | For the proxy configuration exercise. |

### F. Completion Criteria
- [ ] Can start the full "Pulse" stack from a clean clone with a single command and no manual steps.
- [ ] Can explain why `depends_on` alone does not guarantee readiness, with a reproduced example.
- [ ] Can trace and fix a broken inter-service DNS/env-var configuration without guidance.
- [ ] Understands and can explain the data-loss implications of `down -v`.
- [ ] Has implemented a working reverse proxy with correct header forwarding.

---

## Phase 4 — Automated Testing & CI/CD

### A. Phase Overview
- **Duration:** 2–3 weeks.
- **Purpose:** Containers + Compose give you reproducible environments; CI/CD gives you reproducible, automated *processes* around those environments. This is the phase where "DevOps" literally starts meaning "Dev" + "Ops" collaborating through automation.
- **Prerequisites:** Phases 2–3 (you must have something containerized and tagged to build/push), Git workflow fluency (Phase 1).
- **At the end you can:** Explain and build a pipeline with stages (lint → test → build → publish → deploy), use secrets safely in CI, and implement a basic rollback.

### B. Detailed Syllabus
- **Automated testing fundamentals (applied, not from scratch since you can already code):**
  - Unit tests (`pytest`), test doubles/mocking external calls (e.g., mocking Redis/Postgres for pure unit tests), fixtures.
  - Integration tests against real containers (using `docker compose` in CI, or `testcontainers-python`).
  - Coverage reporting and why 100% coverage is not the goal — meaningful tests are.
  - Brief exposure to BDD concepts (`given/when/then`, e.g., `behave` or `pytest-bdd`) — **conceptual understanding is sufficient**, not mastery.
- **CI/CD core concepts:**
  - **Triggers:** push, pull_request, tag, schedule, manual dispatch.
  - **Jobs vs. steps vs. stages**, and **runners** (GitHub-hosted vs. self-hosted) — what a runner actually is (an ephemeral VM/container executing your YAML).
  - **Pipeline as code:** YAML workflow files, versioning pipelines alongside app code.
  - **Artifacts:** passing build outputs between jobs (e.g., test reports, built wheels).
  - **Caching dependencies** (pip cache) to speed up pipelines.
  - **Secrets management in CI:** GitHub Actions encrypted secrets, never echoing secrets into logs, scoping secrets per environment.
  - **Building & publishing container images in CI:** `docker build`, tagging by Git SHA and semantic version, pushing to a registry (Docker Hub now; ECR in Phase 5), using `docker/build-push-action` or equivalent.
  - **Deployment strategies (conceptual now, applied in Phase 5/10):** recreate, rolling update, blue-green, canary — explain trade-offs (downtime vs. complexity vs. speed of rollback).
  - **Health checks gating deployment:** a deploy is only "successful" if the health check passes post-deploy, not just if the deploy command exited 0.
  - **Rollback:** redeploying the previous known-good image tag; why immutable, versioned tags (Phase 2) make this trivial and `latest` makes it dangerous.
  - **Branch protection integration:** required status checks before merge.

### C. Practical Exercises
1. Write `pytest` unit tests for "Pulse" covering at least the core business logic with mocked dependencies.
2. Add an integration test that spins up the real Compose stack and hits a live endpoint.
3. Build a GitHub Actions workflow: on every PR, run lint + unit tests; on merge to `main`, also build and push a Docker image tagged with the Git SHA.
4. **Break it on purpose:** introduce a failing test and confirm the pipeline blocks the merge (branch protection + required check).
5. **Break it on purpose:** leak a secret into a log line intentionally in a throwaway branch, observe GitHub's secret masking, then fix the logging statement — explain why masking isn't a substitute for not logging secrets at all.
6. Add a caching step for pip dependencies and measure pipeline duration before/after.
7. Implement a manual "deploy" job (initially just SSH + `docker compose pull && up -d` to a VM from Phase 5) gated behind a required approval environment.
8. **Independent challenge:** simulate a bad deploy (push a broken image tag) and write the rollback procedure as a runbook, then execute it, restoring the previous tag.
9. Read (do not necessarily build) one example **Jenkinsfile** and one **GitLab CI** `.gitlab-ci.yml` and explain the equivalent GitHub Actions concept for each stage — proves the concepts transfer across tools.

### D. Project
See **Section 21, Milestone 4 & 5** (tests added, CI/CD pipeline built).

### E. Resources
| Resource | Priority | Notes |
|---|---|---|
| GitHub Actions official docs | **Essential** | Authoritative syntax/behavior reference. |
| IBM: *Continuous Integration and Continuous Delivery (CI/CD)* | **Essential** | Good for the conceptual vocabulary (stages, artifacts, deployment strategies) — pair every concept with the GitHub Actions equivalent yourself since the course may use Jenkins/other tooling. |
| IBM: *Introduction to Test and Behavior Driven Development* | **Supplementary** | Use for the BDD vocabulary (given/when/then) only; you already know how to write tests — skip basic unit-testing explanations. |
| freeCodeCamp: *Jenkins Tutorial — Deploy a Test Server with Docker and Linux* | **Supplementary** | Watch once for exposure/recognition of Jenkins syntax and the agent/runner concept; do not adopt Jenkins as your primary tool. |
| freeCodeCamp: *DevOps with GitLab CI — Build Pipelines and Deploy to AWS* | **Supplementary** | Useful for seeing an alternative YAML pipeline syntax and a GitLab-to-AWS deploy pattern; translate the concepts to GitHub Actions rather than switching tools. |
| `pytest`, `testcontainers-python` official docs | **Essential** | For integration testing against real containers. |

### F. Completion Criteria
- [ ] A PR with a failing test is automatically blocked from merging.
- [ ] A merge to `main` automatically builds, tests, and publishes a versioned image.
- [ ] Secrets are never visible in logs or committed to the repository.
- [ ] You have executed at least one real rollback (not just read about it).
- [ ] You can explain rolling vs. blue-green vs. canary deployment trade-offs without notes.

---

## Phase 5 — Cloud Fundamentals & Practical Deployment (AWS)

### A. Phase Overview
- **Duration:** 3 weeks.
- **Purpose:** Move from "runs on my machine/VM" to "runs on real cloud infrastructure reachable by anyone," and understand the building blocks (compute, network, storage, identity) that Terraform will soon automate.
- **Prerequisites:** Phases 1–4 (networking fundamentals, containerized app with CI/CD producing a deployable image).
- **At the end you can:** Explain core AWS services, manually provision a secure VM, deploy "Pulse" to it from your CI/CD pipeline, and expose it safely to the internet.

### B. Detailed Syllabus
- **Cloud computing concepts:** IaaS vs. PaaS vs. SaaS, shared responsibility model (what AWS secures vs. what you secure), regions vs. availability zones, elasticity vs. scalability.
- **Core AWS services for this roadmap (deliberately minimal set):**
  - **IAM** (preview now, formalized in Phase 8): users, groups, roles, policies — principle of least privilege from day one; never use the root account or long-lived access keys for daily work.
  - **VPC networking:** VPC, subnets (public/private), route tables, internet gateway, NAT gateway — mapped directly to the Phase 1 networking/subnetting knowledge.
  - **EC2:** instances, AMIs, instance types, key pairs (SSH), **Security Groups** (stateful firewall — direct application of Phase 1 firewall concepts) vs. **NACLs** (stateless).
  - **ECR** (Elastic Container Registry): private image registry, authentication (`aws ecr get-login-password`), replacing Docker Hub for private images.
  - **S3**: object storage, use case here = storing Terraform state later and backups.
  - **Elastic IP / Route 53 (conceptually):** stable addressing and DNS in the cloud, tying back to Phase 1 DNS knowledge.
  - **Billing/cost awareness:** free tier limits, setting a budget alarm — a genuinely important operational habit.
- **Manual deployment workflow (before automating it in Phase 6/7, intentionally):**
  - Launch an EC2 instance by hand, SSH in, install Docker, pull the image from ECR, run via Compose, expose via Security Group rules.
  - Point a domain (or subdomain, e.g., free DuckDNS if you don't own one) at the instance's IP and discuss DNS propagation.
  - Add Nginx for TLS termination via Let's Encrypt/Certbot — real HTTPS, real certificate chain, connects back to Phase 1 TLS concepts.
- **Why do this manually first:** you cannot appreciate (or safely use) Terraform/Ansible automation in Phase 6/7 until you've felt the pain of doing it by hand and understand exactly what is being automated.

### C. Practical Exercises
1. Create an IAM user with MFA and a scoped policy (not AdministratorAccess) for your own daily CLI use; explain why you didn't use root.
2. Design a VPC on paper first (CIDR ranges, public/private subnets) before creating it — review for addressing mistakes before touching the console/CLI.
3. Launch an EC2 instance in a public subnet with a Security Group allowing only SSH (restricted to your IP) and HTTP/HTTPS from anywhere; verify with `nmap`/`curl` from an external machine what is and isn't reachable.
4. Push "Pulse"'s image to ECR from your existing CI/CD pipeline (extend Phase 4's workflow).
5. SSH into the EC2 instance, deploy the full Compose stack, and make it reachable over HTTP, then HTTPS via Certbot.
6. **Break it on purpose:** remove the inbound HTTPS rule from the Security Group and diagnose the resulting failure as a network-layer (not app-layer) issue, using `curl -v` and `nc` to prove it.
7. **Break it on purpose:** let a Certbot certificate expire (or simulate by misconfiguring the renewal cron) and walk through diagnosing a TLS handshake failure.
8. Set a AWS budget alert at a low threshold and intentionally approach it (e.g., leave a small instance running) to see the notification flow.
9. **Independent challenge:** move the database to a private subnet with no direct internet route, and reconfigure the app/network so only the EC2 instance in the public subnet can reach it — prove external access to the DB port is impossible.

### D. Project
See **Section 21, Milestone 6** ("Pulse" live on a real AWS VM, HTTPS-enabled).

### E. Resources
| Resource | Priority | Notes |
|---|---|---|
| AWS official documentation + AWS Well-Architected basics | **Essential** | Authoritative and current; always verify exact console/CLI steps here since UI changes over time. |
| freeCodeCamp: *AWS Certified Cloud Practitioner course* | **Essential (selective)** | Use for the conceptual breadth (IAM, VPC, EC2, S3, shared responsibility); skip exam-cram sections you don't need and anything referencing discontinued services — verify against current AWS docs. |
| IBM: *Introduction to Cloud Computing* | **Supplementary** | Good for vendor-neutral cloud vocabulary (IaaS/PaaS/SaaS, elasticity) if you want a second explanation; skip if the Cloud Practitioner material already made sense. |
| freeCodeCamp: *AWS Certified Developer Associate course* | **Postpone/Optional** | Oriented at application developers using many managed AWS services (Lambda, DynamoDB, etc.) beyond this roadmap's scope; revisit only if you later specialize in AWS-heavy roles. |
| Let's Encrypt / Certbot official docs | **Essential** | For the real TLS exercise. |

### F. Completion Criteria
- [ ] Can explain shared responsibility model and justify every open Security Group rule on your instance.
- [ ] Deployed "Pulse" manually to a real EC2 instance, reachable over HTTPS with a valid certificate.
- [ ] Can diagnose a network-layer vs application-layer failure on a real cloud instance using the Phase 1 toolkit.
- [ ] Database is not reachable from the public internet — proven, not assumed.
- [ ] Has never used the AWS root account for routine work after the first setup.

---

## Phase 6 — Infrastructure as Code with Terraform

### A. Phase Overview
- **Duration:** 2–3 weeks.
- **Purpose:** Replace the manual, error-prone, undocumented clicking/CLI of Phase 5 with declarative, versioned, reproducible infrastructure definitions.
- **Prerequisites:** Phase 5 (you must know *what* you're automating — VPC, subnets, security groups, EC2, ECR — before Terraform hides the manual steps).
- **At the end you can:** Define your entire Phase 5 infrastructure as code, plan/apply changes safely, manage state, and tear down/recreate an identical environment on demand.

### B. Detailed Syllabus
- **Declarative vs. imperative infrastructure:** you describe the desired end state; Terraform computes the diff and the actions needed — contrast explicitly with the Phase 5 manual/imperative steps you just did.
- **Core workflow:** `terraform init`, `plan`, `apply`, `destroy`; the **plan output as a contract** — always read it before applying.
- **HCL fundamentals:** providers, resources, data sources, variables (`variable`, `.tfvars`), outputs, locals.
- **State:** what the state file is and why it exists (mapping config to real resource IDs), state drift (someone changes infra manually — you will reproduce this on purpose), remote state backend (S3 + DynamoDB for locking) and why local state doesn't work in a team.
- **Modules:** why and when to modularize (reusable VPC module, reusable EC2 module), module inputs/outputs.
- **Dependency graph:** implicit dependencies via resource references vs. explicit `depends_on`.
- **Workspaces/environments:** separating dev/staging/prod configuration without duplicating all code.
- **Secrets in Terraform:** never commit `.tfvars` with secrets, use environment variables or a secrets backend (ties to Phase 8), `sensitive = true` outputs.
- **Common failure modes:** partial apply failures (resource created, then error — now in a half-applied state), state file corruption/loss, drift, destroying the wrong workspace.

### C. Practical Exercises
1. Reproduce the entire Phase 5 manual infrastructure (VPC, subnets, IGW, route tables, Security Groups, EC2, ECR repo) as Terraform code.
2. `terraform destroy` the whole environment, then `terraform apply` again from scratch and confirm "Pulse" comes back up identically — this is the actual proof of "infrastructure as code," not just writing `.tf` files.
3. **Break it on purpose:** manually change a Security Group rule in the AWS console, then run `terraform plan` and observe/explain the detected drift.
4. **Break it on purpose:** corrupt/delete your local state file (after backing it up) and recover using a remote backend you set up, or `terraform import` a resource back into management.
5. Extract the VPC definition into a reusable module with variables for CIDR ranges; instantiate it twice (e.g., a "staging" and "prod" mini-VPC) to prove reusability.
6. Set up remote state in S3 with DynamoDB locking; have two terminal sessions attempt `apply` simultaneously and observe the lock in action.
7. **Independent challenge:** modify the Terraform config to also provision a second, smaller EC2 instance purely from a variable flag (`var.enable_staging = true/false`) without duplicating resource blocks.

### D. Project
See **Section 21, Milestone 7** (infrastructure fully codified).

### E. Resources
| Resource | Priority | Notes |
|---|---|---|
| Official Terraform documentation (developer.hashicorp.com) | **Essential** | Primary, authoritative, and current reference for syntax and provider resources. |
| freeCodeCamp: *Learn Terraform and AWS by Building a Dev Environment* | **Essential** | Directly hands-on and aligned with this phase's goals; implement the same patterns against your own Phase 5 infra instead of a throwaway example. |
| freeCodeCamp: *Infrastructure as Code Crash Course* | **Supplementary** | Useful only if it covers concepts beyond Terraform-AWS course above (e.g., broader IaC philosophy); skip duplicated material. |
| AWS Provider docs (registry.terraform.io/providers/hashicorp/aws) | **Essential** | Exact resource arguments for VPC/EC2/ECR/S3/DynamoDB. |

### F. Completion Criteria
- [ ] Entire Phase 5 infrastructure exists as versioned `.tf` files in Git, with no manually-created resources remaining.
- [ ] Can destroy and recreate the full environment and have the app come back online with zero manual console steps.
- [ ] Can explain state, drift, and remote locking, and has caused + resolved drift at least once.
- [ ] Uses at least one custom module.
- [ ] No secrets committed to the Terraform repository.

---

## Phase 7 — Configuration Management with Ansible

### A. Phase Overview
- **Duration:** 1–2 weeks (shorter — builds directly on Bash/Python/SSH fluency from Phase 1).
- **Purpose:** Terraform provisions *infrastructure* (the VM exists); Ansible configures *what's inside it* (packages, Docker installed, app deployed, config files templated) — idempotently and repeatably, replacing the manual SSH steps from Phase 5.
- **Prerequisites:** Phase 6 (an EC2 instance to target), Phase 1 (SSH, Bash, YAML-adjacent thinking).
- **At the end you can:** Bootstrap a brand-new server from zero to running "Pulse" with a single Ansible playbook run, idempotently.

### B. Detailed Syllabus
- **Agentless architecture:** Ansible connects over SSH and runs Python on the target — explain why this matters (no extra daemon to maintain, matches your Python background since Ansible modules are Python under the hood).
- **Inventory:** static INI/YAML inventory, dynamic inventory (AWS EC2 plugin) to avoid hardcoding IPs that Terraform just created — a direct Terraform→Ansible handoff point (Terraform output → Ansible inventory).
- **Playbooks, plays, tasks, modules:** YAML structure, idempotent modules (`apt`, `docker_container`, `copy`, `template`, `service`) vs. the anti-pattern of raw `shell`/`command` tasks that aren't idempotent.
- **Idempotency in depth:** running the same playbook twice must produce the same result with the second run reporting no changes — verify this explicitly, don't assume it.
- **Variables & templating:** `vars`, `group_vars`/`host_vars`, Jinja2 templates (e.g., templating an Nginx config or `.env` file from variables).
- **Roles:** structuring reusable, shareable playbook components (`roles/docker/tasks/main.yml`, etc.).
- **Handlers:** triggering a service restart only when a config file actually changes.
- **Vault:** `ansible-vault` for encrypting secrets within playbooks/variable files (connects to Phase 8).
- **Error handling:** `ignore_errors`, `failed_when`, `changed_when`, check mode (`--check`) as a "dry run."

### C. Practical Exercises
1. Write a playbook that, on a brand-new Terraform-provisioned EC2 instance, installs Docker, pulls the latest "Pulse" image from ECR, and starts the Compose stack — zero manual SSH.
2. Run the playbook twice in a row; confirm the second run reports `changed=0` for already-satisfied tasks — if it doesn't, find and fix the non-idempotent task.
3. Use a Jinja2 template to generate the Nginx config from variables (domain name, backend port) instead of a static file.
4. Add a handler that restarts Nginx only when its templated config file changes, and prove it does *not* restart when unrelated tasks run.
5. Encrypt the database password with `ansible-vault` and reference it in a task; demonstrate the playbook fails safely without the vault password.
6. **Break it on purpose:** introduce a task using a non-idempotent raw `shell` command (e.g., `shell: echo "line" >> file`) and show how repeated runs corrupt state; fix it using the proper idempotent module/pattern.
7. Connect Terraform's output (instance IP) directly into Ansible's dynamic inventory (or a generated inventory file) so you never manually copy-paste an IP address again.
8. **Independent challenge:** convert your playbook into roles (`common`, `docker`, `app`) and reuse the `docker` role on a second, differently-purposed VM.

### D. Project
See **Section 21, Milestone 7 (extended)** — Terraform + Ansible together form the full "provision + configure" pipeline.

### E. Resources
| Resource | Priority | Notes |
|---|---|---|
| Official Ansible documentation (docs.ansible.com) | **Essential** | Authoritative module reference and best-practice guides. |
| General Ansible+Terraform integration guides (official HashiCorp/Ansible blog posts) | **Supplementary** | For the dynamic inventory hand-off pattern specifically. |

*Note: no freeCodeCamp/IBM course in the provided lists specifically targets Ansible in depth — official documentation plus applying it directly to your own Terraform-provisioned infrastructure is the most reliable path here.*

### F. Completion Criteria
- [ ] A brand-new EC2 instance goes from "just created by Terraform" to "running Pulse" via a single `ansible-playbook` command.
- [ ] Running the playbook twice produces zero unnecessary changes on the second run.
- [ ] Secrets in the playbook are vault-encrypted, not plaintext.
- [ ] Playbook is organized into roles.
- [ ] Can explain, concretely, the division of responsibility between Terraform and Ansible.

---

## Phase 8 — Cloud Security, IAM & Secrets Management

### A. Phase Overview
- **Duration:** 1–2 weeks (concentrated hardening pass — security concepts have already been introduced incrementally since Phase 5; this phase formalizes and audits them).
- **Purpose:** DevOps engineers are frequently the last line of defense against basic misconfigurations (open databases, leaked keys, overly broad IAM). This phase converts "it works" into "it's defensible."
- **Prerequisites:** Phases 5–7 (real infrastructure and deployment pipeline to audit).
- **At the end you can:** Perform a basic security audit of your own stack, apply least privilege throughout, and manage secrets without ever committing them to Git.

### B. Detailed Syllabus
- **IAM deep dive:** users vs. roles vs. policies, policy evaluation logic (explicit deny always wins), instance profiles/roles for EC2 (so the app/Ansible never needs long-lived access keys on the box), cross-account/service roles conceptually.
- **Principle of least privilege, applied:** audit every IAM policy, Security Group, and Ansible/Terraform credential you've created since Phase 5 and tighten anything broader than necessary.
- **Secrets management:** why `.env` files committed to Git are a recurring real-world breach cause; options in increasing sophistication — environment variables injected at deploy time → `ansible-vault` → AWS Secrets Manager/SSM Parameter Store (pick one managed option and implement it for at least the DB password).
- **Network hardening recap and formalization:** confirm database is still private-subnet-only, confirm Security Groups are least-privilege, confirm SSH is key-only.
- **Application security basics (DevSecOps entry point):** OWASP Top 10 categories relevant to a typical web API (injection, broken auth, sensitive data exposure, security misconfiguration), dependency scanning (`pip-audit`/`safety`) added as a CI step, container image scanning (already started in Phase 2) made a required CI gate, not just a manual check.
- **Secrets scanning in CI:** add a pre-commit or CI step (e.g., `gitleaks`) that fails the pipeline if a secret pattern is detected in a diff.
- **Audit logging concept:** AWS CloudTrail as the record of "who did what" — enable it and inspect an entry.

### C. Practical Exercises
1. List every IAM policy/role created so far; for each, justify why it needs every permission it has, and remove anything unused.
2. Replace any long-lived AWS access key used by the EC2 instance/Ansible with an **instance role**, and prove the app still works without a key stored on disk.
3. Move the database password out of `ansible-vault`/`.env` into AWS SSM Parameter Store (or Secrets Manager); update the deployment so the app fetches it at runtime or injection time.
4. Add `gitleaks` (or similar) to the CI pipeline and prove it blocks a commit containing a fake AWS key pattern.
5. Add `pip-audit` to CI and fix any reported vulnerable dependency in "Pulse."
6. Make container image scanning (Phase 2) a **required, failing** CI check instead of a manual step.
7. **Break it on purpose, then fix it:** temporarily widen a Security Group to `0.0.0.0/0` on the database port, confirm external reachability with a tool from an outside machine (e.g., `nc`/`nmap` from a separate VM or online port-checker), then revert and document the exposure window as if writing an incident report.
8. Enable CloudTrail and find the log entry corresponding to one of your own `terraform apply` runs.

### D. Project
Security hardening pass applied across all "Pulse" infrastructure (folds into Section 21/22 as a cross-cutting milestone, not a separate app).

### E. Resources
| Resource | Priority | Notes |
|---|---|---|
| IBM: *Application Security for Developers and DevOps Professionals* | **Essential (selective)** | Focus on OWASP Top 10 and secure SDLC concepts; skip language-specific sections not relevant to Python if present. |
| freeCodeCamp: *Web Application Vulnerabilities — DevSecOps Course* | **Essential (selective)** | Use for hands-on exploitation/defense understanding of common web vulnerabilities; apply findings directly against "Pulse" rather than a throwaway app. |
| AWS IAM & Secrets Manager official docs | **Essential** | Exact, current policy syntax and service behavior. |
| `gitleaks`, `trivy`, `pip-audit` documentation | **Essential** | For the CI-gating exercises. |

### F. Completion Criteria
- [ ] No IAM policy in use grants more than what is actually exercised.
- [ ] No long-lived AWS access keys exist on any server.
- [ ] No secret exists in plaintext in Git history (verified with a scan, not assumed).
- [ ] CI pipeline fails the build on a leaked secret, a critical dependency CVE, or a critical image vulnerability.
- [ ] Can explain, with a real example from your own project, one OWASP Top 10 risk and its mitigation.

---

## Phase 9 — Monitoring, Logging & Observability

### A. Phase Overview
- **Duration:** 2 weeks.
- **Purpose:** You cannot operate what you cannot see. This phase adds the feedback loop that turns "deploy and hope" into "deploy and know."
- **Prerequisites:** A running, deployed "Pulse" stack (Phases 5–8).
- **At the end you can:** Instrument an application with metrics, collect and visualize them, centralize logs, and configure alerts that distinguish real incidents from noise.

### B. Detailed Syllabus
- **The three pillars:** metrics (numeric, aggregable over time), logs (discrete, detailed events), traces (request path across services, introduced conceptually — full distributed tracing is Advanced/Optional). Explain what each answers and what it can't.
- **Metrics with Prometheus:** pull-based scraping model, `/metrics` endpoint exposition format, instrumenting "Pulse" with `prometheus_client` (Python) to expose request counts, latency histograms, and error rates (RED method: Rate, Errors, Duration), `node_exporter` for host-level metrics (CPU, memory, disk — ties back to Phase 1 resource concepts), scrape configs and targets.
- **Visualization with Grafana:** connecting Prometheus as a data source, building a dashboard from scratch (not importing a pre-made one, at least initially) so panel/query logic is understood, PromQL basics (rate, histogram_quantile).
- **Logging:** structured logging (JSON logs) in "Pulse" instead of free-text prints, centralizing container logs (Docker `json-file` driver limitations, forwarding to a simple stack — e.g., Loki + Promtail, chosen for consistency with the Prometheus/Grafana ecosystem), correlating a log line with a specific request/trace ID.
- **Alerting:** Prometheus Alertmanager, writing an alert rule (e.g., error rate > 5% for 5 minutes, or instance down), routing to a notification channel (email/Slack/webhook), and the critical discipline of avoiding alert fatigue (alert on symptoms that matter to users, not on every possible metric).
- **SLIs/SLOs (conceptual introduction):** what a Service Level Indicator/Objective is and why alerting should be tied to them rather than arbitrary thresholds.
- **Connecting back to earlier phases:** a Docker container exit code 137 (Phase 2) should now show up as an actual host OOM metric spike in Grafana — tie the layers together explicitly.

### C. Practical Exercises
1. Instrument "Pulse" to expose a `/metrics` endpoint with at least request count, latency histogram, and error count.
2. Deploy Prometheus (via Compose, alongside "Pulse") and confirm it's scraping successfully (`up == 1` in Prometheus's own UI).
3. Build a Grafana dashboard from scratch showing request rate, error rate, and p95 latency using PromQL you wrote yourself.
4. Add `node_exporter`; build a second dashboard panel for CPU/memory/disk of the host.
5. Generate artificial load (a simple script hammering an endpoint) and watch metrics change in real time; correlate a deliberate memory-limited container crash (from Phase 2) with a metrics spike before the crash.
6. Switch "Pulse" logging to structured JSON; ship logs to Loki via Promtail; query logs filtered by a specific status code in Grafana's log view.
7. Write a Prometheus alert rule for "error rate too high" and one for "instance down"; trigger each deliberately (inject errors; stop the container) and confirm the alert fires and routes correctly.
8. **Break it on purpose:** misconfigure a Prometheus scrape target (wrong port) and diagnose the "target down" state using Prometheus's own target page plus the Phase 1 networking toolkit.
9. **Independent challenge:** define one SLO for "Pulse" (e.g., "99% of requests succeed in under 300ms over 24h") and build a dashboard panel that directly shows current standing against that SLO.

### D. Project
See **Section 21, Milestone 8** (full observability stack layered onto "Pulse").

### E. Resources
| Resource | Priority | Notes |
|---|---|---|
| Official Prometheus documentation | **Essential** | PromQL and exposition format reference. |
| Official Grafana documentation | **Essential** | Dashboard/data source reference. |
| IBM: *Monitoring and Observability for Development and DevOps* | **Essential (selective)** | Good for the conceptual framing (three pillars, SLI/SLO); pair every concept with a hands-on Prometheus/Grafana equivalent since the course may reference different vendor tooling. |
| `prometheus_client` Python library docs | **Essential** | For instrumenting "Pulse" directly. |
| Grafana Loki + Promtail official docs | **Supplementary** | For the structured-logging/centralization exercise; treat as "good enough" for a portfolio project rather than a production-grade logging platform (e.g., ELK) which is Advanced/Optional. |

### F. Completion Criteria
- [ ] "Pulse" exposes real, meaningful metrics (not just a dummy counter).
- [ ] A from-scratch Grafana dashboard (not imported) shows rate, errors, and latency.
- [ ] At least two alert rules exist and have been proven to fire correctly.
- [ ] Logs are structured and centrally queryable.
- [ ] Can explain the difference between a metric, a log, and a trace, and when each is the right tool.

---

## Phase 10 — Kubernetes & Container Orchestration

### A. Phase Overview
- **Duration:** 3–4 weeks (the largest single phase — deliberately, since this is usually the biggest knowledge gap for junior DevOps candidates).
- **Purpose:** Move from manually/Ansible-managed single-VM deployment to an orchestrated platform that handles scheduling, self-healing, scaling, and rolling updates for you — and understand *exactly* what it's doing under the hood instead of treating it as magic.
- **Prerequisites:** Phases 2–4 (deep Docker/Compose/CI fluency is mandatory), Phase 9 helpful but not blocking (you'll re-apply monitoring concepts inside K8s).
- **At the end you can:** Deploy "Pulse" to a local Kubernetes cluster with correct resource requests/limits, configuration, secrets, networking, and self-healing, and diagnose common Pod failures independently.

### B. Detailed Syllabus
- **Why Kubernetes exists:** the problems it solves that Compose/Ansible on a single VM cannot — multi-node scheduling, self-healing, declarative desired-state reconciliation, horizontal scaling, rolling updates with automatic rollback. Be explicit that Kubernetes is **not** always the right answer, and a single well-run VM is often sufficient for small systems (important maturity point for an interview).
- **Local cluster setup:** `kind` or `minikube` (choose one; `kind` recommended since it runs K8s-in-Docker, directly building on Phase 2 knowledge), `kubectl` context/config.
- **Core objects:**
  - **Pod:** smallest deployable unit, one or more containers sharing network namespace — connect directly to Phase 1 namespace knowledge.
  - **Deployment & ReplicaSet:** desired-state reconciliation loop, rolling update strategy (`maxSurge`/`maxUnavailable`), rollback (`kubectl rollout undo`).
  - **Service:** ClusterIP, NodePort, LoadBalancer — stable virtual IP + DNS name for a changing set of Pods; kube-proxy and how Service load-balancing actually works (iptables/IPVS rules) — ties to Phase 1 networking.
  - **Ingress & Ingress Controller:** HTTP(S) routing into the cluster, direct conceptual successor to the Nginx reverse proxy from Phase 3/5, TLS termination at the ingress.
  - **ConfigMap & Secret:** externalized configuration, mounted as env vars or files; Secret base64-encoding is **not** encryption — explain this precisely (ties to Phase 8 secrets discipline).
  - **Namespaces:** logical isolation of resources within a cluster.
  - **Volumes & PersistentVolume/PersistentVolumeClaim/StorageClass:** how Kubernetes abstracts storage, relevant for the database component of "Pulse."
  - **Probes:** `livenessProbe`, `readinessProbe`, `startupProbe` — direct evolution of the Docker `HEALTHCHECK` concept, now actively used by the scheduler/Service to make routing and restart decisions.
  - **Resource requests & limits:** CPU/memory requests (scheduling hint) vs. limits (hard cap), and what happens when a Pod exceeds its memory limit (OOMKilled — same concept as Phase 2's exit 137, now at the orchestrator level).
  - **DNS inside Kubernetes:** CoreDNS, Service DNS names (`service.namespace.svc.cluster.local`) — direct continuation of Phase 2/3 container DNS concepts.
- **Scheduling basics:** how the scheduler picks a node (conceptual), node affinity/taints-tolerations (awareness level only).
- **kubectl workflow:** `apply -f`, `get`, `describe`, `logs`, `exec`, `port-forward`, `rollout status/undo`, `top` (with metrics-server).
- **Manifests as code:** plain YAML first (mandatory, to understand the raw API), Kustomize overlays for environment differences (lightweight introduction before Helm in Phase 11).

### C. Practical Exercises
1. Deploy "Pulse" to `kind` as a single Pod via a raw YAML manifest (no Deployment yet); delete the Pod and observe it does **not** come back — explain why, and fix it by wrapping it in a Deployment.
2. Scale the Deployment to 3 replicas; kill one Pod manually (`kubectl delete pod`) and observe self-healing.
3. Expose "Pulse" via a ClusterIP Service, then `port-forward` to it; then switch to an Ingress Controller (e.g., ingress-nginx) and reach it via a hostname.
4. Externalize all configuration into a ConfigMap and the DB password into a Secret; prove the app fails cleanly (not crash-loop silently) if the Secret is missing.
5. Add `readinessProbe` and `livenessProbe`; **break it on purpose** by making the readiness check depend on the database, then kill the database Pod and observe "Pulse" Pods removed from Service routing (but not restarted) — explain the readiness vs. liveness distinction concretely from this observation.
6. Set a memory limit lower than the app needs; observe `OOMKilled` status in `kubectl describe pod`, and correlate with the Phase 2/9 OOM knowledge.
7. **Troubleshooting scenario (classic "CrashLoopBackOff," diagnose independently):** deploy a Pod with a deliberately wrong environment variable causing the app to exit immediately on startup; use `kubectl describe`, `kubectl logs --previous`, and event inspection to find the root cause without being told what's wrong.
8. **Troubleshooting scenario ("ImagePullBackOff"):** reference a nonexistent image tag and diagnose using `kubectl describe pod` events.
9. **Troubleshooting scenario ("Pending" Pod):** request more CPU/memory than the cluster node has available and diagnose via `kubectl describe pod` and `kubectl describe node`.
10. Add the PostgreSQL database as a StatefulSet (or acknowledge and document why you might instead keep the DB external/managed — a legitimate real-world decision) with a PersistentVolumeClaim; delete the Pod and confirm data persists.
11. Perform a rolling update by changing the image tag; watch `kubectl rollout status`; then deliberately deploy a broken image tag and execute `kubectl rollout undo`.
12. Re-deploy the Phase 9 monitoring approach: run `kube-state-metrics` + Prometheus inside or alongside the cluster and confirm you can see Kubernetes-level metrics (Pod restarts, resource usage) in Grafana.

### D. Project
See **Section 21, Milestone 9** ("Pulse" running on Kubernetes with self-healing, probes, and persistent storage).

### E. Resources
| Resource | Priority | Notes |
|---|---|---|
| Official Kubernetes documentation (kubernetes.io/docs) | **Essential** | The single most reliable reference; concepts and API fields change between versions, always check here. |
| freeCodeCamp: *Kubernetes Course — Full Beginners Tutorial* | **Essential** | Strong hands-on foundation; implement every exercise against "Pulse" instead of (or in addition to) the course's example app. |
| freeCodeCamp: *Kubernetes and Cloud Native Associate (KCNA) course* | **Supplementary** | Good for filling conceptual breadth (cloud-native landscape, CNCF projects) and validating your understanding; treat the certification itself as optional — it is an associate-level, vendor-neutral exam and not a hard requirement for junior roles. Verify current exam domains on the CNCF site if you decide to pursue it. |
| IBM: *Introduction to Containers with Docker, Kubernetes & OpenShift* (Kubernetes/OpenShift modules, postponed from Phase 2) | **Supplementary** | Now revisit the Kubernetes and OpenShift sections you skipped earlier; OpenShift itself is **not** a required tool for this roadmap — treat it as "know Kubernetes is at its core, aware of enterprise differences." |

### F. Completion Criteria
- [ ] Can deploy "Pulse" to a clean local cluster from manifests with zero manual `kubectl` troubleshooting steps needed afterward.
- [ ] Has independently diagnosed CrashLoopBackOff, ImagePullBackOff, and Pending-due-to-resources without being told the cause in advance.
- [ ] Can explain readiness vs. liveness probes using a real observed example from your own cluster.
- [ ] Has performed a rolling update and a rollback.
- [ ] Can explain when Kubernetes is *not* the right choice for a project.

---

## Phase 11 — Helm, GitOps & Advanced Delivery

### A. Phase Overview
- **Duration:** 2 weeks.
- **Purpose:** Now that you can hand-write and debug raw Kubernetes YAML, learn the templating and automation layers that make multi-environment, auditable deployments practical at scale.
- **Prerequisites:** Phase 10 fully complete — Helm/GitOps over manifests you don't understand is cargo-culting, not DevOps.
- **At the end you can:** Package "Pulse" as a Helm chart with environment-specific values, and set up a GitOps workflow where Git is the single source of truth for what's deployed.

### B. Detailed Syllabus
- **Helm:** charts, templates (Go templating over YAML), `values.yaml` and overrides per environment, `helm install/upgrade/rollback`, chart versioning, why this is preferable to copy-pasted YAML across environments (direct echo of the Kustomize preview from Phase 10, now compared against templating).
- **GitOps principles:** Git as the single source of truth for desired cluster state; a controller (ArgoCD, chosen as the primary tool — widely adopted, visual, CNCF project) continuously reconciles actual cluster state to match the Git repo; the key shift from "CI pushes to the cluster" (Phase 10's manual `kubectl apply`/CI deploy) to "a controller pulls from Git" — explain the security benefit (no cluster credentials needed in CI).
- **App-of-apps / repo structure patterns:** separating application code repo from a "deployment manifests" repo (or a clearly separated directory), environment promotion via Git (merge/PR from a staging branch/folder to a prod one).
- **Progressive delivery concepts (awareness level):** canary releases and automated analysis (e.g., Argo Rollouts/Flagger) — know what they are and why they exist; full hands-on mastery is Advanced/Optional.
- **Secrets in GitOps:** the specific problem of "Git is the source of truth but Secrets shouldn't be plaintext in Git" — know at least one solution exists (Sealed Secrets or External Secrets Operator pulling from Phase 8's AWS Secrets Manager) at an awareness level.

### C. Practical Exercises
1. Convert your raw "Pulse" Kubernetes manifests into a Helm chart with templated values for image tag, replica count, and resource limits.
2. Deploy the same chart with different `values-staging.yaml` and `values-prod.yaml` files, proving one chart serves multiple environments.
3. Deliberately break a template (bad Go template syntax) and diagnose using `helm template`/`helm lint` before ever touching the cluster.
4. Install ArgoCD in your local cluster; point it at a Git repo containing your Helm chart; make a change by editing Git (not `kubectl`) and watch ArgoCD reconcile it automatically.
5. **Break it on purpose:** manually `kubectl edit` a Deployment that ArgoCD manages, and observe/explain ArgoCD reverting the drift — the GitOps enforcement loop made visible.
6. Perform a rollback purely through Git (revert a commit) instead of `kubectl`/`helm` commands directly, and confirm ArgoCD applies the reverted state.
7. **Independent challenge:** structure a `staging` and `prod` folder/branch promotion flow and document the exact Git-based steps to promote a new "Pulse" version from staging to prod.

### D. Project
See **Section 21, Milestone 10** (Helm chart + ArgoCD-managed deployment).

### E. Resources
| Resource | Priority | Notes |
|---|---|---|
| Official Helm documentation | **Essential** | Chart structure and templating reference. |
| Official ArgoCD documentation | **Essential** | Installation and application CRD reference. |
| OpenGitOps / CNCF GitOps principles (opengitops.dev) | **Supplementary** | For precise, vendor-neutral GitOps definitions if you want the formal principles. |

*Note: no resource in the provided IBM/freeCodeCamp lists specifically covers Helm or GitOps/ArgoCD — official documentation plus direct application to "Pulse" is the correct path.*

### F. Completion Criteria
- [ ] "Pulse" is packaged as a working, linted Helm chart deployable to at least two differently-configured environments.
- [ ] ArgoCD is managing the deployment, and a Git commit — not a manual `kubectl`/`helm` command — is the only way changes are intended to reach the cluster.
- [ ] Has observed and can explain ArgoCD reverting manual drift.
- [ ] Can execute a rollback via Git revert alone.

---

## Phase 12 — Capstone & Portfolio Readiness

### A. Phase Overview
- **Duration:** 3–4 weeks.
- **Purpose:** Consolidate every phase into one coherent, documented, defensible system, and prepare the GitHub portfolio and personal narrative for internship/junior role applications.
- **Prerequisites:** All previous phases.
- **At the end you can:** Explain and defend an end-to-end production-style system, from a cold clone to a monitored, secured, auto-deployed Kubernetes application, in a technical interview setting.

### B. What happens in this phase
This phase has no new *tools* — it is integration, documentation, polish, failure-injection testing across the whole stack, and interview preparation. See **Section 22** for the full capstone specification and **Section 24/25** for portfolio and skills-matrix expectations.

### C. Completion Criteria
- [ ] A reviewer can clone your capstone repo and, following only your README, get the full system running locally and understand how it reaches production.
- [ ] You can whiteboard the architecture from memory and explain every component's purpose and alternative choices considered.
- [ ] You have injected and recovered from at least 5 of the failure scenarios in Section 22 and documented each as a mini incident report.
- [ ] Your GitHub profile demonstrates a progression (Pulse v1 → v2 → ... → capstone), not just one isolated final repo.

---

## 18. Advanced & Optional Topics

These are **not required** to be hireable as a *junior* DevOps engineer. Learn them only after the core (Phases 0–12) is solid, and prioritize based on the specific jobs you're targeting.

| Topic | Treatment | When / Why |
|---|---|---|
| Service mesh (Istio/Linkerd) | Conceptual only, then hands-on if targeting platform/SRE-heavy roles | Solves cross-service mTLS, traffic shaping, and observability at a scale (many microservices) that a junior portfolio project won't have. Learn *after* Kubernetes networking (Phase 10) is second nature. |
| Serverless (AWS Lambda, API Gateway) & microservices patterns | Conceptual now (via IBM course below), hands-on optional | Valid, common pattern but a different operational model from the container-centric path this roadmap builds; worth a small side project once Phase 5 cloud fundamentals are solid. |
| Multi-cloud (Azure, GCP) | Conceptual awareness only | Switching clouds after mastering one is a vocabulary/API exercise, not a new conceptual framework. Only specialize in a second cloud if a specific job requires it. |
| OpenStack | Conceptual awareness only | Relevant mainly to organizations running private clouds; not a common requirement for junior cloud-native DevOps roles. The freeCodeCamp OpenStack tutorial is optional exposure, not a priority. |
| KCNA / other certifications | Optional validation, not a prerequisite | Useful as structured revision and a resume line once the hands-on skills already exist; never substitute for the projects in this roadmap. |
| Advanced progressive delivery (Argo Rollouts/Flagger, automated canary analysis) | Hands-on optional | Natural next step after Phase 11 GitOps basics, valuable for SRE-track roles. |
| ELK/EFK stack, distributed tracing (OpenTelemetry, Jaeger) | Conceptual now, hands-on optional | Prometheus/Grafana/Loki (Phase 9) is sufficient for junior-level observability competency; add tracing once working with genuinely distributed microservices. |
| Chaos engineering (e.g., Chaos Mesh) | Optional, advanced | A natural extension of the "break it on purpose" philosophy already baked into this roadmap — pursue once the capstone is stable enough to intentionally destabilize further. |
| Cost optimization / FinOps | Conceptual awareness now, deepen on the job | Budget-alarm habit from Phase 5 is the practical minimum for a junior role. |
| "Code Your Own Heroku Clone with Python" (freeCodeCamp) | Optional, excellent *review* exercise | A genuinely good capstone-adjacent exercise for reinforcing containers + orchestration + deployment concepts in a from-scratch way; do it for fun/review after Phase 10 if you want a deeper systems-level understanding of what PaaS platforms automate, not as a replacement for the main roadmap projects. |

---

## 19. IBM Course Mapping

| Course | Verdict | Where / How |
|---|---|---|
| 1. Introduction to DevOps | **Selective** | Skim once for vocabulary/history; you'll learn the substance by doing Phases 1–12. |
| 2. Introduction to Cloud Computing | **Supplementary** | Phase 5, if you want a second, vendor-neutral explanation alongside the AWS-specific course. |
| 3. Introduction to Agile Development and Scrum | **Optional** | Useful workplace context (sprints, standups, backlogs) but not a hands-on DevOps skill; read once, don't spend study hours here. |
| 4. Introduction to Software Engineering | **Skip** | Redundant with your existing project experience at 1337. |
| 5. Getting Started with Git and GitHub | **Selective** | Phase 1, branching/PR-workflow sections only. |
| 6. Hands-on Introduction to Linux Commands and Shell Scripting | **Selective** | Phase 1, gaps only (systemd, signals, scripting patterns). |
| 7. Python for Data Science, AI & Development | **Skip** | You already write Python; this course targets different goals (data science) than DevOps automation. |
| 8. Developing AI Applications with Python and Flask | **Skip** (or optional) | Not DevOps-focused; only relevant if "Pulse" needs a Flask refresher, which your background likely doesn't. |
| 9. Introduction to Containers with Docker, Kubernetes & OpenShift | **Essential (split)** | Docker module → Phase 2. Kubernetes/OpenShift modules → Phase 10 (postponed deliberately). |
| 10. Application Development using Microservices and Serverless | **Postpone/Optional** | Advanced/Optional topics (Section 18), after the core roadmap. |
| 11. Introduction to Test and Behavior Driven Development | **Supplementary** | Phase 4, BDD vocabulary only. |
| 12. Continuous Integration and Continuous Delivery (CI/CD) | **Essential** | Phase 4, conceptual vocabulary mapped onto GitHub Actions. |
| 13. Application Security for Developers and DevOps Professionals | **Essential (selective)** | Phase 8, OWASP Top 10 and secure SDLC sections. |
| 14. Monitoring and Observability for Development and DevOps | **Essential (selective)** | Phase 9, conceptual framing paired with Prometheus/Grafana hands-on. |
| 15. DevOps Capstone Project | **Optional reference** | Compare its structure against Section 22's capstone for ideas, but build your own capstone around "Pulse" rather than IBM's prescribed app so the skills compound on your existing portfolio. |

---

## 20. freeCodeCamp Video Mapping

| Resource | Verdict | Where / How |
|---|---|---|
| DevOps Prerequisites Course — Getting Started with DevOps | Supplementary | Phase 1 orientation only. |
| Docker Tutorial for Beginners — Full DevOps Course | **Essential** | Phase 2–3. |
| DevOps Engineering Course for Beginners | Supplementary | Use for broad orientation/cross-check against this roadmap's structure; expect overlap with other listed videos — skip repeated material. |
| AWS Certified Cloud Practitioner course | **Essential (selective)** | Phase 5. |
| AWS Certified Developer Associate course | Postpone/Optional | Section 18, revisit if specializing in AWS application services. |
| Kubernetes Course — Full Beginners Tutorial | **Essential** | Phase 10. |
| Azure Developer Associate course | Skip for now | Multi-cloud is Section 18; only pursue if a target job specifically requires Azure. |
| DevOps with GitLab CI — Build Pipelines and Deploy to AWS | Supplementary | Phase 4, for exposure to an alternative CI/CD syntax; don't adopt GitLab CI as your primary tool. |
| Docker with Node.js and Express | Optional | Phase 2, only if you want a second worked containerization example. |
| OpenStack Tutorial | Optional | Section 18, conceptual awareness only. |
| Kubernetes and Cloud Native Associate (KCNA) course | Supplementary | Phase 10, for breadth/cloud-native vocabulary; certification itself optional. |
| Learn Terraform and AWS by Building a Dev Environment | **Essential** | Phase 6. |
| Jenkins Tutorial — Deploy a Test Server with Docker and Linux | Supplementary | Phase 4, for recognition/reading ability, not primary tool adoption. |
| Learn Docker — Full DevOps Course for Deploying Containerized Apps | Supplementary | Phase 2–3, deployment-oriented sections only (overlaps with the beginner Docker course). |
| Web Application Vulnerabilities — DevSecOps Course | **Essential (selective)** | Phase 8. |
| AWS CDK Crash Course | Optional | Section 18 awareness; CDK is an alternative to Terraform — don't split focus across two IaC tools during the core roadmap. |
| Infrastructure as Code Crash Course | Supplementary | Phase 6, only the parts not already covered by the Terraform+AWS course. |
| Code Your Own Heroku Clone with Python | Optional (great review) | Section 18, post-Phase 10 systems-understanding exercise. |

---

## 21. The Progressive Portfolio Project: "Pulse"

### Why one evolving project instead of many disconnected ones
Switching apps every phase means re-learning the app instead of the tool. "Pulse" is deliberately simple so every new DevOps concept is the only new variable.

### What "Pulse" is
A small Python web API — a **URL shortener with click analytics** — because it naturally needs: a web server, a relational database (URL mappings), a cache (hot-URL lookups), background counting (click events), and produces genuinely meaningful metrics (requests, redirects, cache hit ratio, error rate) for the observability phase.

**Core features (deliberately minimal, built in Phase 1, never rewritten — only re-packaged/deployed):**
- `POST /shorten` — accepts a long URL, returns a short code.
- `GET /<code>` — redirects to the original URL, increments a click counter.
- `GET /stats/<code>` — returns click count and creation date.
- `GET /health` — liveness/readiness-friendly health endpoint (checks DB + cache connectivity).
- `GET /metrics` — Prometheus exposition format (added in Phase 9).

**Suggested structure:**
```
pulse/
├── app/
│   ├── __init__.py
│   ├── main.py          # Flask/FastAPI app factory
│   ├── routes.py
│   ├── db.py            # SQLAlchemy models / connection
│   ├── cache.py         # Redis client wrapper
│   └── config.py        # env-based configuration
├── tests/
│   ├── unit/
│   └── integration/
├── Dockerfile
├── docker-compose.yml
├── docker-compose.override.yml
├── .env.example
├── requirements.txt
├── nginx/
│   └── nginx.conf
├── terraform/
├── ansible/
├── k8s/
│   ├── base/
│   └── overlays/
├── helm/pulse/
├── .github/workflows/
└── README.md
```

### Milestone-by-milestone evolution

| Milestone | Phase | New skill added | Why the next milestone needs it |
|---|---|---|---|
| 1. Runs locally, documented dependencies | 1 | Reproducible setup documentation, Python ops scripting | Can't containerize what you can't precisely describe the dependencies of. |
| 2. Dockerized, pushed to Docker Hub | 2 | Image building, tagging, registries | Multi-container orchestration (next) requires a working image for each service. |
| 3. Full Compose stack (DB + cache + Nginx) | 3 | Networking, volumes, reverse proxy | CI/CD needs a real, testable multi-service target to validate against. |
| 4. Automated tests added | 4a | Unit + integration testing | A CI pipeline without tests only automates shipping bugs faster. |
| 5. CI/CD pipeline (test → build → push) | 4b | Pipelines, secrets in CI, artifact publishing | Cloud deployment should be triggered by this pipeline, not manual builds. |
| 6. Deployed manually to AWS EC2, HTTPS | 5 | Cloud networking, real TLS, manual ops pain | Feeling manual pain motivates and contextualizes IaC. |
| 7. Infrastructure as Terraform + Ansible | 6–7 | Reproducible infra & config | A reproducible environment is required before you can safely practice security hardening and chaos/failure testing without fear of unrecoverable mistakes. |
| 8. Full observability (Prometheus/Grafana/Loki) | 9 | Metrics, logs, alerting | Before moving to Kubernetes, you need a baseline of "what healthy looks like" to recognize orchestration-induced issues later. |
| 9. Deployed to Kubernetes (kind) | 10 | Orchestration, self-healing, probes | GitOps (next) needs a Kubernetes target to manage declaratively. |
| 10. Helm chart + ArgoCD GitOps | 11 | Templating, declarative delivery | Capstone needs a deployment story that's auditable and promotable across environments. |
| 11. Hardened, documented, final capstone | 8 + 12 | Security audit, incident documentation, portfolio polish | — |

*(Phase 8's security hardening is applied continuously from Milestone 6 onward, then formally audited as its own pass — see Phase 8.)*

### Failure-injection library (use throughout, referenced per phase above)
| Scenario | Layer | What to inspect | Symptom vs. root cause |
|---|---|---|---|
| App can't connect to DB | App/Network | App logs, `docker exec` into DB, `nc`/`curl` test from app container, env vars | Symptom: 500 errors / connection refused in app logs. Root cause candidates: wrong host/port, DB not ready yet, network not shared, credentials wrong. |
| Wrong environment variable | Config | `docker inspect`/`kubectl describe`, compare against `.env.example`/ConfigMap | Symptom: app crashes on startup or silently misbehaves. Root cause: typo, wrong secret reference, stale cached config. |
| Container exits unexpectedly | Container runtime | `docker inspect` exit code, `docker logs`, `dmesg` for OOM | Symptom: restart loop. Root cause: unhandled exception (code 1), OOM (137), external SIGTERM (143). |
| Wrong port mapping/firewall rule | Network | `ss`, Security Group/NACL rules, `curl -v` from inside vs. outside | Symptom: timeout (firewall) vs. refused (nothing listening) — the distinction is the diagnostic skill. |
| Broken CI pipeline | CI/CD | Job logs, which step failed, whether it's a test failure vs. an infra/runner issue | Symptom: red pipeline. Root cause: flaky test, missing secret, registry auth expired, runner resource limits. |
| Invalid Terraform config | IaC | `terraform validate`/`plan` output, provider error messages | Symptom: `apply` fails mid-way. Root cause: syntax error, invalid reference, provider API rejecting a value, quota limits. |
| Failed deployment / unhealthy app | Deploy/Orchestration | Health check results, rollout status, previous logs | Symptom: deploy "succeeds" but app is unhealthy. Root cause: missing post-deploy health gate — exactly why Phase 4 teaches gating deploys on health, not just exit codes. |
| Pod fails to start | Kubernetes | `kubectl describe pod`, events, `kubectl logs --previous` | Differentiate CrashLoopBackOff (app-level failure) vs. ImagePullBackOff (registry/auth/tag issue) vs. Pending (scheduling/resource issue). |
| Missing permissions/secrets | IAM/Secrets | IAM policy simulator, `kubectl describe` for mount errors, CI secret scoping | Symptom: "access denied" or a Pod stuck waiting for a Secret/ConfigMap that doesn't exist. |
| Disk/memory/CPU resource problems | Host/Container | `df`, `free`, `top`/`docker stats`, cgroup limits, Kubernetes resource requests/limits | Symptom: slow or killed processes. Root cause distinguished by which resource is actually exhausted — never guess, measure. |

---

## 22. Final Capstone Project Specification

### Name
**"Pulse — Production-Style Deployment Capstone"** (the same app, now presented and operated as a complete system).

### Objective
Demonstrate the full, integrated DevOps lifecycle on a real, if small, application: code → test → containerize → provision → configure → secure → deploy → observe → operate → recover.

### Problem being solved
Show that you can take a working application from "runs on a laptop" to "runs reliably and observably in a cloud-native environment, deployable and recoverable by someone other than you, following your documentation."

### Architecture (final state)
```
GitHub repo (app + infra + manifests)
   │
   ▼ (push/PR)
GitHub Actions CI ── test ── build image ── scan (trivy, gitleaks, pip-audit)
   │                                               │
   │ (on tag/merge)                                ▼ fail blocks merge
   └─ push image ──► AWS ECR
                           │
            Terraform ─────┼───► AWS VPC, subnets, EC2 (or EKS node group), IAM roles, SSM params
                           │
            Ansible  ──────┘ (if EC2-based) bootstraps node, installs runtime
                           │
                           ▼
                 Kubernetes cluster (kind locally / self-managed or EKS for the live demo)
                   ├── Deployment: pulse (N replicas, probes, resource limits)
                   ├── StatefulSet or managed external DB: PostgreSQL
                   ├── Deployment: Redis
                   ├── Ingress (TLS) ──► public URL
                   ├── Prometheus + Grafana + Loki/Promtail
                   └── ArgoCD watching the Git "deploy" path, auto-syncing
```

### Required features
- Public HTTPS URL serving "Pulse."
- CI pipeline: lint, unit + integration tests, security scans, image build/push — all required checks before merge.
- Infrastructure fully defined in Terraform; zero manually-created cloud resources.
- Configuration/bootstrap automated via Ansible where a raw VM is involved (or documented justification if fully containerized/EKS-managed without Ansible).
- Secrets never in Git; sourced from AWS SSM/Secrets Manager or Kubernetes Secrets populated via a secure mechanism.
- Kubernetes deployment with working liveness/readiness probes, resource requests/limits, and at least 2 replicas.
- GitOps-managed deployment via ArgoCD — the cluster state matches Git, not ad-hoc `kubectl` commands.
- Dashboards showing request rate, error rate, latency, and resource usage; at least 2 working alert rules.
- A documented, tested backup procedure for the database and a documented, tested restore procedure.
- A documented rollback procedure, exercised at least once for a real (or deliberately injected) bad deploy.

### Implementation milestones
1. Finalize app features and test coverage.
2. Finalize CI pipeline with all security gates passing.
3. Finalize Terraform modules (reused/refined from Phase 6).
4. Finalize Ansible roles (reused/refined from Phase 7), or document the EKS-only alternative.
5. Finalize Kubernetes manifests/Helm chart (reused/refined from Phase 10–11).
6. Wire ArgoCD to the manifests repo/path.
7. Finalize monitoring stack and alert rules.
8. Write and test backup/restore procedure.
9. Run the full failure-injection list (Section 21) against this final system and document each as a mini incident report in `docs/incidents/`.
10. Write final documentation (see below) and record a short architecture walkthrough (even just for yourself, to rehearse explaining it).

### Failure scenarios to test (minimum set, beyond Section 21's generic list)
- Database Pod/instance deleted — restore from backup, measure and document actual data loss window (RPO) and recovery time (RTO).
- A bad image tag deployed via Git — recover via Git revert + ArgoCD sync.
- A node/VM running the app is terminated — confirm Kubernetes reschedules automatically (if using a multi-node setup) or document the single-node limitation honestly if using a single kind/EC2 node.
- An alert fires for a real injected problem (e.g., sustained 5xx errors) — confirm you receive it and can correlate it with a dashboard and logs within minutes.

### Acceptance criteria
- A technically competent reviewer can clone the repo, read the README, and understand the entire system without further explanation from you.
- Every "required feature" above is demonstrably true (not just described) — screenshots, recorded terminal sessions, or a live demo link are acceptable evidence.
- You can explain every architectural decision and name at least one alternative you considered and why you didn't choose it.

### README must document
- Project overview and problem statement.
- Architecture diagram (can be drawn with a tool like Excalidraw/diagrams.py and committed as an image).
- Prerequisites (tool versions: Docker, Terraform, kubectl, Helm, Ansible, AWS CLI).
- Setup instructions (local dev via Compose; cloud deployment via Terraform/Ansible/ArgoCD).
- Configuration and environment variables (with a `.env.example`, never real secrets).
- Deployment procedure (how a change goes from commit to production).
- CI/CD workflow explanation (diagram or step list).
- Security considerations (IAM scope, secrets handling, scanning gates).
- Monitoring/alerting overview (what's measured, what triggers an alert).
- Backup/restore procedure.
- Troubleshooting guide (at least the failure scenarios you tested).
- Known limitations and future improvements (be honest — e.g., "single-node cluster, no multi-AZ failover").

### Optional extensions (for after the baseline capstone is solid)
- Multi-node Kubernetes cluster with proper node failure testing.
- Canary deployment via Argo Rollouts.
- Cost report/FinOps review of the AWS resources used.
- A second, intentionally different environment (e.g., staging on a smaller instance type) to prove environment parity via the same Terraform/Helm code with different variables.

### Interview / defense questions you should be able to answer afterward
- Why Terraform *and* Ansible — why not just one? What would you lose by dropping either?
- Why Kubernetes for this app — what would running it on a single VM with Compose have cost you, and what did Kubernetes cost you in complexity?
- Walk through what happens, step by step, from `git push` to the new version serving live traffic.
- How do you know the system is healthy right now, without SSHing in?
- If the database Pod disappeared right now, what exactly would happen, in what order, and how would you recover?
- Where are your secrets stored, and what prevents them from ending up in Git or in your container images?
- What is your single biggest point of failure in this architecture, and what would you do about it with more time/budget?
- What would you change if this needed to handle 100x the traffic?

---

## 23. Weekly Study Plan (8–10 h/week)

This is a *rhythm*, not a rigid calendar. Each week mixes theory, hands-on building, and troubleshooting — never a full week of passive watching.

| Week(s) | Phase | Weekly focus | Deliverable checkpoint |
|---|---|---|---|
| 1 | 0 | Diagnostic self-assessment, environment setup | Diagnostic answers committed to `devops-learning-log` |
| 2–4 | 1 | Networking deep dive, Bash/Python automation, Git workflow upgrade | Healthcheck script, SSH lockout/recovery documented, "Pulse" v1 running locally with README |
| 5–7 | 2 | Docker fundamentals | Multi-stage Dockerfile, image on Docker Hub, scan report with 1+ fixed issue |
| 8–9 | 3 | Docker Compose | Full local stack (app+DB+cache+Nginx), readiness-race bug reproduced & fixed |
| 10–12 | 4 | Testing & CI/CD | GitHub Actions pipeline: tests block merge, image auto-published, 1 executed rollback |
| 13–15 | 5 | AWS fundamentals | "Pulse" live on EC2 over HTTPS, DB isolated in private subnet |
| 16–18 | 6 | Terraform | Entire Phase 5 infra reproducible from `terraform apply` on a clean account/region |
| 19–20 | 7 | Ansible | One-command server bootstrap + deploy, idempotency proven |
| 21–22 | 8 | Security/IAM/Secrets | IAM least-privilege audit done, secrets out of Git, CI security gates added |
| 23–24 | 9 | Monitoring/Observability | From-scratch Grafana dashboard, 2 working alerts |
| 25–28 | 10 | Kubernetes | "Pulse" on `kind` with probes, self-healing proven, 3 failure scenarios independently diagnosed |
| 29–30 | 11 | Helm & GitOps | Helm chart multi-env, ArgoCD auto-sync + drift correction demonstrated |
| 31–34 | 12 | Capstone & Portfolio | Full capstone repo, documented incidents, portfolio polish, mock interview self-review |

**Dependencies that can delay progress (plan for these, don't be surprised by them):**
- Networking (Phase 1) is the most common hidden blocker later — if Phase 10 troubleshooting feels impossible, the gap is usually here, not in Kubernetes itself.
- AWS free-tier limits/billing surprises can interrupt Phase 5–8 — set the budget alarm in Week 13, not later.
- Terraform state mistakes (Phase 6) can require rebuilding an environment — treat this as expected practice, not a setback.
- Kubernetes (Phase 10) is intentionally the longest phase; do not compress it to "stay on schedule" — rushing it undermines everything in Phase 11–12.

---

## 24. GitHub Portfolio Checklist

Structure your GitHub presence to show **progression**, not just a final artifact.

**Repositories to maintain:**
1. `devops-learning-log` — diagnostic notes, troubleshooting write-ups, concept explanations in your own words (shows thinking, not just output).
2. `pulse` — the evolving application itself, with a clean, linear Git history and tagged releases per milestone (`v0.1-local`, `v0.2-docker`, `v0.3-compose`, ... up to the capstone tag).
3. (Optional) separate `pulse-infra` repo for Terraform/Ansible/Kubernetes manifests if you want to demonstrate the app-repo/infra-repo separation pattern used in real GitOps setups.

**Every major repository should include:**
- [ ] Clear project overview and purpose (first paragraph, no fluff).
- [ ] Architecture diagram (image, not just prose).
- [ ] Prerequisites with exact tool versions.
- [ ] Setup instructions that work on a clean machine (test this literally, on a fresh VM or container).
- [ ] Configuration/environment variable documentation with a safe `.env.example`.
- [ ] Deployment procedure.
- [ ] CI/CD workflow explanation (badge + description).
- [ ] Security considerations section.
- [ ] Troubleshooting guide drawn from real issues you hit.
- [ ] Known limitations and future improvements, stated honestly.
- [ ] A LICENSE file and consistent commit message convention.

**Distinguishing levels of competence (be honest with yourself about which applies):**
| Level | Description |
|---|---|
| Completed a tutorial | You followed steps and it worked; you could not reproduce it without the tutorial open. |
| Completed a project | You built it from requirements, made your own decisions, and can rebuild it from scratch without notes. |
| Independently understand & maintain a system | You can change requirements after the fact, diagnose novel failures you've never seen before, and explain trade-offs you didn't read about — only this level is portfolio-ready for interviews. |

Your goal before applying: every repository in your portfolio should be at the "project" level at minimum, and your capstone should be at the "independently understand & maintain" level.

---

## 25. Junior DevOps Skills Matrix

Use this as a pre-application self-check. You should be able to say "yes, demonstrably" (not "yes, I watched a video about it") for every **Core** row before applying.

| Skill | Tier | Demonstrated by |
|---|---|---|
| Linux process/permission/signal management | Core | Phase 1 exercises, "Pulse" ops scripts |
| Networking troubleshooting (DNS/TCP/HTTP/TLS) | Core | Phase 1, 3, 5, 10 failure scenarios resolved independently |
| Bash & Python automation | Core | Healthcheck script, Ansible-adjacent tooling |
| Git branching/PR/release workflow | Core | "Pulse" repo history and tags |
| Docker image building, networking, volumes | Core | Phase 2–3 deliverables |
| Docker Compose multi-service orchestration | Core | Phase 3 deliverable |
| Automated testing (unit + integration) | Core | Phase 4 test suite |
| CI/CD pipeline design (GitHub Actions) | Core | Phase 4 pipeline, enforced gates |
| Cloud fundamentals (AWS VPC/EC2/IAM/ECR/S3) | Core | Phase 5 deployment |
| Infrastructure as Code (Terraform) | Core | Phase 6 reproducible environment |
| Configuration management (Ansible) | Core | Phase 7 idempotent playbook |
| Secrets & IAM least privilege | Core | Phase 8 audit |
| Monitoring/logging/alerting (Prometheus/Grafana) | Core | Phase 9 dashboards & alerts |
| Kubernetes core objects & troubleshooting | Core | Phase 10 independent diagnoses |
| Helm templating | Core-adjacent | Phase 11 chart |
| GitOps principles (ArgoCD) | Core-adjacent | Phase 11 drift-correction demo |
| Incident documentation / RCA writing | Core | Capstone `docs/incidents/` |
| Service mesh | Advanced/Optional | Not required for junior roles |
| Multi-cloud | Advanced/Optional | Not required for junior roles |
| Chaos engineering | Advanced/Optional | Portfolio differentiator, not a requirement |

### When are you ready to apply?
Not based on elapsed time. You are ready when:
- [ ] Every **Core** row above has a real, demonstrable artifact (not "watched a course on it").
- [ ] You can explain the capstone architecture and defend every decision (Section 22's interview questions) without notes.
- [ ] You have at least 5 documented, independently-diagnosed failure scenarios across different layers (app, container, network, infra, platform).
- [ ] A stranger could deploy your capstone from your README alone.
- [ ] You can comfortably say "I don't know, but here's how I'd find out" for questions outside this roadmap's scope — that instinct, not tool-count, is what separates a junior DevOps hire from a tutorial-follower.

No roadmap or certificate guarantees an interview or an offer — this matrix defines *readiness to compete*, not a guarantee of outcome.

---

## 26. What To Do First — Exact Tasks for Day 1–7

| Day | Task |
|---|---|
| 1 | Create the `devops-learning-log` GitHub repo. Set up (or confirm) a dedicated Linux environment you control as root (VM, WSL2, or a free-tier cloud instance). Write down, unaided, your answers to the Phase 0 diagnostic questions (DNS resolution, TCP handshake, TLS, process signals, `git rebase` vs `merge`). Commit them. |
| 2 | Do Phase 0 diagnostic tasks 1–3 (sudoers config, process signals/`/proc` inspection, networking explanation review against a reliable source — fix any wrong assumptions in your Day 1 notes). |
| 3 | Do Phase 0 diagnostic tasks 4–6 (Bash log-parsing one-liner, Python `df -h` checker script, Git rebase/merge/force-push explanation). Commit all scripts to `devops-learning-log`. |
| 4 | Start the "Pulse" application: decide on Flask or FastAPI (pick whichever you're more comfortable with — the framework choice is not the point), scaffold `POST /shorten`, `GET /<code>` using an in-memory store for now. |
| 5 | Add PostgreSQL (plain, not yet containerized) and SQLAlchemy models for "Pulse"; replace the in-memory store. Add `GET /stats/<code>`. |
| 6 | Add the `GET /health` endpoint checking real DB connectivity. Write the Phase 1 `healthcheck.py` external script (Section "Phase 1 Exercises," item 7) and run it against your running app. Write the README documenting exact local setup steps from a clean machine. |
| 7 | Do the SSH hardening + deliberate lockout + recovery exercise (Phase 1, exercise 5) on your Linux environment. Review the week: update your diagnostic gap list based on what actually took longer than expected, and schedule Phase 1's networking deep-dive as your Week 2 priority. |

**By the end of Day 7 you should have:** a committed diagnostic self-assessment, a working (if simple) "Pulse" application with a real database connection and health endpoint, a documented recovery from a self-inflicted SSH lockout, and a clear, written list of your top 3 real knowledge gaps to prioritize in Phase 1.

---

*This document is a living study guide. Revisit and amend it — especially the weekly plan and gap list — as you progress. Treat completion checklists as gatekeepers for moving forward, not the courses or videos themselves.*
