# Unit 5: AI Software Ecosystem

**Exam mapping:** Topic 1, *Essential AI Knowledge*, and Topic 3, *AI Operations*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript

## What you should be able to do after this unit
1. Describe **vGPU** as the foundation the AI ecosystem sits on.
2. Describe the NVIDIA **deep learning software stack** and the **CUDA-X** ecosystem.
3. Define the steps of the AI workflow and the tools for each one.
4. Define **frameworks** and name open-source, third-party and NVIDIA examples.
5. Describe the benefits of **NGC and the Enterprise Catalog** for building a DIY AI platform.
6. Describe the benefits and use cases of **NVIDIA AI Enterprise** and NVIDIA **AI workflows**.

---

## 1. Virtual GPU (vGPU)

### Why it exists
- With remote and hybrid work, **user experience plus security** is a top IT priority.
- **Old VDI's #1 failure was user experience.** Early virtual desktops had **no GPU**, so the **host CPU** did all the capture, encoding and rendering.
- **NVIDIA vGPU** virtualizes a GPU and **shares it across multiple VMs**. That makes existing VDI faster and enables new use cases.

### vGPU products

| Product | Who it's for |
|---|---|
| **vPC (Virtual PC) / vApps (Virtual Apps)** | **Knowledge and business workers**: office apps, browsers, HD video |
| **RTX vWS (Virtual Workstation)** | **Creative and technical professionals**: CAD and design (Revit, Maya), GIS (ArcGIS Pro), oil and gas (Petrel), finance (Bloomberg), healthcare (Epic), manufacturing (CATIA, Siemens NX, SOLIDWORKS) |

It runs **on-prem and in the cloud**.

### How it works (VMware ESXi example)
1. A server with a GPU runs the **ESXi hypervisor**.
2. Install the **NVIDIA vGPU Manager** (the **VIB**) on the host. You can then **assign vGPU profiles to individual VMs**.
3. Install **NVIDIA drivers in each guest OS**. They're the **same drivers used on non-virtualized systems**.
- **Many VMs can share one GPU**, or **several GPUs can be combined for one VM**.
- Offloading work from the CPU means **more users per server**.

### Benefits beyond sharing
- **Close to bare-metal performance** for compute, with minimal overhead.
- **Management integrations** (e.g. VMware) and familiar monitoring tools give insight into GPU usage.
- **Live migration** of GPU workloads with no interruption, for **business continuity and load balancing**.
- **Flexible allocation** gives better utilization.
- **Security**: data stays in the data center.
- vGPU software is **included in NVIDIA AI Enterprise**.

---

## 2. Deep Learning Recap
- **DL is a subclass of ML.** It trains neural networks on **very large (terabyte-scale) datasets**.
- **Labeled data** (e.g. images tagged "car" or "truck") teaches the network. **Errors on the training data** are used to improve it step by step.
- Once trained, the model is deployed on **new, unlabeled data** and classifies similar items in new situations.

## 3. The AI Workflow and Its Tools

| Step | Purpose | Tools |
|---|---|---|
| **Data prep** | Make raw data usable | **RAPIDS**, **RAPIDS Accelerator for Apache Spark** |
| **Training** | Teach the model | **PyTorch**, **TensorFlow**, **NVIDIA TAO Toolkit** |
| **Optimization** | Refine for deployment | **TensorRT** |
| **Deployment / inference** | Serve predictions | **Triton Inference Server**: simple, scalable deployment of models in production |

## 4. Frameworks
- **Frameworks** are **higher-level building blocks** (an interface, library or tool) that make it easier for data scientists and domain experts to **design, train and validate** models.
- Examples:
  - **Scikit-learn**: a free Python library for classification, regression and clustering. Works with NumPy and SciPy.
  - **PyTorch, TensorFlow**: open-source ML libraries.
  - **NVIDIA Isaac Lab**: built on **Isaac Sim**, for robot training with **reinforcement and imitation learning**.

## 5. The Deep Learning Software Stack (bottom to top)

| Layer | What it is |
|---|---|
| **Hardware** | A workstation or server with one or more GPUs |
| **OS + NVIDIA driver** | The driver lets frameworks use the GPU |
| **NVIDIA container runtime** | Runs GPU-enabled Docker containers |
| **Containers from NGC** | Frameworks packaged with **all the libraries** they need for GPU acceleration |
| **CUDA Toolkit** | NVIDIA's **parallel programming model**, with optimizations for DL, ML and HPC on GPUs (the base of **CUDA-X** libraries) |

- **Containers are the preferred way to develop.** NGC hosts **over 100 containers** for GPU-accelerated apps, tools and frameworks, portable across **cloud, data center and edge**.

---

## 6. Two Ways to Build an AI Platform

| | **DIY (open source)** | **NVIDIA AI Enterprise** |
|---|---|---|
| Source | Community-maintained | NVIDIA-supported, built on open-source practices |
| QA | No dedicated QA or verification | **Tested and certified** on **past, current and future GPUs** |
| GPU support | Often **only the current GPU architecture** | Past, current and future |
| Support | **Self-service only** | **NVIDIA Enterprise Support** |
| Good for | Experimenting | **Mission-critical production** |

