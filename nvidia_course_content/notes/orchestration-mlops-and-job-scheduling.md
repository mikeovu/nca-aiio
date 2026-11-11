# Unit 14: Orchestration, MLOps and Job Scheduling

**Exam mapping:** Topic 1, *Essential AI Knowledge*, and Topic 3, *AI Operations*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript

---

## 1. Orchestration vs. Scheduling
- **Container orchestration** **automates operations on containers**, based on what the environment needs.
- **Scheduling** **assigns workloads to available compute resources**.

| | **Orchestration** (e.g. Kubernetes) | **Scheduling** (e.g. Slurm) |
|---|---|---|
| Based on | **Containers** | **Bare metal** (but supports containers) |
| Designed for | **Microservices** | **High-performance computing** |
| Inference | **Scales up and down with inference demand** | **No inference capabilities** |
| Advanced features | Needs extra **meta-schedulers** | **Priority and preemption built in** |
| Scope | Manages **entire workflows and processes** | **Assigns tasks and jobs** to resources |
| Traffic and placement | **Load balancing** across containers | Finds the **hosts with the right resources** to run containers |

---

## 2. Kubernetes
- **Open-source container orchestration** that automates **deployment, scaling and management**.
- **Designed by Google**, now maintained by the **Cloud Native Computing Foundation (CNCF)**.
- **How a job runs:**
  1. You define a container-based job, e.g. a **CUDA container that runs `nvidia-smi` on a node with 1 GPU**.
  2. The **master (control plane) node** finds a **worker node** that meets the job's criteria and deploys it there.
  3. The job runs as a **pod** on that worker node.

### Core components

| Component | What it is |
|---|---|
| **Node** | A server with defined **CPU, memory, GPU** and other resources. Can be **physical or virtual**, anything that runs an OS |
| **Cluster** | **One or more nodes** that run containerized workloads |
| **Namespace** | An **isolated environment for multi-tenancy**. Its resources are unique to it, and it can have a **resource quota** |
| **Container** | A **self-contained runtime with its dependencies**, created from **fixed images**. It **only exists while running** |
| **Pod** | **One or more containers run as a single application.** Holds the containers, **storage** and a **unique network ID**, plus how to run them |
| **Persistent volume** | Storage mounted on **all containers in the pod**. **Data survives container restarts.** A pod can have several, and they **exist outside the pod's scope** |
| **Service** | Handles **networking** and tasks like **deploying pods and creating replicas** |

### NVIDIA tools for GPUs on Kubernetes

| Tool | What it does |
|---|---|
| **NVIDIA GPU Operator** | **Open-source.** **Automates deploying and managing all the NVIDIA software needed to use GPUs on Kubernetes.** Faster time to outcome and an **error-free, automated path to scale** |
| **NVIDIA Network Operator** | Installs **on top of the GPU Operator**. Installs the **host networking components needed for RDMA and GPUDirect** in the cluster, including **GPUDirect RDMA** |
| **MLNX_OFED** | NVIDIA's packaged and tested **networking libraries and drivers**. Supports **RDMA over InfiniBand and Ethernet** |
| **NVIDIA Peer Memory Driver** | Works with the network drivers to provide **RDMA between GPUs and host memory** |

---

## 3. MLOps
- **Machine Learning Operations** brings **organized, methodical discipline** to running and deploying AI projects. It's often **used with Kubernetes** and keeps infrastructure **well utilized**.
- **What it covers:**
  - **data preparation**
  - **versioning** of data, models and parameters
  - **monitoring experiments and results**
  - **deploying models for inference**
  - **monitoring model performance**
- **Benefits:**
  - better **user productivity**
  - **faster workflows**
  - **maximum resource utilization**
  - projects that **scale**
- NVIDIA works with **many MLOps partners**.

---

## 4. Slurm
- Created by **SchedMD**. An **open-source cluster management and job scheduling system for Linux clusters**.
- **Traits:**
  - **highly scalable and fault-tolerant**
  - **no kernel modifications** needed
  - **schedules jobs onto a subset of cluster resources**
  - **excellent for AI training** and highly performant
  - tied closely to **Unix and Linux**
  - easy to integrate with **existing security mechanisms**

### Slurm design

| Part | Role |
|---|---|
| **Slurm controller** | The **central manager** of workloads and cluster resources. **Users send commands here** |
| **Compute nodes** | **Run the jobs and return results.** Jobs are placed based on the **resources each job needs** |
| **Database** (optional) | Tracks **accounting records** |

### Containers on Slurm
- **NVIDIA recommends running jobs in containers.**
- **Enroot** turns containers into **unprivileged sandboxes**.
- **Pyxis** **integrates Enroot with Slurm**.
- Together they make sure **containers don't get root access** to the compute nodes.

