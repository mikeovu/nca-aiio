# Unit 12: AI in the Cloud Considerations

**Exam mapping:** Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript (part 3 of Unit 12, sub-unit 12.4)

---

## 1. The AI Maturity Model
A framework for **assessing how mature an organization's AI capabilities are**. Knowing your stage guides your **cloud strategy**.

| Stage | What it looks like |
|---|---|
| **1. Awareness** | Just **exploring AI**. Early conversations and experiments. **No formal strategy or investment** |
| **2. Active AI experimentation** | Experimenting in a **data science context**, with a **small team** of data scientists and engineers. AI **isn't pervasive** yet |
| **3. Operational AI in production** | AI **in production**, automating processes and improving decisions. **Best practices established** |
| **4. Systemic AI** | AI is **fully part of the digital strategy** and a **core component of every new digital project**. A defined **AI roadmap** |
| **5. Transformational AI** | AI is **in the organization's DNA**. A strong AI culture, and AI is in **every part of the business** |

---

## 2. Starting On-Premises
- **Owning hardware doesn't mean you're mature.** An on-prem organization can still be at an early stage.
- On-prem usually means one of two decisions:
  - **TCO favors ownership.** The ongoing cost of reserved cloud instances was weighed against the fixed cost of a system. This is the **CapEx vs. OpEx** trade-off.
  - **Data must stay inside your own data center.**

| On-prem benefit | Detail |
|---|---|
| **Data sovereignty and compliance** | You control your data and meet regulations |
| **Fastest iteration speed** | Spin resources up and down quickly to speed up development cycles |
| **Predictable costs** | Costs **scale linearly with usage**, which makes budgeting easier |

---

## 3. Starting in the Cloud
- Many organizations are **cloud-first or cloud-only**.
- **Elastic scale:** resources grow and shrink with **changing (temporal) needs**.
- **Minimal barriers to entry:** **every cloud provider offers NVIDIA GPU instances**, and you can turn them **on and off like a faucet**.
- **Best fit for early-stage organizations:** they're still experimenting, **training runs are short, models are small and datasets are limited**.
- **As they mature**, models and datasets grow, needs become constant, and **cloud operating expenses rise**. Many customers are already at this **inflection point**.

---

## 4. Cloud or On-Prem? The Numbers

| Fact | Number |
|---|---|
| Performance boost from **specialized AI infrastructure** vs. cloud, when **data is local and compute is in the cloud** | **2–6×** |
| Extra latency from distance between data and cloud | **+1 ms per 60 miles**, which raises the cost of **data gravity** |
| Large-enterprise IT decision makers who think **on-prem security is stronger** than cloud | **62%** |

### The answer is hybrid
- It's **not one or the other**. Use both, depending on **where you are in your AI journey**.
- **Start in the cloud:** small experiments with cloud-hosted training, to **build skills** on a small budget.
- **Inflection point:** as datasets grow, **data gravity** bites, developers spend more time **grooming each training run to avoid failure**, and **iteration slows**. That's when you may move production-scale work **on-prem**.

### A common hybrid pattern
- **On-prem: training, customization and optimization.**
  - **Full control** of the training environment (hardware, software, data).
  - **Data sensitivity and compliance:** data stays inside your own network.
  - **Data gravity alignment:** compute sits next to the data, which **reduces latency**.
- **Cloud: production inference.** Cloud **scale and flexibility** handle **varying inference loads**.

---

## 5. Key Considerations Recap
- Strategies vary: **cloud-first**, **"own the base, rent the spike"**, or **multi-cloud hybrid**.
- Some AI workloads must stay **on-prem or in specific cloud regions** because of **real-time performance, data residency or data sovereignty**.

| Consideration | Meaning |
|---|---|
| **Data locality** | Move **compute closer to the data** to cut network congestion and improve performance |
| **Data sovereignty** | Follow **country-specific rules** on where data from a location must be **stored and processed** |
| **Hybrid IT strategies** | Hybrid and multi-cloud, using **best-of-breed** options for POCs, training and deployment at scale |
| **Real-time performance** | Apps that must respond in **real time**, or give real-time analytics on **sensor data** |

---

## Key Terms
- **AI maturity model**: 5 stages, awareness → active experimentation → operational → systemic → transformational.
- **TCO**: total cost of ownership, used to compare owning systems with renting cloud instances.
- **CapEx vs. OpEx**: buying hardware up front vs. paying ongoing operating costs (cloud).
- **Data gravity**: large datasets pull compute toward them. Distance adds latency (about 1 ms per 60 miles) and cost.
- **Data sovereignty**: country rules on where data must be stored and processed.
- **Data locality**: putting compute close to the data.
- **"Own the base, rent the spike"**: own capacity for steady demand, and use the cloud for peaks.
- **Inflection point**: where growing cloud costs and data gravity make on-prem more attractive.

## Exam Tips
- **Know the five maturity stages in order:** Awareness, Active Experimentation, Operational, Systemic, Transformational.
- **On-prem benefits:** data sovereignty and compliance, fastest iteration, predictable costs that scale linearly.
- **Cloud benefits:** elastic scale, low barrier to entry (NVIDIA GPUs at every CSP). Best for **early-stage** experimentation.
- **Common hybrid pattern: train on-prem, run inference in the cloud.**
- **Numbers:** 2–6× performance with specialized infrastructure, **1 ms of latency per 60 miles**, 62% trust on-prem security more.
- **Four considerations:** data locality, data sovereignty, hybrid IT, real-time performance.

---

## NVIDIA Documentation
Official NVIDIA pages for this lesson's main concepts (links checked November 11, 2026).

- [NVIDIA Cloud Computing Solutions](https://www.nvidia.com/en-us/data-center/gpu-cloud-computing/): NVIDIA GPU instances across cloud providers.
- [NVIDIA DGX Cloud](https://www.nvidia.com/en-us/data-center/dgx-cloud/): NVIDIA's AI platform in the cloud.
- [NVIDIA DGX Platform](https://www.nvidia.com/en-us/data-center/dgx-platform/): on-premises AI infrastructure.
- [NVIDIA AI Enterprise](https://www.nvidia.com/en-us/data-center/products/ai-enterprise/): the same software stack on-prem and in the cloud, for hybrid deployments.
