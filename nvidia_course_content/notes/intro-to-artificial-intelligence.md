# Unit 2: Introduction to Artificial Intelligence

**Exam mapping:** Topic 1, *Essential AI Knowledge* (38% of the exam)
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript

## What you should be able to do after this unit
1. Describe key milestones in the evolution of AI.
2. Picture a typical AI workflow and the main steps in each phase.
3. Describe at a high level how neural networks work.
4. Identify common challenges enterprises face when adopting AI.
5. Explain the value of NVIDIA's end-to-end software stack for running AI in production.

---

## 1. Evolution of AI

| Era | When | What it is | What made it possible |
|---|---|---|---|
| **AI** | 1950s → | A broad field: computers doing things that need human-level intelligence | Early on it was limited to games (Tic-Tac-Toe, Checkers) and had few practical uses |
| **Machine Learning (ML)** | 1980s → | Uses **statistical techniques** to build a model from observed data | Relies on **human-defined classifiers / feature extractors**, e.g. linear regression, or **bag-of-words**, which made **email spam filters** possible |
| **Deep Learning (DL)** | ~2010 → | Uses **deep neural networks (DNNs)**, which **automate feature extraction** by learning from large amounts of data | Three things: **better hardware**, **large datasets** (from smartphones, webcams, social media and sensors, i.e. "big data"), and **better training algorithms** |
| **Generative AI / LLMs** | Within about a decade of DNNs | Systems that seem surprisingly human-like | Used for chatbots, virtual assistants, content generation and translation |
| **Agentic AI** | Now | Autonomous **AI agents** that **reason, plan and act** with little or no human input. They can work together as **multi-agent systems** on problems that span several domains | — |
| **Physical AI** | Now | Machines (e.g. robots) that **perceive, understand and interact with the physical world** by combining AI with **sensors and actuators** | — |

How the terms relate: **AI ⊃ ML ⊃ DL**, and **Generative AI** builds on neural networks.
- **ML** trains a model on large datasets with statistical methods so it can predict outcomes from new data.
- **DL** is the most popular ML technique today. It uses artificial neural networks and **shines for vision and speech**.
- **Generative AI** learns patterns from training data with neural networks and **creates new content** that looks human-made.

---

## 2. The AI Workflow (4 steps)

The same thing is also called the *ML workflow* or *data science workflow*. It's the process data scientists, ML engineers and AI practitioners follow to develop, train, deploy and maintain models.

| # | Step | What happens | Key facts |
|---|---|---|---|
| 1 | **Data preparation** | Collect, clean and pre-process raw data | Data **quality, diversity and relevance** matter **as much as size** |
| 2 | **Model training** | An ML/DL model learns patterns from a **labeled dataset**, often over many iterations | **The most compute-intensive step.** It benefits the most from extra hardware, more than inference does. It often uses **mixed precision (FP8, FP16)** to run faster while keeping accuracy |
| 3 | **Model optimization** | Fine-tune the model for accuracy, efficiency and fit to the use case | An iterative loop: evaluate, adjust, and repeat until it meets the deployment criteria |
| 4 | **Inference / deployment** | The trained model makes predictions or generates output from **new, unseen data** in production | Usually the **core of the AI application** |

### Example: "ImageMe" radiology clinic (detecting fractures and tumors)

| Step | NVIDIA / ecosystem tool | What it does |
|---|---|---|
| Data prep | **RAPIDS** | An open-source suite of **GPU-accelerated Python libraries** for analytics and data prep |
| Data prep | **RAPIDS Accelerator for Apache Spark** | A plug-in that **automatically intercepts and GPU-accelerates** Spark operations it can speed up. Everything else keeps running on the CPU |
| Training | **PyTorch, TensorFlow** | GPU-accelerated frameworks for training at scale, now integrated with RAPIDS |
| Optimization | **NVIDIA TensorRT** | A **deep learning inference optimizer** that tunes a trained model so it's ready to deploy and scale |
| Inference | **NVIDIA Triton Inference Server** | **Open-source** software that **standardizes model deployment and execution** and handles IT/DevOps concerns such as **load balancing** |

> Memory hook: **RAPIDS → PyTorch/TensorFlow → TensorRT → Triton** = prep → train → optimize → serve.

---

## 3. How Neural Networks Work

### Biological inspiration
Geoffrey Hinton ("godfather of deep learning") held that AI works best when it computes **the way the brain does**.

| Biological neuron part | Role |
|---|---|
| **Dendrites** | Receiving antennas. They pick up signals from neighboring neurons' terminal buttons |
| **Cell nucleus** | Processes the signal |
| **Axon** | A long branch that carries the electrical impulse |
| **Synapse** | A bridge that passes the impulse on to the next neuron's dendrites |

**Artificial neurons** (also called **nodes** or **perceptrons**) copy this behavior.

### Structure of a DNN
- **Input layer**, then **hidden layers**, then **output layer**. Connections show which nodes pass results to which.
- It's called **"deep"** because it has **many hidden layers**.
- The **design of the network** decides what task it suits. Image classification models look very different from speech recognition models. They differ in:
  - number of layers
  - nodes per layer
  - the algorithm in each node
  - how nodes are connected
- Pre-built models exist for classification, object recognition, segmentation and more. They often need **modifying to reach high accuracy** on a specific dataset.

