# Unit 13: AI Data Center Management and Monitoring

**Exam mapping:** Topic 3, *AI Operations*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript

## What you should be able to do after this unit
1. Identify the general concepts of **provisioning, managing and monitoring** AI infrastructure.
2. Describe the **value of cluster management tools**.
3. Describe the concepts of **ongoing monitoring and maintenance**.
4. Identify the **tools** used for provisioning, management and monitoring.

---

## 1. Three Concepts for Managing AI Infrastructure

| Concept | What it covers |
|---|---|
| **Infrastructure provisioning** | **Setting up and configuring hardware**: servers, switches, storage and other cluster parts |
| **Resource management and monitoring** | Collecting **metrics from cluster resources** to see how the cluster performs, then making updates |
| **Workload management and monitoring** | Making sure **data scientists and AI practitioners have the tools they need**, and understanding **cluster usage** |

---

## 2. Infrastructure Provisioning
- After hardware is **installed in the data center or procured in the cloud**, it must be provisioned before use.
- **New hardware may not have the right software or firmware versions.** The versions needed depend on the **other components in the data center** and the **workload**.
- **Steps:**
  1. Work out the **correct software and firmware versions**.
  2. **Download** them.
  3. **Update the systems.** This covers the **OS, GPU drivers, networking drivers, management tools and applications** on servers, switches and storage, plus **hardware firmware**.
- **Done when** compute nodes, GPUs, storage and networking are **ready to run workloads**.

| Provisioning tool | What it is |
|---|---|
| **Ansible** | **Open-source, command-line IT automation** that configures systems and deploys software |
| **Terraform** | **Infrastructure as code (IaC)**. Defines both **cloud and on-prem** resources |
| **Foreman** | **Open-source** tool for managing servers through their **whole lifecycle**: provisioning, configuration, orchestration and monitoring |

---

## 3. Resource Management and Monitoring
- **Management and monitoring go hand in hand.** Monitoring shows which systems need attention **beyond regular maintenance**.

| Component | Monitor | Manage |
|---|---|---|
| **Compute nodes** | Overall **system health**, plus **GPU metrics** | **Security patches and updates**, **firmware**, **drivers**, **replace failing parts** |
| **Network** | **Congestion, connection quality, connectivity** | **Replace faulty or degraded cables**. Upgrade **topology or bandwidth** as workloads or the cluster grow |
| **Storage and management nodes** | **Disk space**, **management node health** | Keep management software **updated**, make **cloud and on-prem tools work together**, make sure the **right users are authorized** |

| Monitoring tool | What it is |
|---|---|
| **Redfish** | A **DMTF (Distributed Management Task Force) standard** for **simple, secure management** of servers, networks, storage and other infrastructure |
| **DCGM Exporter** | Built on the **Go APIs to NVIDIA DCGM (Data Center GPU Manager)**. Gathers **GPU metrics** to understand workload behavior and monitor GPUs in clusters |
| **Prometheus** | **Open-source** system that **collects and stores metrics** |
| **Grafana** | **Visualizes time-series data**, used together with Prometheus |

---

## 4. Workload Management and Monitoring
- **Management:**
  - Make sure jobs get the **resources they need** (the right number of **GPUs or CPU cores**).
  - **Schedule jobs** onto compute nodes.
  - **Stop** problem jobs and **restart** failed ones.
- **Monitoring:**
  - **Efficiency of resource use:** are **GPUs and CPUs well utilized**? Are there **memory or storage** issues?
  - **Job status**, so results can be returned and **resources released** back to the cluster.

| Workload tool | What it is |
|---|---|
| **Kubernetes** | **Open-source container orchestration.** Has **operators** for NVIDIA GPUs, shares metrics with **Prometheus**, and integrates with **advanced schedulers like Run:ai** |
| **Jupyter (JupyterLab)** | **Open-source web app** for creating and sharing **computational documents** (code, visualizations). Can run **inside containers** |
| **Slurm** | Created by **SchedMD**. **Resource sharing on large AI and HPC clusters.** Runs **interactive and batch jobs**, **prioritizes jobs**, supports **resource reservations** and **per-job quality of service** |

---

## 5. NVIDIA Base Command Manager (BCM)
**One software system that provisions, manages and monitors an AI data center.**
- **Infrastructure provisioning**, **user access**, **workload management** and **resource monitoring**.
- Sets up **networking, security and DNS**, and keeps the **cluster consistent**.
- **Automates server management and updates**, which **prevents server drift**.
- **Deploys Kubernetes, Slurm** and other workload managers, plus streamlined **JupyterLab** setup.
- **Built-in job monitoring and metrics** for GPUs and other resources.

### Three value propositions

| # | Value | How |
|---|---|---|
| 1 | **Faster time to value** | Simplifies infrastructure bring-up and workload provisioning, so data scientists **get resources quickly** |
| 2 | **Less complexity and effort** | **Automates management and operations** of accelerated infrastructure |
| 3 | **Agility** | Supports **many workload types** with **dynamic resource allocation** based on business needs |

