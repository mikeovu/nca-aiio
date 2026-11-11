# Unit 9: Storage for AI

**Exam mapping:** Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript

## What you should be able to do after this unit
1. Identify the **storage requirements of AI workloads**.
2. Explain the key concepts of **storage file systems** and apply them to scenarios.
3. Understand the benefits of **NVIDIA-validated storage partners**.
4. Summarize **storage considerations** for AI.

---

## 1. Why AI Needs Serious Storage
- **More complex models are often more accurate, but they need more data.**
  - Image classification: **millions to billions of images**.
  - Autonomous driving: **one 1080p camera captures about 0.5 TB in 30 minutes**.
  - NLP: **billions of records a day** from email, texts, posts and more.
- Storage must be **fast, flexible and scalable**, readable and reusable by many applications, and quickly recalled by all **authorized** users.

### How storage performance is measured

| Metric | Meaning |
|---|---|
| **IOPS** (input/output operations per second) | How quickly data moves between storage and servers |
| **Bandwidth** | Also how quickly data moves between storage and servers |
| **Metadata operations** | **Finding, querying and manipulating** the stored data and its structure |

### What good storage provides
- **Visibility** across the IT infrastructure (a **shared view**).
- **Clear labeling** of what the data is and where it came from.
- **Integrity**: a way to know the data hasn't changed since it was written.
- **Resiliency**: the data can be **recovered or rebuilt** after a failure.
- Building storage that is resilient, fault-tolerant, fast *and* shared is hard, so **match the solution to users' needs**.

### Questions to ask across the data lifecycle
- How will the data be **written** and **read**? **How often** is it accessed?
- Can the storage deliver it **fast enough**? **Who needs access**?
- What happens on **failure**? Are there **privacy** concerns? **When should data be retired?**

---

## 2. Types of Storage

| Type | How it works | Pros | Cons |
|---|---|---|---|
| **Local storage** | Disk in each server | **Fast, strong performance, simple** | **Not shared.** Data must be **copied** to every server that needs it |
| **Network file system (NFS)** | A **local-like view** of data for a group of servers, using **open standard protocols** across operating systems | **Reliable, decent read/write, simple interface.** Mature features: **snapshots, replication, performance profiling** | Not the fastest at scale |
| **Parallel / distributed file systems** | Spread data across **many storage units on a high-speed network**. **Scale out in performance *and* capacity** | **The highest read/write speeds by far.** Strong single- and multi-threaded performance. Support **InfiniBand** | Need a **custom client** specific to each file system |
| **Object storage** | **No directory tree.** Data is stored as **blobs in buckets** and found by **keys** (key-value). Accessed through a **REST API** | **Scales massively**, to **petabytes and even exabytes**. Resilient through **replication** | **Not a standard**, so apps must be **rewritten** to use its API. Each pool is accessed differently |
| **Databases** (SQL, NoSQL, SQL-like) | Store and retrieve records | Unique performance and access patterns | **Less general-purpose** than file systems |

### Details worth knowing
- **NFS**
  - Created by **Sun Microsystems in 1984**. The **most common shared file system**.
  - Files are stored in **blocks** and appear **local** to servers.
  - Accessed through **POSIX** (operations like open, read, seek and close).
  - Partners: **NetApp, Pure Storage, Dell EMC**.
- **Parallel file systems** split files into **chunks (e.g. 1 MB)** spread across storage devices. They present data through **POSIX**, but through their own client.
- **Distributed file systems** may keep a file on one unit but **combine many servers** for total performance and capacity. They use **custom alternatives to NFS clients**, e.g. over **InfiniBand**.
  - Parallel and distributed partners: **DDN (DataDirect Networks), IBM, WEKA**.
- **Object storage** is used for the **largest public and private cloud repositories**. Data is usually **pulled from it into a local, network or parallel file system** to work on. Examples: **Amazon S3, Google Cloud Storage, OpenStack (Swift), Azure Blob Storage**.

### The lines between types blur
- NFS systems often **scale out** like distributed file systems.
- Some file systems offer **object access as well as a local-like view**.
- Parallel and distributed file systems often **support NFS too**.
- **Don't rule out a technology** on the assumption that it lacks a feature.
- **Multi-tier hierarchy:** **fast tiers close to the user**, slower **data lakes as the archive**.

---

## 3. NVIDIA-Validated Storage Partners
**What they are:** companies that work with NVIDIA so their storage is **compatible with NVIDIA data center solutions** such as **DGX SuperPOD and DGX BasePOD**.

| Benefit | Detail |
|---|---|
| **Seamless integration** | Storage works well with NVIDIA systems, so you get full hardware performance |
| **Performance** | Products are **tuned together with NVIDIA** |
| **Reliability** | They go through **stringent testing** for heavy data center workloads |
| **Scalability** | They grow with large deployments |
| **Security** | Built-in features protect against unauthorized access |
| **Lower cost** | Optimized solutions **avoid expensive customization or upgrades** |

They're **fully integrated, tested and ready to deploy**, which **shortens time to deployment and lowers management risk**.

---

## 4. Storage Considerations for Deep Learning
- **Reads dominate, but writes matter too.**
- **DL training reads records repeatedly, in random order.** Storage must handle **fast random access**, which puts pressure on **metadata performance**.
- **The first read may be slow. Re-reads decide training speed.** So **cache data locally in RAM or on local disk**.
- **Key metric for DL training: read and re-read performance.**
- **Closer to the GPU is faster.** Local caching **speeds up training** and **reduces load on shared storage**, so you don't have to **over-provision**.
- **Write I/O matters more as models grow**, e.g. saving very large models.
- **You'll train many models at once**, which multiplies storage needs.
- **Rule of thumb:** **fast read I/O plus data caching** gives the best overall performance for most AI workloads.
- **Data is the most important asset in an AI environment.** Accessibility and manageability are critical.

---

## Key Terms
- **IOPS**: input/output operations per second.
- **Metadata operations**: finding, querying and organizing stored data.
- **NFS**: Network File System, a standard shared file system from 1984 that uses POSIX.
- **POSIX**: the standard interface for file operations (open, read, seek, close).
- **Parallel file system**: files are split into chunks across many storage nodes, accessed through a custom client.
- **Object storage**: key-value blobs in buckets, accessed through a REST API (S3, GCS, Azure Blob).
- **Validated storage partner**: a vendor whose storage is tested with DGX SuperPOD and BasePOD.
- **Multi-tier storage**: fast tiers near compute, a slow data lake as the archive.

## Exam Tips
- **The key metric for DL training is read and re-read performance.** **Cache locally** (RAM or NVMe) to speed training and protect shared storage.
- **Training reads data randomly and repeatedly**, which **stresses metadata performance**.
- **The highest throughput comes from parallel and distributed file systems. The most common shared storage is NFS. The biggest capacity is object storage.**
- **Object storage is not POSIX.** Apps use a **REST API** and may need rewriting.
- **Local storage is fast but not shared**, so data has to be duplicated.
- **Write performance grows in importance with model size.** Training many models at once multiplies demand.
- **Validated partners work with DGX SuperPOD and BasePOD.** Know NFS partners (**NetApp, Pure, Dell EMC**) and parallel partners (**DDN, IBM, WEKA**).
