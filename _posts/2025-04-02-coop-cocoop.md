---
layout: post
title: CoOp & CoCoOp — Prompt Learning for Vision-Language Models
date: 2025-04-02 22:00:00
description: This post summarizes two prompt learning approaches for adapting CLIP to downstream tasks CoOp and CoCoOp.
tags: paper
categories: study
giscus_comments: true
related_posts: false
thumbnail:
---  
# 📄 CoOp & CoCoOp: Prompt Learning for Vision-Language Models

> **CoOp:** *Learning to Prompt for Vision-Language Models*, CVPR 2022  
> **CoCoOp:** *Conditional Prompt Learning for Vision-Language Models*, CVPR 2023  
> **Authors:** Kaiyang Zhou et al.  
> **Links:**  
> - [CoOp Paper](https://arxiv.org/abs/2109.01134)  
> - [CoCoOp Paper](https://arxiv.org/abs/2203.05557)  
> **Keywords:** Prompt Tuning, CLIP, Few-Shot Learning, Domain Generalization, Vision-Language Models

---

## 📌 Overview

Both **CoOp** and **CoCoOp** are prompt learning techniques developed to adapt CLIP (Contrastive Language–Image Pretraining) to downstream tasks such as classification. Instead of relying on handcrafted prompts, these methods optimize learnable prompt embeddings for improved performance, especially under limited supervision.

---

## 🧠 Key Idea

### CoOp (CVPR 2022)

- Replaces the hand-crafted prompt (e.g., "a photo of a dog") with a **learnable context vector** prepended to the class name.
- The prompt format becomes:  
  [V1] [V2] [V3] … [Vn] “class_name”  
- Only the context vectors are trainable. The CLIP text and image encoders are **frozen**.
- Strong performance in **few-shot classification**.
- Limitation: context is **static**, same for all images of a class.

---

### CoCoOp (CVPR 2023)

- Introduces a **Meta Network** that generates the context vector **conditioned on the input image**.
- Each image receives a custom prompt depending on its visual content.  
context(image) + “class_name”  
- Maintains the frozen CLIP encoders, but adds a lightweight MLP to generate dynamic prompts.
- Excels in **unseen class recognition** and **domain generalization**.
- More flexible, but slightly more complex than CoOp.

---

## ⚖️ CoOp vs CoCoOp

| Aspect                 | CoOp                            | CoCoOp                                  |
|------------------------|----------------------------------|-------------------------------------------|
| Prompt Type            | Static, learnable context       | Dynamic, image-conditioned context        |
| Class Name             | Fixed token                     | Fixed token                               |
| Text Encoder           | Frozen (CLIP)                   | Frozen (CLIP)                             |
| Image Encoder          | Frozen (CLIP)                   | Frozen (CLIP)                             |
| Learns                | Prompt embeddings                | Meta-network generating prompt embeddings |
| Strength               | Few-shot performance            | Generalization to unseen classes          |
| Limitation             | Limited to seen classes         | Slightly higher complexity                |

---

## ✅ Conclusion

- **CoOp** is well-suited for tasks where class definitions are fixed and the goal is to improve few-shot classification.
- **CoCoOp** is preferable when handling open-world scenarios or out-of-distribution data, where input-dependent prompts provide better flexibility.
- Both approaches retain CLIP’s zero-shot capabilities by keeping the encoders frozen, making them lightweight and efficient for deployment.

These works laid the foundation for many later prompt-tuning and adapter-based methods in the vision-language community.

---

