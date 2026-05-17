# 🤖 CedOps — AI Infrastructure Operations NOC

> A live AI operations platform running on Hetzner VPS — 8 autonomous agents orchestrated by Paperclip, monitored in real-time by a Prometheus + Grafana NOC dashboard. Built by a Digital Systems Engineer at GE Aerospace.

[![Live NOC](https://img.shields.io/badge/Live%20NOC-noc.chasedumphord.com-1D9E75?style=flat-square)](https://noc.chasedumphord.com)
[![Paperclip](https://img.shields.io/badge/Paperclip-AI%20Agent%20Platform-6B46C1?style=flat-square)](https://paperclip.synthossystems.com)
[![Synthos Systems](https://img.shields.io/badge/Synthos%20Systems-synthossystems.com-0EA5E9?style=flat-square)](https://synthossystems.com)
[![Portfolio](https://img.shields.io/badge/Portfolio-chasedumphord.com-0F6E56?style=flat-square)](https://chasedumphord.com)
[![Agents](https://img.shields.io/badge/AI%20Agents-8%20Active-orange?style=flat-square)](#-ai-agent-roster)
[![Platform](https://img.shields.io/badge/Platform-Hetzner%20VPS-D4001A?style=flat-square)](#️-infrastructure-layer)
[![Monitoring](https://img.shields.io/badge/Monitoring-Prometheus%20%2B%20Grafana-F46800?style=flat-square)](#-observability--noc)

---

## 📸 NOC Dashboard

[![CedOps NOC Dashboard](docs/screenshots/dashboard_v1.png)](docs/screenshots/dashboard_v1.png)

> **Live:** All 5 public services reporting UP · NOC Health Score 100% · VPS Disk 27% · Prometheus scraping every 30s

---

## 🧭 Overview

CedOps is a **production-style AI operations platform** built to simulate a real-world Platform Engineering and AI Infrastructure environment. The entire stack runs on a Hetzner VPS and is monitored continuously by a live Grafana NOC dashboard.

The platform combines:

- **Paperclip** — AI Agent Orchestration Platform managing 8 autonomous agents
- **SugeBot** — Hermes AI agent deployed as Telegram Operations Assistant (CTO/Ops role)
- **n8n** — Automation platform for workflow execution and inter-service routing
- **OpenRouter** — AI model gateway serving as the LLM backbone for all agents
- **Prometheus + Grafana** — Full observability NOC monitoring the entire stack in real-time
- **Nginx Proxy Manager** — Reverse proxy + SSL management across all services
- **Docker + Portainer** — Container infrastructure and management layer

---

## 🏗️ Architecture Overview

```
                        Internet
                            │
              ┌─────────────┴─────────────┐
              │      Cloudflare Edge       │
              │   DNS · Tunnels · Proxy    │
              └─────────────┬─────────────┘
                            │
              ┌─────────────▼─────────────┐
              │       Hetzner VPS          │
              │    synthos-node-1          │
              │                           │
              │  ┌──────────────────────┐ │
              │  │  Nginx Proxy Manager  │ │
              │  │  Reverse Proxy / SSL  │ │
              │  └──────────┬───────────┘ │
              │             │             │
              │  ┌──────────▼───────────┐ │
              │  │      Portainer        │ │
              │  │  Docker Management    │ │
              │  └──────────┬───────────┘ │
              │             │             │
              │  ┌──────────▼───────────────────────────────┐ │
              │  │            CedOps Platform                │ │
              │  │                                           │ │
              │  │  ┌─────────────┐  ┌──────────────────┐  │ │
              │  │  │  Paperclip  │  │     SugeBot       │  │ │
              │  │  │ AI Orch.    │  │  Telegram Ops     │  │ │
              │  │  │  8 Agents   │  │  (Hermes Agent)   │  │ │
              │  │  └──────┬──────┘  └────────┬─────────┘  │ │
              │  │         │                   │            │ │
              │  │  ┌──────▼──────┐  ┌────────▼─────────┐  │ │
              │  │  │ OpenRouter  │  │       n8n         │  │ │
              │  │  │ AI Gateway  │  │  Automation       │  │ │
              │  │  └─────────────┘  └──────────────────┘  │ │
              │  └───────────────────────────────────────────┘ │
              │                                               │
              │  ┌───────────────────────────────────────┐   │
              │  │       Observability Stack              │   │
              │  │  Prometheus → Grafana NOC Dashboard    │   │
              │  │  Blackbox Exporter → Service Uptime    │   │
              │  │  Node Exporter → VPS Resource Health   │   │
              │  └───────────────────────────────────────┘   │
              └───────────────────────────────────────────────┘
```

---

## 🤖 AI Agent Roster

All agents run inside **Paperclip** — the AI Agent Orchestration Platform at `paperclip.synthossystems.com`.

| Agent | Role | Status |
|---|---|---|
| **Suge** | CTO / Operations (Hermes Agent) — also deployed as SugeBot on Telegram | ✅ Live |
| **CEO** | Executive decision-making and strategic oversight | ✅ Live |
| **ClaudeCoder** | Software engineering and code generation | ✅ Live |
| **Engineer** | Infrastructure and systems engineering | ✅ Live |
| **Marketing** | Marketing strategy and content | ✅ Live |
| **Offer Builder Agent** | Sales offer generation and pipeline | ✅ Live |
| **Research** | Market research and intelligence gathering | ✅ Live |
| **Sales Agent** | Lead qualification and outreach | ✅ Live |

> **Suge** serves dual duty — the primary Hermes-style ops agent inside Paperclip, and the external-facing **SugeBot** on Telegram for real-time operational commands.

---

## 🖥️ Infrastructure Layer

All services run on a **Hetzner VPS** (`synthos-node-1`) behind Cloudflare Tunnels with zero exposed ports.

| Service | Role | URL |
|---|---|---|
| **VPS / Portainer** | Docker container management | Internal |
| **Nginx Proxy Manager** | Reverse proxy + SSL termination | Internal |
| **Homepage** | CedOps command center dashboard | `ops.synthossystems.com` |
| **Synthos Website** | Business-facing website | `synthossystems.com` |
| **Ced's Home Lab** | Homelab / Portfolio platform | `cedshomelab.com` |

**Traffic Flow:**
```
Internet → Cloudflare Edge → Tunnel → Nginx Proxy Manager → Docker Services
```

---

## 📊 Observability & NOC

The CedOps NOC dashboard monitors the entire VPS stack in real-time.

### Executive Health Panel
- **Synthos VPS Status** — UP/DOWN state with instant alerting
- **Public Services Up** — count of healthy endpoints (target: 5/5)
- **NOC Health Score** — composite platform health percentage
- **VPS Uptime** — continuous uptime tracking in days

### VPS Resource Health
- CPU Usage % — `synthos-node-1` CPU time series
- Memory Utilization % — real-time memory pressure
- Disk Used % — current at 27%
- Network Traffic — RX/TX bandwidth graphs (30s refresh)

### Public Service Availability

Tracked via **Blackbox Exporter** HTTP probes:

| Service | Endpoint | Status |
|---|---|---|
| cedshomelab | cedshomelab.com | ✅ UP |
| n8n | n8n.synthossystems.com | ✅ UP |
| cedops | ops.synthossystems.com | ✅ UP |
| paperclip | paperclip.synthossystems.com | ✅ UP |
| synthos-website | synthossystems.com | ✅ UP |

### Reliability Metrics
- HTTP Status Codes per endpoint (all returning `200`)
- Public Endpoint Response Time (ms) — time series graph
- SSL Expiry Days — tracked per certificate with warning thresholds

---

## 🔒 Security Architecture

CedOps is designed with **zero public infrastructure exposure**.

| Control | Implementation |
|---|---|
| No open ports | Cloudflare Tunnel handles all ingress |
| No public Prometheus | Metrics stay private; only Grafana is exposed |
| SSL everywhere | NPM handles termination for all services |
| Container isolation | Docker network segmentation via Portainer |
| Secret management | No secrets in this repo — handled via environment variables |

---

## 📂 Repository Structure

```
cedops-ai-infrastructure-noc/
│
├── docs/
│   ├── architecture/
│   ├── screenshots/
│   │   └── dashboard_v1.png
│   └── sops/
│
├── grafana/
│   └── cedops-ai-infrastructure-noc-v1.json
│
├── prometheus/
│   ├── prometheus-example.yml
│   └── blackbox-targets-example.yml
│
├── diagrams/
│   └── cedops-architecture.mmd
│
└── README.md
```

> **Note:** Prometheus and Blackbox configs are sanitized for public sharing. Production configs are managed privately via environment variables and are never committed to this repo.

---

## 🛠️ Stack

| Layer | Technology |
|---|---|
| **Compute** | Hetzner VPS (synthos-node-1) |
| **Containers** | Docker + Portainer |
| **Reverse Proxy** | Nginx Proxy Manager |
| **DNS & Tunnels** | Cloudflare |
| **AI Orchestration** | Paperclip |
| **AI Gateway** | OpenRouter |
| **Automation** | n8n |
| **Ops Agent** | SugeBot (Hermes / Telegram) |
| **Metrics** | Prometheus + Node Exporter + Blackbox Exporter |
| **Visualization** | Grafana |

---

## 🔮 Roadmap

### V2 Dashboard
- [ ] Agent activity metrics (Paperclip runs, success rate, token spend)
- [ ] SugeBot command log panel
- [ ] Per-agent health monitoring
- [ ] n8n workflow execution tracking
- [ ] Telegram alert integration via SugeBot

### Platform Enhancements
- [ ] AI Incident Detection — anomaly-triggered agent escalation
- [ ] Automated Remediation — n8n workflows triggered by Prometheus alerts
- [ ] Multi-environment monitoring (homelab + VPS unified NOC)
- [ ] Discord alert channel

---

## 👤 Author

**Chase Dumphord**
Digital Systems Engineer | Platform Engineering | AI Infrastructure | Observability

[![LinkedIn](https://img.shields.io/badge/LinkedIn-chase--dumphord-0A66C2?style=flat-square)](https://www.linkedin.com/in/toochase-dumphord/)
[![GitHub](https://img.shields.io/badge/GitHub-ced4568-181717?style=flat-square)](https://github.com/ced4568)
[![Live NOC](https://img.shields.io/badge/Live%20NOC-noc.chasedumphord.com-1D9E75?style=flat-square)](https://noc.chasedumphord.com)
[![Portfolio](https://img.shields.io/badge/Portfolio-chasedumphord.com-0F6E56?style=flat-square)](https://chasedumphord.com)

---

## 🔗 Related Repos

| Repo | Description |
|---|---|
| [ceds-homelab](https://github.com/ced4568/ceds-homelab) | 6-node Proxmox cluster + 12-node K3s + full homelab infrastructure |
| [ced-k3s-homelab](https://github.com/ced4568/ced-k3s-homelab) | 12-node Raspberry Pi K3s cluster detail |
# 🤖 CedOps — AI Infrastructure Operations NOC

> A live AI operations platform running on Hetzner VPS — 8 autonomous agents orchestrated by Paperclip, monitored in real-time by a Prometheus + Grafana NOC dashboard. Built by a Digital Systems Engineer at GE Aerospace.

[![Live NOC](https://img.shields.io/badge/Live%20NOC-noc.chasedumphord.com-1D9E75?style=flat-square)](https://noc.chasedumphord.com)
[![Paperclip](https://img.shields.io/badge/Paperclip-AI%20Agent%20Platform-6B46C1?style=flat-square)](https://paperclip.synthossystems.com)
[![Synthos Systems](https://img.shields.io/badge/Synthos%20Systems-synthossystems.com-0EA5E9?style=flat-square)](https://synthossystems.com)
[![Portfolio](https://img.shields.io/badge/Portfolio-chasedumphord.com-0F6E56?style=flat-square)](https://chasedumphord.com)
[![Agents](https://img.shields.io/badge/AI%20Agents-8%20Active-orange?style=flat-square)](#-ai-agent-roster)
[![Platform](https://img.shields.io/badge/Platform-Hetzner%20VPS-D4001A?style=flat-square)](#️-infrastructure-layer)
[![Monitoring](https://img.shields.io/badge/Monitoring-Prometheus%20%2B%20Grafana-F46800?style=flat-square)](#-observability--noc)

---

## 📸 NOC Dashboard

[![CedOps NOC Dashboard](docs/screenshots/dashboard_v1.png)](docs/screenshots/dashboard_v1.png)

> **Live:** All 5 public services reporting UP · NOC Health Score 100% · VPS Disk 27% · Prometheus scraping every 30s

---

## 🧭 Overview

CedOps is a **production-style AI operations platform** built to simulate a real-world Platform Engineering and AI Infrastructure environment. The entire stack runs on a Hetzner VPS and is monitored continuously by a live Grafana NOC dashboard.

The platform combines:

- **Paperclip** — AI Agent Orchestration Platform managing 8 autonomous agents
- **SugeBot** — Hermes AI agent deployed as Telegram Operations Assistant (CTO/Ops role)
- **n8n** — Automation platform for workflow execution and inter-service routing
- **OpenRouter** — AI model gateway serving as the LLM backbone for all agents
- **Prometheus + Grafana** — Full observability NOC monitoring the entire stack in real-time
- **Nginx Proxy Manager** — Reverse proxy + SSL management across all services
- **Docker + Portainer** — Container infrastructure and management layer

---

## 🏗️ Architecture Overview

```
                        Internet
                            │
              ┌─────────────┴─────────────┐
              │      Cloudflare Edge       │
              │   DNS · Tunnels · Proxy    │
              └─────────────┬─────────────┘
                            │
              ┌─────────────▼─────────────┐
              │       Hetzner VPS          │
              │    synthos-node-1          │
              │                           │
              │  ┌──────────────────────┐ │
              │  │  Nginx Proxy Manager  │ │
              │  │  Reverse Proxy / SSL  │ │
              │  └──────────┬───────────┘ │
              │             │             │
              │  ┌──────────▼───────────┐ │
              │  │      Portainer        │ │
              │  │  Docker Management    │ │
              │  └──────────┬───────────┘ │
              │             │             │
              │  ┌──────────▼───────────────────────────────┐ │
              │  │            CedOps Platform                │ │
              │  │                                           │ │
              │  │  ┌─────────────┐  ┌──────────────────┐  │ │
              │  │  │  Paperclip  │  │     SugeBot       │  │ │
              │  │  │ AI Orch.    │  │  Telegram Ops     │  │ │
              │  │  │  8 Agents   │  │  (Hermes Agent)   │  │ │
              │  │  └──────┬──────┘  └────────┬─────────┘  │ │
              │  │         │                   │            │ │
              │  │  ┌──────▼──────┐  ┌────────▼─────────┐  │ │
              │  │  │ OpenRouter  │  │       n8n         │  │ │
              │  │  │ AI Gateway  │  │  Automation       │  │ │
              │  │  └─────────────┘  └──────────────────┘  │ │
              │  └───────────────────────────────────────────┘ │
              │                                               │
              │  ┌───────────────────────────────────────┐   │
              │  │       Observability Stack              │   │
              │  │  Prometheus → Grafana NOC Dashboard    │   │
              │  │  Blackbox Exporter → Service Uptime    │   │
              │  │  Node Exporter → VPS Resource Health   │   │
              │  └───────────────────────────────────────┘   │
              └───────────────────────────────────────────────┘
```

---

## 🤖 AI Agent Roster

All agents run inside **Paperclip** — the AI Agent Orchestration Platform at `paperclip.synthossystems.com`.

| Agent | Role | Status |
|---|---|---|
| **Suge** | CTO / Operations (Hermes Agent) — also deployed as SugeBot on Telegram | ✅ Live |
| **CEO** | Executive decision-making and strategic oversight | ✅ Live |
| **ClaudeCoder** | Software engineering and code generation | ✅ Live |
| **Engineer** | Infrastructure and systems engineering | ✅ Live |
| **Marketing** | Marketing strategy and content | ✅ Live |
| **Offer Builder Agent** | Sales offer generation and pipeline | ✅ Live |
| **Research** | Market research and intelligence gathering | ✅ Live |
| **Sales Agent** | Lead qualification and outreach | ✅ Live |

> **Suge** serves dual duty — the primary Hermes-style ops agent inside Paperclip, and the external-facing **SugeBot** on Telegram for real-time operational commands.

---

## 🖥️ Infrastructure Layer

All services run on a **Hetzner VPS** (`synthos-node-1`) behind Cloudflare Tunnels with zero exposed ports.

| Service | Role | URL |
|---|---|---|
| **VPS / Portainer** | Docker container management | Internal |
| **Nginx Proxy Manager** | Reverse proxy + SSL termination | Internal |
| **Homepage** | CedOps command center dashboard | `ops.synthossystems.com` |
| **Synthos Website** | Business-facing website | `synthossystems.com` |
| **Ced's Home Lab** | Homelab / Portfolio platform | `cedshomelab.com` |

**Traffic Flow:**
```
Internet → Cloudflare Edge → Tunnel → Nginx Proxy Manager → Docker Services
```

---

## 📊 Observability & NOC

The CedOps NOC dashboard monitors the entire VPS stack in real-time.

### Executive Health Panel
- **Synthos VPS Status** — UP/DOWN state with instant alerting
- **Public Services Up** — count of healthy endpoints (target: 5/5)
- **NOC Health Score** — composite platform health percentage
- **VPS Uptime** — continuous uptime tracking in days

### VPS Resource Health
- CPU Usage % — `synthos-node-1` CPU time series
- Memory Utilization % — real-time memory pressure
- Disk Used % — current at 27%
- Network Traffic — RX/TX bandwidth graphs (30s refresh)

### Public Service Availability

Tracked via **Blackbox Exporter** HTTP probes:

| Service | Endpoint | Status |
|---|---|---|
| cedshomelab | cedshomelab.com | ✅ UP |
| n8n | n8n.synthossystems.com | ✅ UP |
| cedops | ops.synthossystems.com | ✅ UP |
| paperclip | paperclip.synthossystems.com | ✅ UP |
| synthos-website | synthossystems.com | ✅ UP |

### Reliability Metrics
- HTTP Status Codes per endpoint (all returning `200`)
- Public Endpoint Response Time (ms) — time series graph
- SSL Expiry Days — tracked per certificate with warning thresholds

---

## 🔒 Security Architecture

CedOps is designed with **zero public infrastructure exposure**.

| Control | Implementation |
|---|---|
| No open ports | Cloudflare Tunnel handles all ingress |
| No public Prometheus | Metrics stay private; only Grafana is exposed |
| SSL everywhere | NPM handles termination for all services |
| Container isolation | Docker network segmentation via Portainer |
| Secret management | No secrets in this repo — handled via environment variables |

---

## 📂 Repository Structure

```
cedops-ai-infrastructure-noc/
│
├── docs/
│   ├── architecture/
│   ├── screenshots/
│   │   └── dashboard_v1.png
│   └── sops/
│
├── grafana/
│   └── cedops-ai-infrastructure-noc-v1.json
│
├── prometheus/
│   ├── prometheus-example.yml
│   └── blackbox-targets-example.yml
│
├── diagrams/
│   └── cedops-architecture.mmd
│
└── README.md
```

> **Note:** Prometheus and Blackbox configs are sanitized for public sharing. Production configs are managed privately via environment variables and are never committed to this repo.

---

## 🛠️ Stack

| Layer | Technology |
|---|---|
| **Compute** | Hetzner VPS (synthos-node-1) |
| **Containers** | Docker + Portainer |
| **Reverse Proxy** | Nginx Proxy Manager |
| **DNS & Tunnels** | Cloudflare |
| **AI Orchestration** | Paperclip |
| **AI Gateway** | OpenRouter |
| **Automation** | n8n |
| **Ops Agent** | SugeBot (Hermes / Telegram) |
| **Metrics** | Prometheus + Node Exporter + Blackbox Exporter |
| **Visualization** | Grafana |

---

## 🔮 Roadmap

### V2 Dashboard
- [ ] Agent activity metrics (Paperclip runs, success rate, token spend)
- [ ] SugeBot command log panel
- [ ] Per-agent health monitoring
- [ ] n8n workflow execution tracking
- [ ] Telegram alert integration via SugeBot

### Platform Enhancements
- [ ] AI Incident Detection — anomaly-triggered agent escalation
- [ ] Automated Remediation — n8n workflows triggered by Prometheus alerts
- [ ] Multi-environment monitoring (homelab + VPS unified NOC)
- [ ] Discord alert channel

---

## 👤 Author

**Chase Dumphord**
Digital Systems Engineer | Platform Engineering | AI Infrastructure | Observability

[![LinkedIn](https://img.shields.io/badge/LinkedIn-chase--dumphord-0A66C2?style=flat-square)](https://www.linkedin.com/in/toochase-dumphord/)
[![GitHub](https://img.shields.io/badge/GitHub-ced4568-181717?style=flat-square)](https://github.com/ced4568)
[![Live NOC](https://img.shields.io/badge/Live%20NOC-noc.chasedumphord.com-1D9E75?style=flat-square)](https://noc.chasedumphord.com)
[![Portfolio](https://img.shields.io/badge/Portfolio-chasedumphord.com-0F6E56?style=flat-square)](https://chasedumphord.com)

---

## 🔗 Related Repos

| Repo | Description |
|---|---|
| [ceds-homelab](https://github.com/ced4568/ceds-homelab) | 6-node Proxmox cluster + 12-node K3s + full homelab infrastructure |
| [ced-noc](https://github.com/ced4568/ceds-noc) | Custom-built public NOC dashboard |
| [ced-k3s-homelab](https://github.com/ced4568/ced-k3s-homelab) | 12-nodeRaspberry Pi K3s cluster detail |