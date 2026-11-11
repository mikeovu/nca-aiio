# Unit 3: Generative AI and Beyond (Generative AI Overview)

**Exam mapping:** Topic 1, *Essential AI Knowledge* (38% of the exam)
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript

## What you should be able to do after this unit
1. Explain what generative AI is and how the technology works.
2. Discuss generative AI market trends and the challenges in this space.
3. Describe the steps enterprises take to unlock new business opportunities with generative AI.

---

## 1. What Generative AI Is

- **Generative AI** is a **subset of AI** that **creates new data or content**, such as text, images and multimedia, from patterns learned in a dataset.
- **What sets it apart is versatility.** It goes well beyond text and chat: it can generate realistic **images, video, music, even whole virtual environments**.

### Use cases by industry

| Industry | Generative AI use cases |
|---|---|
| **Finance** | Fraud detection, personalized banking, investment insights |
| **Healthcare** | Molecule simulation, **drug discovery**, clinical trial data analysis |
| **Retail** | Personalized shopping, automated catalog descriptions, automatic price optimization |
| **Manufacturing** | Factory simulation, product design, **predictive maintenance** |

---

## 2. Foundation Models

- **Foundation models** are the **base that generative AI systems are built from**. They provide the starting framework for language structure, semantics and context.
- They're **neural networks trained on massive *unlabeled* datasets**, and they handle many jobs: generating text and images, summarizing, translating and more.
- **Key breakthrough:** they can use **unsupervised or semi-supervised learning**. The model finds patterns and structure on its own, so it **doesn't need labeled data**.
- **Unlabeled data** is raw text, images, audio or video with no predefined categories, labels or annotations. It's **abundant and diverse**, coming from the internet, social media and proprietary datasets.

### Example foundation models

| Model | What it does |
|---|---|
| **DALL-E** | Realistic images from text descriptions. Also image captioning, editing and manipulation |
| **Edify** | A **diffusion model** that makes photorealistic images from any text prompt |
| **Llama 2** | Diverse, high-quality natural-language text for content creation, language understanding and conversational AI |
| **NVIDIA GPT** | A family of **production-ready LLMs** you can tune for enterprise apps: product descriptions, customer Q&A, writing code |
| **GPT-4** | Human-like text and content, images and music, plus conversational Q&A |

---

## 3. How LLMs Work

- **LLMs** are a turning point. They learn **context**, **infer intent**, can be **independently creative**, and can be **fine-tuned** for many different tasks.
- They're built on a neural network architecture called the **transformer**.
- **Two stages:** **pre-training** on huge text datasets, then **fine-tuning** for specific tasks.
- **Goal of a language model: predict the next word** given the words that come before it. This works for human languages and for programming languages.

### Generating text, step by step
1. The user gives a **prompt**, e.g. "Write a review about an Italian restaurant I visited and enjoyed."
2. The prompt is broken into **tokens**, which are fed into the model.
3. The model **predicts the next word** from the tokens so far, then feeds it back in. It generates **one word at a time**.
4. This repeats until the user stops or the model reaches a **predetermined stopping point**.

### Key mechanics
- **Tokens** are the **smallest units of meaning**: words, characters, sub-words or other symbols.
- **Self-attention** is how the transformer understands **relationships between tokens and concepts**. It assigns each token a **score, called a weight**, to capture how strongly items relate.

### Why GPUs
- Generative AI is full of **complex math and heavy computation**.
- GPUs excel at **parallel processing, matrix operations, memory capacity and memory bandwidth**.
- The result is **faster training *and* inference than CPUs**, the ability to **work with large-scale models**, and support for **real-time applications**.
- Example: **ChatGPT was trained on 10,000 NVIDIA GPUs for weeks.**

---

## 4. Challenges and Risks

Adoption involves **technical, ethical and regulatory** issues. **Guardrails**, meaning rules, mitigate inappropriate outcomes.

| Risk | What to watch for |
|---|---|
| **Data privacy** | Watch **healthcare and finance** use cases closely to prevent leaks of money-related or sensitive data |
| **IP rights and copyright** | Platforms should mitigate infringement of creators' work |
| **Bias, errors and limitations** | Models are as biased as people, because they're **trained on our own biases** |
| **Ethical implications** | It's unclear **who is responsible** for harmful output: the developers, the users or the technology |
| **Malevolent activities** | Bad actors can use it too, e.g. **fraudulent scams** |