These help the **whole AI team**: IT, data scientists and line-of-business owners.

---

## 6. NVIDIA Mission Control
**Software that runs AI factory operations**, from developer workloads to infrastructure to **facilities**. It's described as **"a world-class operations team delivered as software."**
- Powers **NVIDIA Blackwell data centers**.
- **An integrated suite that includes Base Command Manager** plus NVIDIA-run AI functions for **configuration, validation and operations**.

| Capability | Detail |
|---|---|
| **Advanced BCM features** | **Liquid-cooling integration** and **enhanced provisioning for Grace Blackwell NVL72** |
| **Intelligent Job Restart** | **Recovers on its own** from job and hardware failures. **Isolates the problem** and uses **built-in playbooks** |
| **Health validation and diagnosis** | Uses **telemetry**, shown in **customizable dashboards** |
| **Advanced cluster management** | From **provisioning to power optimization** |

- **Who benefits:**
  - **AI practitioners** get compute, orchestrate workloads, **tune GPU performance**, and don't need to step in manually after hardware failures.
  - **Enterprise IT** gets **telemetry, dashboards and on-demand health checks**.

---

## Key Terms
- **Provisioning**: setting up and configuring hardware, software and firmware so it's ready for workloads.
- **Infrastructure as code (IaC)**: defining infrastructure in code (Terraform).
- **Redfish**: DMTF standard for secure infrastructure management.
- [**DCGM**](https://docs.nvidia.com/datacenter/dcgm/latest/index.html): NVIDIA Data Center GPU Manager, for GPU management and monitoring.
- [**DCGM Exporter**](https://docs.nvidia.com/datacenter/cloud-native/gpu-telemetry/latest/dcgm-exporter.html): exports DCGM GPU metrics (to Prometheus).
- **Prometheus / Grafana**: metrics collection and storage / time-series dashboards.
- [**Kubernetes**](https://www.nvidia.com/en-us/glossary/kubernetes/): open-source container orchestration.
- [**Slurm**](https://developer.nvidia.com/slurm): SchedMD's job scheduler for AI and HPC clusters.
- **Server drift**: servers slowly falling out of a consistent configuration. BCM prevents it.
- [**Base Command Manager (BCM)**](https://www.nvidia.com/en-us/data-center/base-command-manager/): NVIDIA's software for provisioning, managing and monitoring AI clusters.
- [**Mission Control**](https://www.nvidia.com/en-us/data-center/mission-control/): NVIDIA's AI factory operations suite, including BCM.
- **Intelligent Job Restart**: Mission Control's automatic recovery from job and hardware failures.

## Exam Tips
- **The three concepts are infrastructure provisioning, resource management and monitoring, and workload management and monitoring.**
- **Match tool to task:**
  - **Provisioning:** Ansible, Terraform (IaC), Foreman.
  - **Resource monitoring:** Redfish, DCGM Exporter, Prometheus + Grafana.
  - **Workloads:** Kubernetes, Jupyter, Slurm.
- **DCGM Exporter gives GPU metrics. Prometheus stores metrics. Grafana visualizes them.**
- **BCM** provisions, manages and monitors. It **prevents server drift** and **deploys Kubernetes, Slurm and Jupyter**. Its values are **time to value, less complexity, agility**.
- **Mission Control = BCM + AI-driven operations** for Blackwell / **GB NVL72**. It **includes Intelligent Job Restart**, **liquid-cooling** integration and **telemetry dashboards**.

---

## NVIDIA Documentation
Official NVIDIA pages for this lesson's main concepts (links checked November 11, 2026).

- [NVIDIA Base Command Manager](https://www.nvidia.com/en-us/data-center/base-command-manager/): product overview.
- [Base Command Manager Documentation](https://docs.nvidia.com/base-command-manager/index.html): manuals for installing and administering BCM.
- [NVIDIA Mission Control](https://www.nvidia.com/en-us/data-center/mission-control/): product overview.
- [Mission Control Documentation](https://docs.nvidia.com/mission-control/index.html): guides for Mission Control.
- [NVIDIA DCGM](https://developer.nvidia.com/dcgm): Data Center GPU Manager overview.
- [DCGM Documentation](https://docs.nvidia.com/datacenter/dcgm/latest/index.html): GPU health, diagnostics and metrics.
- [DCGM Exporter](https://docs.nvidia.com/datacenter/cloud-native/gpu-telemetry/latest/dcgm-exporter.html): exporting GPU metrics to Prometheus.
- [NVIDIA GPU Telemetry](https://docs.nvidia.com/datacenter/cloud-native/gpu-telemetry/latest/index.html): GPU monitoring with DCGM, Prometheus and Grafana.
- [Slurm at NVIDIA](https://developer.nvidia.com/slurm): the Slurm workload manager.
