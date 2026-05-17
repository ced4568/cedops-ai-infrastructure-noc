# 🚀 CedOps — AI Infrastructure Operations NOC

![Grafana](https://img.shields.io/badge/Grafana-Dashboard-orange)
![Prometheus](https://img.shields.io/badge/Prometheus-Monitoring-red)
![Docker](https://img.shields.io/badge/Docker-Containers-blue)
![Tailscale](https://img.shields.io/badge/Tailscale-ZeroTrust-purple)
![Proxmox](https://img.shields.io/badge/Proxmox-Virtualization-orange)
![Platform Engineering](https://img.shields.io/badge/Focus-Platform%20Engineering-green)

![CedOps Dashboard](https://raw.githubusercontent.com/ced4568/cedops-ai-infrastructure-noc/main/docs/screenshots/dashboard_v1.png)

## Overview

CedOps is an **AI-Assisted Infrastructure Operations Platform** designed to provide centralized monitoring, observability, uptime management, and operational visibility across a hybrid environment of:

- 🏠 Homelab Infrastructure
- ☁️ VPS Cloud Infrastructure
- 🤖 AI Operations Systems
- 🌐 Public-Facing Services
- 📡 Network & Platform Health

The platform combines:

- **Prometheus** for metrics collection
- **Grafana** for visualization
- **Blackbox Exporter** for service monitoring
- **Node Exporter** for infrastructure metrics
- **Tailscale** for secure private observability
- **Proxmox VE** for virtualization
- **Docker** for service deployment

---

# 🎯 Project Goals

CedOps was built to simulate a **real-world Platform Engineering / Infrastructure Operations environment**.

Goals:

✅ Single-pane-of-glass infrastructure visibility  
✅ Secure observability without exposing services publicly  
✅ Hybrid monitoring (on-prem + cloud)  
✅ Public service uptime tracking  
✅ AI platform monitoring  
✅ Portfolio-grade infrastructure engineering project

---

# 🏗️ Architecture Overview

```text
                    Internet
                        │
            ┌───────────┴───────────┐
            │   Public Services     │
            │ synthossystems.com    │
            │ noc.chasedumphord.com │
            │ cedshomelab.com       │
            └───────────┬───────────┘
                        │
                 Blackbox Exporter
                        │
                        ▼
               Prometheus Monitoring
                (10.10.30.140)
                        │
        ┌───────────────┼────────────────┐
        │               │                │
        ▼               ▼                ▼
   Proxmox Nodes    K3s Cluster     Hetzner VPS
   Node Exporter    Monitoring      synthos-node-1
                                         │
                                   Node Exporter
                                         │
                                     Tailscale
```

---

# 🖥️ Dashboard Features

## Executive Health

- VPS Status
- Public Services Status
- NOC Health Score
- Uptime Metrics

## Infrastructure Monitoring

- CPU Usage
- Memory Utilization
- Disk Usage
- Network Traffic

## Public Service Monitoring

Tracked via Blackbox Exporter:

- CedOps
- n8n
- Paperclip
- Synthos Website
- Ced's Home Lab
- Grafana
- Prometheus

## Reliability Monitoring

- HTTP Status Codes
- Response Times
- Endpoint Availability
- Service Reachability

---

# 📸 Dashboard Screenshots

## CedOps Infrastructure NOC (V1)

![Dashboard V1](docs/screenshots/dashboard_v1.png)

---

# 🔒 Security Architecture

CedOps prioritizes **secure observability**.

### No Public Prometheus Exposure

Infrastructure metrics are collected using:

**Tailscale private networking**

Benefits:

- Encrypted communication
- Zero Trust access
- No public metrics exposure
- Private infrastructure scraping

### Monitoring Stack

| Tool | Purpose |
|------|---------|
| Prometheus | Metrics collection |
| Grafana | Visualization |
| Blackbox Exporter | Uptime checks |
| Node Exporter | Linux system metrics |
| Tailscale | Secure networking |
| Docker | Service deployment |
| Proxmox | Virtualization |

---

# 📂 Repository Structure

```text
cedops-ai-infrastructure-noc/
│
├── docs/
│   ├── architecture/
│   ├── screenshots/
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

---

# 🛠️ Skills Demonstrated

### Platform Engineering
- Infrastructure Monitoring
- Observability Design
- Service Reliability
- Secure Networking

### DevOps
- Linux Administration
- Docker
- YAML Configuration
- Troubleshooting

### Cloud & Infrastructure
- Hetzner VPS
- Proxmox Virtualization
- Hybrid Infrastructure
- Private Networking

### Monitoring & Observability
- Prometheus
- Grafana
- Blackbox Exporter
- Alerting
- Metrics Design

---

# 💼 Resume Relevance

This project demonstrates real-world experience with:

**Platform Engineering**  
**Infrastructure Monitoring**  
**Observability Engineering**  
**DevOps Workflows**  
**Cloud + On-Prem Hybrid Systems**

---

# 🔮 Roadmap

## V2 Dashboard

- SSL Expiration Monitoring
- Alert Feed
- SLA Tracking
- Reliability Scoring
- Capacity Metrics

## Future Enhancements

- Telegram Alerts
- Discord Notifications
- AI Incident Detection
- Automated Remediation
- Multi-Environment Monitoring

---

# 👨‍💻 Author

### Chase Dumphord

Digital Systems Engineer | Infrastructure & Platform Engineering | Observability | AI Systems

GitHub: https://github.com/ced4568

Portfolio:
- https://chasedumphord.com
- https://noc.chasedumphord.com
- https://cedshomelab.com