The software for both approaches comes from **NGC and the Enterprise Catalog**.

---

## 7. NGC Catalog
- **Why it's needed:** software stacks vary by use case (AI vs. HPC vs. genomics vs. visualization) and by platform (on-prem or cloud, bare metal, container, VM or microservice).
- **What's in it:**
  - **Containers** for AI, HPC, data science and visualization, from NVIDIA and partners. Each packages an app and its dependencies, and runs on-prem, in the cloud or at the edge.
  - **Pre-trained models** for computer vision, NLP, recommenders and more, which you can **fine-tune with your own data**. Examples:
    - general-purpose: **ResNet-50, U-Net**
    - application-specific: people and vehicle detection, pose and gaze estimation
    - conversational AI: speech recognition, text-to-speech, translation
    - They plug into SDKs such as **Riva** (speech) and **DeepStream** (video analytics).
  - **Model resumes** show the training dataset, epochs, batch size and **accuracy**, to help you pick the right model.
  - **Helm charts** for consistent deployment.
  - **Collections** bundle the building blocks for an application.

### NGC containers
- A **container** packages an app and **all its dependencies**, independent of the host OS. It gives **consistent runs** and **reproducible research**.
- NGC images are **scanned for vulnerabilities and tested**. Some are backed by NVIDIA AI Enterprise support.
- They support **multi-GPU and multi-node** workloads.
- They run on **Docker, CRI-O, containerd and Singularity**, on **bare metal, VMs and Kubernetes**.
- DL containers such as TensorFlow and PyTorch are **updated monthly**.

---

## 8. NVIDIA AI Enterprise
- A **suite of NVIDIA software** that's **portable across cloud, data center and edge**. It's built for **performance, security and stability** in development and production. It's the **easiest on-ramp**.
- **Two types of software:**
  - **Application software**: for building **AI agents, generative AI** and other AI workflows. Includes **NVIDIA NIM** and **NVIDIA NeMo**.
  - **Infrastructure software**: **GPU and networking drivers** and **Kubernetes operators** that manage accelerators for AI, data science and HPC.
- Use only the parts you need. It's **integrated with leading partner platforms** and supports the **full lifecycle of AI agents**: training, optimization and deployment.

## 9. Workloads vs. Workflows, and Blueprints
- **Workload**: something customers **already run**. NVIDIA frameworks and libraries accelerate it on GPUs.
- **AI workflow**: a **pre-packaged, tested, documented, customizable** solution for a specific use case, for teams that don't know how to start. Available on **NGC and the Enterprise Catalog** and vetted by NVIDIA.
  - It includes **frameworks, pre-trained models, training and inference pipelines, Jupyter notebooks and Helm charts**.
- **NVIDIA Blueprints** are **reference AI workflows** pre-trained for specific use cases and customizable by developers. They include:
  - reference code built on NVIDIA AI Enterprise (**NIM microservices + NeMo**)
  - deployment tools and documentation
  - a **reference architecture** covering API definitions and how the microservices interoperate
- **Why:** most enterprises struggle with the **complexity of getting to production**. Workflows give a jump-start, plus **NVIDIA Enterprise Support** when needed.

---

## Key Terms
- **vGPU**: a GPU virtualized and shared across VMs (vPC/vApps for knowledge workers, RTX vWS for professionals).
- **vGPU Manager (VIB)**: the host software that assigns **vGPU profiles** to VMs.
- **Framework**: a high-level library or tool for building models (PyTorch, TensorFlow, scikit-learn).
- **CUDA / CUDA-X**: NVIDIA's parallel programming model and its acceleration libraries.
- **NGC**: NVIDIA's catalog of GPU-optimized containers, pre-trained models, Helm charts and collections.
- **Model resume**: the training details and accuracy card for an NGC model.
- **NVIDIA AI Enterprise**: a supported, certified software suite (application + infrastructure software).
- **NIM / NeMo**: inference microservices / a framework for building and customizing generative AI.
- **AI workflow / Blueprint**: a pre-packaged reference solution for a specific use case.
- **TAO Toolkit**: NVIDIA's toolkit for training and fine-tuning models. **Riva / DeepStream**: SDKs for speech / video analytics.

## Exam Tips
- **Old VDI was slow because the CPU did the graphics.** **vGPU** fixes that by sharing a GPU across VMs.
- Know the **vGPU setup**: hypervisor → **vGPU Manager (VIB)** on the host → **vGPU profile** per VM → **NVIDIA driver in the guest**.
- vGPU supports **live migration** and gets **near bare-metal performance**.
- **Tool by step:** RAPIDS (prep), PyTorch/TensorFlow/TAO (train), TensorRT (optimize), Triton (serve).
- **NGC = containers + pre-trained models (with model resumes) + Helm charts + collections.**
- **NVIDIA AI Enterprise vs. DIY:** enterprise support, testing and certification, and **past, current and future GPU** support.
- **AI Enterprise has two kinds of software:** application (NIM, NeMo) and infrastructure (drivers, K8s operators).
- **A workload already exists and gets accelerated. A workflow is a pre-built recipe. Blueprints are reference workflows.**