---

## 5. Generative AI in the Enterprise

- Enterprises that used **traditional AI** for **classification, named entity recognition (NER) and NLP** are **gradually moving those tasks to LLMs**.

### Generative AI vs. traditional AI

| | Generative AI | Traditional AI |
|---|---|---|
| Does | **Produces new content** from learned patterns | **Detects patterns, makes decisions**, analytics, **classifies data, detects fraud** |
| Compute | Heavy | **Less compute-intensive** |
| Relationship | **Complementary, not mutually exclusive** | Still the right fit for many use cases |

### The customization spectrum (from least to most investment)

| Level | What the enterprise does | Investment |
|---|---|---|
| **Generative AI as a service** (the largest group, e.g. ChatGPT) | Writes a prompt and gets a response. If the answer is poor, they **refine the prompt**. **The model doesn't change** | Lowest |
| **Moderate customization** | Adds parameters to an existing **pre-trained model** and **slightly tunes it** | Needs infrastructure expertise and investment |
| **Extensive customization** | **Builds its own foundation model**, with extensive fine-tuning | Most infrastructure and AI expertise |

- **Building a foundation model from scratch** takes huge amounts of data and compute, so it's **very costly**. It's usually done by **big tech, research institutions and well-funded startups**.
- **Customizing a pre-trained model** needs **less data, fewer resources and less expertise**. You feed it domain-specific data and tasks and adjust its parameters, which still requires knowing the model's capabilities, data format and evaluation metrics.
- **The most common choice:** take an **existing foundation model and fine-tune it**, because it's more cost-effective.

### Why building custom LLMs is hard
1. **Data:** you need massive, diverse, high-quality data, and the **collection, curation, storage and management** that go with it.
2. **Compute:** training at this scale needs **large, expensive infrastructure**.
3. **Software:** you need tools for both **training and inference**, from algorithm development to accelerating inference on **distributed infrastructure**.
4. **Expertise:** you need teams skilled in AI, ML and data science, who are **hard to find and keep**.

---

## 6. Getting Started: 5 Steps for Enterprises

1. **Identify the business opportunity.** Pick use cases with **big business impact** that your **unique data** can improve.
2. **Build out domain and AI teams.** Pair internal people with **partner and application-provider AI expertise** to form an interdisciplinary team.
3. **Analyze data for training and customization.** **Acquire, refine and protect** the data.
4. **Invest in accelerated infrastructure.** Assess current infrastructure, architecture and operating model, including **cost and energy consumption**.
5. **Develop a plan for responsible AI.** Use tools and best practices so models act ethically.

> In short, deploying generative AI isn't only about technology. It means aligning **business goals, team capabilities, data strategy, infrastructure readiness and responsible AI**.

---

## 7. Building a Generative AI App: the LLM Workflow

| # | Phase | What happens |
|---|---|---|
| 1 | **Data acquisition** | Collect data from public datasets, web scraping, user-generated content or proprietary data. It must be **diverse and representative** of the target domain |
| 2 | **Data curation** | **Clean, filter and organize** the data |
| 3 | **Pre-training** | Expose the model to a **vast text corpus** so it learns language patterns. This usually **starts from a foundation model** |
| 4 | **Customization** | Adapt the generic model to a **specific task or domain** for better accuracy, efficiency and effectiveness |
| 5 | **Model evaluation** | Measure how well the model learned and how accurately it predicts on **unseen data** |
| 6 | **Inference** | Deploy the model to turn input into output such as classifications, predictions or recommendations |
| 7 | **Guardrails** | Add these for **ethical, safe, responsible use**, reducing misuse and misinterpretation of generated text |

---

## 8. The NVIDIA Generative AI Platform

It rests on three things: **robust hardware**, **versatile software** and **enterprise-grade support**. Together they make a production-ready way to build **custom LLMs** for language, multimodal, healthcare, life sciences and visual content.

Think of it as a **pyramid, from top to bottom**:

| Layer | What it is |
|---|---|
| **NVIDIA AI Foundations** (top) | Tools and services for customizing enterprise generative AI:<br>• **NeMo**: text / language<br>• **Picasso**: visual content<br>• **BioNeMo**: biology |
| **NVIDIA AI Enterprise** (middle) | A **software suite** that streamlines development and deployment of **generative AI, computer vision and speech AI**, so teams spend less time on maintenance and tuning |
| **Accelerated compute infrastructure** (base) | Flexible. Runs **anywhere: cloud or on-premises** |

