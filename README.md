# 🧠 AI Learnings

A personal repository documenting my journey through Artificial Intelligence, Machine Learning, and Deep Learning concepts — from foundational theory to hands-on implementations.

---

## 📚 Overview

This repository serves as a structured learning log and reference hub for AI/ML topics. Each folder contains notebooks, experiments, and notes on a specific concept or technique, built up progressively as I explore the field.

> **Goal**: Understand AI from first principles — not just *how* to use models, but *why* they work.

---

## 🗂️ Contents

### 🔤 [Tokenization](./Tokenization/)

Understanding how text is broken down into tokens before being fed into language models.

| File | Description |
|------|-------------|
| [`GPT_Tokenizer_AndrejKarpathy.ipynb`](./Tokenization/GPT_Tokenizer_AndrejKarpathy.ipynb) | Hands-on implementation of a GPT-style tokenizer, following Andrej Karpathy's approach. Covers byte-pair encoding (BPE) from scratch. |
| [`test.txt`](./Tokenization/test.txt) | Sample text corpus used for training and testing the tokenizer. |
| [`tok400.model`](./Tokenization/tok400.model) | Trained tokenizer model file with a vocabulary size of 400. |
| [`tok400.vocab`](./Tokenization/tok400.vocab) | Human-readable vocabulary file showing the 400 learned tokens and their merge rules. |

**Key concepts covered:**
- Byte-Pair Encoding (BPE) algorithm
- Building a vocabulary from a text corpus
- Encoding and decoding text using learned merges
- How tokenization affects model behavior and context length

---

## 🧭 Learning Roadmap

Topics I'm exploring (✅ = covered, 🔄 = in progress, 📌 = planned):

- 🔄 **Tokenization** — BPE, WordPiece, SentencePiece
- 📌 **Embeddings** — Word2Vec, GloVe, positional encodings
- 📌 **Attention Mechanism** — Scaled dot-product, multi-head attention
- 📌 **Transformers** — Encoder-decoder architecture, GPT vs BERT
- 📌 **Training Dynamics** — Loss landscapes, gradient flow, learning rate schedules
- 📌 **Fine-tuning & PEFT** — LoRA, adapters, prompt tuning
- 📌 **Reinforcement Learning from Human Feedback (RLHF)**

---

## 📖 References & Inspiration

- [Andrej Karpathy — *Let's build the GPT Tokenizer*](https://www.youtube.com/watch?v=zduSFxRajkE)
- [Andrej Karpathy — Neural Networks: Zero to Hero](https://karpathy.ai/zero-to-hero.html)
- [Attention Is All You Need (Vaswani et al., 2017)](https://arxiv.org/abs/1706.03762)
- [The Illustrated Transformer — Jay Alammar](https://jalammar.github.io/illustrated-transformer/)
- [HuggingFace tutorials](https://www.youtube.com/@HuggingFace)

---

## 👤 About

Personal AI/ML learning journal by **Jayanth Miriyala**.  
Built from curiosity, one notebook at a time. 🚀