---

## 5. NVIDIA Run:ai
- An **AI workload and GPU orchestration platform**, **built on Kubernetes**. It **maximizes GPU efficiency and utilization**.
- **Main capabilities:**
  - **dynamic resource allocation**
  - **full AI lifecycle support** (build, train, deploy, scale)
  - **strategic resource management**
- **Results:**
  - **Lower operating costs** and **shorter development cycles**.
  - **Higher utilization and less idle time.** GPUs are allocated intelligently.
  - **A unified management interface** for data scientists, engineers and IT.
- Runs across **public and private clouds, hybrid and on-prem**.

---

## Key Terms
- **Orchestration**: automating container operations for microservices, with autoscaling for inference.
- **Scheduling**: assigning jobs to compute resources. HPC-focused, with priority and preemption built in.
- [**Kubernetes**](https://www.nvidia.com/en-us/glossary/kubernetes/): open-source container orchestration from Google, maintained by CNCF.
- **Pod**: one or more containers managed as one application, with a unique network ID.
- **Namespace**: an isolated multi-tenant environment that can have a resource quota.
- **Persistent volume**: pod storage that survives container restarts.
- [**GPU Operator**](https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/latest/index.html): automates the NVIDIA software stack for GPUs on Kubernetes.
- [**Network Operator**](https://docs.nvidia.com/networking/display/kubernetes2671/index.html): adds RDMA and GPUDirect networking on top of the GPU Operator.
- [**MLNX_OFED**](https://network.nvidia.com/products/infiniband-drivers/linux/mlnx_ofed/): NVIDIA networking drivers for RDMA over InfiniBand and Ethernet.
- [**GPUDirect RDMA**](https://docs.nvidia.com/cuda/gpudirect-rdma/index.html): direct data transfer between GPUs and the network, bypassing the CPU.
- [**MLOps**](https://www.nvidia.com/en-us/glossary/mlops/): a discipline for versioning, deploying and monitoring ML.
- [**Slurm**](https://developer.nvidia.com/slurm): SchedMD's open-source job scheduler for Linux clusters.
- **Enroot / Pyxis**: unprivileged container sandboxes / the Slurm plugin that runs them.
- [**Run:ai**](https://www.nvidia.com/en-us/software/run-ai/): NVIDIA's Kubernetes-based GPU orchestration platform.

## Exam Tips
- **Orchestration (Kubernetes): containers, microservices, inference autoscaling, load balancing.** Needs meta-schedulers for advanced features.
- **Scheduling (Slurm): bare metal, HPC, priority and preemption built in, no inference.**
- **Know the Kubernetes components:** node, cluster, namespace (multi-tenancy + quota), container, pod (unique network ID), persistent volume (survives restarts), service.
- **The GPU Operator puts GPUs on Kubernetes. The Network Operator adds RDMA and GPUDirect on top of it.**
- **Slurm = controller + compute nodes (+ optional accounting database).** Created by SchedMD.
- **Enroot + Pyxis = containers on Slurm without root access.**
- **Run:ai = GPU orchestration on Kubernetes** that maximizes utilization across cloud, hybrid and on-prem.

---

## NVIDIA Documentation
Official NVIDIA pages for this lesson's main concepts (links checked November 11, 2026).

- [What Is Kubernetes?](https://www.nvidia.com/en-us/glossary/kubernetes/): NVIDIA glossary.
- [NVIDIA GPU Operator](https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/latest/index.html): GPUs on Kubernetes.
- [GPU Operator: GPUDirect RDMA and GPUDirect Storage](https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/latest/gpu-operator-rdma.html): how the GPU Operator and Network Operator work together.
- [NVIDIA Network Operator](https://docs.nvidia.com/networking/display/kubernetes2671/index.html): RDMA and GPUDirect networking on Kubernetes.
- [MLNX_OFED Linux Drivers](https://network.nvidia.com/products/infiniband-drivers/linux/mlnx_ofed/): NVIDIA InfiniBand and Ethernet drivers.
- [NVIDIA Cloud Native Technologies](https://docs.nvidia.com/datacenter/cloud-native/index.html): containers, Kubernetes and GPU telemetry docs.
- [What Is MLOps?](https://www.nvidia.com/en-us/glossary/mlops/): NVIDIA glossary.
- [Slurm at NVIDIA](https://developer.nvidia.com/slurm): the Slurm workload manager.
- [NVIDIA Run:ai](https://www.nvidia.com/en-us/software/run-ai/): product overview.
- [NVIDIA Run:ai Documentation](https://run-ai-docs.nvidia.com/): Run:ai guides.