---

## Key Terms
- [**Generative AI**](https://www.nvidia.com/en-us/glossary/generative-ai/): AI that creates new content (text, images, video, music, virtual environments) from learned patterns.
- [**Foundation model**](https://blogs.nvidia.com/blog/what-are-foundation-models/): a large neural network pre-trained on massive unlabeled data that serves as the base for many tasks.
- **Unsupervised / semi-supervised learning**: learning patterns without labels, or with only a few.
- [**LLM**](https://www.nvidia.com/en-us/glossary/large-language-models/): a large language model, a transformer-based model that predicts the next token.
- [**Transformer**](https://blogs.nvidia.com/blog/what-is-a-transformer-model/): the neural network architecture behind LLMs. It uses self-attention.
- [**Self-attention**](https://blogs.nvidia.com/blog/what-is-a-transformer-model/): assigns weights between tokens to model how they relate.
- [**Token**](https://blogs.nvidia.com/blog/ai-tokens-explained/): the smallest unit of meaning: a word, sub-word, character or symbol.
- **Prompt**: the user's input that starts generation.
- [**Pre-training vs. fine-tuning / customization**](https://blogs.nvidia.com/blog/what-is-a-pretrained-ai-model/): general learning on huge data vs. adapting the model to a specific domain or task.
- **Diffusion model**: a type of image-generation model, e.g. Edify.
- [**Guardrails**](https://docs.nvidia.com/nemo/guardrails/about-nemo-guardrails-library/overview): rules that keep model output safe, ethical and appropriate.
- [**NeMo / Picasso / BioNeMo**](https://www.nvidia.com/en-us/ai-data-science/products/nemo/): NVIDIA AI Foundations services for language / visual / biology.

## Exam Tips
- **Foundation models train on *unlabeled* data** with unsupervised or semi-supervised learning. Contrast this with Unit 2's labeled-data training.
- **An LLM's core job is to predict the next word/token.** Know that the **transformer** and **self-attention** are the mechanism behind it.
- **GPUs speed up both training and inference** because of parallelism, matrix math, memory capacity and bandwidth.
- **Generative and traditional AI are complementary.** Traditional AI is **less compute-intensive** and still fits many use cases.
- **Customization spectrum:** as a service (prompt only, model unchanged), then moderate (tune a pre-trained model), then extensive (build your own foundation model). **Fine-tuning an existing model is the cost-effective norm.**
- **The 4 barriers to custom LLMs:** data, compute, software and expertise.
- **The 5 enterprise steps:** opportunity, teams, data, infrastructure, responsible AI.
- **The NVIDIA stack from top to bottom:** AI Foundations (NeMo, Picasso, BioNeMo), then **AI Enterprise**, then accelerated infrastructure (cloud or on-prem).

---

## NVIDIA Documentation
Official NVIDIA pages for this lesson's main concepts (links checked November 10, 2026).

- [What Is Generative AI?](https://www.nvidia.com/en-us/glossary/generative-ai/): NVIDIA glossary entry.
- [What Are Large Language Models?](https://www.nvidia.com/en-us/glossary/large-language-models/): NVIDIA glossary entry.
- [What Are Foundation Models?](https://blogs.nvidia.com/blog/what-are-foundation-models/): NVIDIA blog.
- [What Is a Transformer Model?](https://blogs.nvidia.com/blog/what-is-a-transformer-model/): NVIDIA blog on transformers and self-attention.
- [What Are AI Tokens?](https://blogs.nvidia.com/blog/ai-tokens-explained/): NVIDIA blog.
- [What Is a Pretrained AI Model?](https://blogs.nvidia.com/blog/what-is-a-pretrained-ai-model/): NVIDIA blog on pre-training and fine-tuning.
- [NVIDIA NeMo](https://www.nvidia.com/en-us/ai-data-science/products/nemo/): NVIDIA's platform for building and customizing generative AI.
- [NeMo Guardrails](https://docs.nvidia.com/nemo/guardrails/about-nemo-guardrails-library/overview): library for adding guardrails to LLM apps.
- [NVIDIA AI Enterprise](https://www.nvidia.com/en-us/data-center/products/ai-enterprise/): the software layer of the NVIDIA generative AI platform.
