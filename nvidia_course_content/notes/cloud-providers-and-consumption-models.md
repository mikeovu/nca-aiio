# Unit 12: Supported Cloud Providers and Consumption Models

**Exam mapping:** Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript (part 4 of Unit 12, sub-unit 12.5)

---

## 1. NVIDIA Works With All Major CSPs
NVIDIA partners with the leading **cloud service providers (CSPs)**, so you can deploy AI on the provider you choose:
- **Amazon Web Services (AWS)**
- **Microsoft Azure**
- **Google Cloud Platform (GCP)**
- **Oracle Cloud Infrastructure (OCI)**

The ecosystem **keeps growing**, so you can **scale AI workloads across different clouds** with flexibility, reliability and performance.

---

## 2. Consumption Models: Who Manages What
- **The models differ in how responsibility is split between the customer and the CSP.**
- **On-premises** is the baseline. The customer manages **the whole stack**: data center, network, storage, physical servers, virtualization, OS, scaling, application code and data configuration.

| Model | The CSP manages | The customer manages |
|---|---|---|
| **On-premises** | Nothing | **Everything** |
| **IaaS** (Infrastructure as a Service) | **On-demand infrastructure** | Everything **above the infrastructure** |
| **PaaS** (Platform as a Service) | Builds on IaaS: **hardware and software** | **Their code** (developers focus on coding) |
| **SaaS** (Software as a Service) | **The complete application** and all hosting | Using the app |

- **First step for AI in the cloud:** understand your company's **current cloud strategy**, including its **enterprise cloud contracts** and the services it already uses (e.g. IaaS or PaaS).

---

## 3. Cloud Marketplaces
A **cloud marketplace** is a **one-stop shop** for cloud services from many providers. It's one of the most popular ways to get started.

| Benefit | Detail |
|---|---|
| **One-stop shop** | **Compare and choose** services from many providers |
| **Easy discovery** | A **central place** to find the right services |
| **Streamlined procurement** | Buy and deploy quickly, **without a long procurement process** |
| **Cost savings** | **Transparent pricing** and cost comparison across providers |
| **Increased agility** | **Scale up or down** quickly as business needs change |

---

## Key Terms
- **CSP**: cloud service provider (AWS, Azure, GCP, OCI).
- **IaaS**: the CSP runs the infrastructure, and the customer handles everything above it.
- **PaaS**: the CSP runs the hardware and software platform, and developers just write code.
- **SaaS**: the CSP delivers the complete application.
- **Cloud marketplace**: a one-stop shop to discover, compare and buy cloud services.

## Exam Tips
- **The four major CSPs NVIDIA supports are AWS, Azure, GCP and OCI.**
- **Responsibility moves to the CSP as you go On-prem → IaaS → PaaS → SaaS.**
- **PaaS = focus on code. SaaS = complete application. IaaS = infrastructure only.**
- **Marketplace benefits:** one-stop shop, easy discovery, streamlined procurement, cost savings, agility.
- **The first step is to understand the company's current cloud strategy and contracts.**

---

## NVIDIA Documentation
Official NVIDIA pages for this lesson's main concepts (links checked November 11, 2026).

- [NVIDIA Cloud Computing Solutions](https://www.nvidia.com/en-us/data-center/gpu-cloud-computing/): overview of NVIDIA across CSPs.
- [NVIDIA on AWS](https://www.nvidia.com/en-us/data-center/gpu-cloud-computing/amazon-web-services/): GPU-accelerated AWS.
- [NVIDIA on Microsoft Azure](https://www.nvidia.com/en-us/data-center/gpu-cloud-computing/microsoft-azure/): GPU-accelerated Azure.
- [NVIDIA on Google Cloud](https://www.nvidia.com/en-us/data-center/gpu-cloud-computing/google-cloud-platform/): GPU-accelerated GCP.
- [NVIDIA on Oracle Cloud Infrastructure](https://www.nvidia.com/en-us/data-center/gpu-cloud-computing/oracle-cloud-infrastructure/): GPU-accelerated OCI.
- [NVIDIA AI Enterprise Cloud Deployment Guide](https://docs.nvidia.com/ai-enterprise/deployment/cloud/latest/index.html): deploying NVIDIA AI Enterprise on CSPs, including through marketplaces.