### Deep learning workflow (cats vs. dogs example)
1. **Build a training dataset**: several thousand **labeled** images. It must be **representative**, covering many breeds, poses and environments.
2. **Pick an untrained DNN** for the task (detection, classification or segmentation) and data type (image, text, audio or video). For images this would be a **CNN such as AlexNet**.
   - AlexNet's nodes run **simple, generalized algorithms**. That is the **key advantage of DL over earlier ML**, which needed specialists to hand-build custom feature extractors for each dataset and task.
3. **Train it with a deep learning framework.** The framework feeds the images through the network.
   - Each output node reports a confidence score. Sorted from most to least confident, these scores make up the **confidence vector**.
   - The framework compares the guess with the **label**. A **correct** guess **strengthens the weights** of the connections that led to it. A **wrong** guess **reduces** those weights.
   - After **one pass** through the dataset, the model is right only a bit more than half the time, barely better than a coin flip. It needs **many more rounds** to become accurate.
4. **Limits and retraining**: if the model sees a raccoon, it gives cat and dog similar confidence. To add a raccoon class:
   - add a **third output node** (change the topology)
   - add thousands of raccoon images
   - **retrain**
5. **Optimize for inference**: a trained model no longer needs the flexibility it had during training. Two common optimizations are:
   - **layer fusion**, which reduces memory and communication overhead
   - **pruning** nodes that contribute little
6. **Deploy** the model in an application, where it infers on images it hasn't seen before.

### Training vs. inference

| | Training | Inference |
|---|---|---|
| Purpose | Learn patterns from labeled data | Predict on new, unseen data |
| Compute | **Heaviest**. Benefits most from more hardware | Lighter. The model is optimized first (fusion, pruning, TensorRT) |
| Model state | Flexible: weights keep being adjusted | Fixed, optimized for speed |

---

## 4. Who Uses AI and What Gets in Their Way

### Stakeholders in an AI data center

| Stakeholder | What they want |
|---|---|
| **AI practitioners** | An agile, **cloud-native** platform that keeps up with new AI, with the accuracy and performance to deploy faster |
| **Enterprise IT** | Infrastructure that meets AI demands. AI is a new, fast-changing, often open-source workload landing on **legacy infrastructure and technical debt** |
| **Line-of-business managers** | More models in production sooner, with **efficient use of infrastructure investments** |
| **Leaders** | The fastest **ROI** and data-driven results from AI spending |

### Challenges in adopting AI
1. **Exploding model sizes and complexity**: models need more and more compute and energy, which hurts **affordability, sustainability and access for smaller organizations**.
2. **Versatility for rich experiences**: one application, such as recommendations, voice assistants or contact centers, may need **several different models** deployed together.
3. **Performance and scalability**: training and customizing is intense and iterative, so **end-to-end performance** matters for each step and for each full iteration.

Getting AI into production takes three things:
- **tools for the full AI lifecycle**
- **compute infrastructure**
- **a robust support model** for data scientists, engineers, developers and operators

---

## 5. NVIDIA's Answer: the End-to-End AI Software Stack
- **For practitioners**: top-tier development tools, frameworks and **pre-trained models**.
- **For IT**: management and **orchestration** with performance, **high availability** and **security**.
- **Covers the full pipeline**: data prep, then training, then inference, then scaling.
- **Faster time to production** with AI workflows and pre-trained models for specific business outcomes:
  - intelligent virtual assistants
  - **digital fingerprinting** (real-time cybersecurity threat detection)
  - recommender systems for retail
- **Optimized and certified to deploy anywhere**: public cloud, data center and edge. This **lowers the risk of moving from pilot to production** when environments differ.

---

## Key Terms
- **Machine learning (ML)**: statistical models learned from data, using human-defined feature extractors.
- **Deep learning (DL)**: ML with deep neural networks that learn their own features from large datasets.
- **DNN**: a deep neural network, i.e. a network with many hidden layers.
- **Perceptron / node**: an artificial neuron.
- **CNN**: a convolutional neural network, used for images (e.g. **AlexNet**).
- **Confidence vector**: the output-node scores sorted from most to least confident.
- **Weights**: connection strengths that training adjusts up or down.
- **Mixed precision (FP8/FP16)**: lower-precision formats that make training more efficient while keeping accuracy.
- **Layer fusion / pruning**: optimizations applied after training to speed up inference.
- **Agentic AI**: autonomous agents that reason, plan and act, sometimes in multi-agent systems.
- **Physical AI**: AI plus sensors and actuators, acting in the real world.
- **RAPIDS**: GPU-accelerated Python libraries for data science and data prep.
- **TensorRT**: NVIDIA's inference optimizer.
- **Triton Inference Server**: NVIDIA's open-source model serving software. It handles deployment and load balancing.

## Exam Tips
- **Training is the most compute-intensive step** of the AI workflow, more than inference.
- **DL took off around 2010** because of three things: **hardware, big datasets and better algorithms**.
- **ML uses hand-built feature extractors. DL learns them automatically.** This is the key difference.
- Match the tool to the step: **RAPIDS** = data prep, **TensorRT** = optimize, **Triton** = serve/inference.
- The **RAPIDS Accelerator for Spark** sends GPU-friendly operations to the GPU, and the rest stay on the CPU.
- **Data quality, diversity and relevance** matter as much as dataset size.
- Adding a new class means **changing the output layer and retraining**.
- Know the **three adoption challenges**: model size/complexity, versatility (multiple models), and performance/scalability.
