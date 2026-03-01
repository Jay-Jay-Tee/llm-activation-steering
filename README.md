# 🔐 Steering LLM Behavior via Contrastive Activation Directions
### Inference-Time Control for AI Safety & Cybersecurity

---

## 📖 Overview

This project explores inference-time behavioral steering in Large Language Models (LLMs) using contrastive activation directions.

Rather than fine-tuning model weights, we compute a direction in hidden-state space that captures the difference between:

- Direct, confident explanations
- Hedged, cautious explanations

This direction is injected during generation to bias the model toward more safety-aware behavior.

The project demonstrates how internal representations can be manipulated dynamically without retraining — a concept relevant to AI alignment, robustness, and cybersecurity applications.

---

## 🎯 Motivation

Large language models often produce:

- Overconfident responses
- Insufficient uncertainty framing
- Weak contextual risk awareness

In safety-critical domains — especially cybersecurity — controlling how models express uncertainty and limitations is crucial.

This project investigates whether such behavioral traits correspond to structured directions in representation space and whether they can be reliably controlled at inference time.

---

## 🧠 Mathematical Formulation

### Contrastive Direction

For a chosen transformer layer `L`, we extract last-token hidden states:

- h_hedged
- h_direct

The steering direction is computed as:

`v = mean(h_hedged) - mean(h_direct)`

The direction is normalized:

`v = v / ||v||`

---

### Inference-Time Intervention

During generation, the hidden state `h` at layer `L` is modified as:

`h' = h - alpha * v`

Where:

- v = normalized contrastive direction
- alpha = steering strength
- h = original hidden state
- h' = modified hidden state

No model weights are updated.

---

## 📊 Evaluation Strategy

Behavioral effects are measured using:

- Hedge marker frequency
- Semantic similarity (embedding cosine similarity)
- Keyword overlap with the prompt
- Output length changes

Layer-wise and strength-wise sweeps are performed to analyze behavioral trade-offs.

---

## ⚙️ Experimental Setup

- Base Model: Qwen2.5-0.5B-Instruct
- Embedding Model: all-MiniLM-L6-v2
- Layers Tested: 4, 6, 8, 10
- Alpha Sweep: 0.0 → 5.0

---

## 🔎 Key Concepts

- Activation Steering
- Representation Engineering
- Mechanistic Interpretability
- Inference-Time Control
- AI Safety & Alignment

---

## 📚 References

Turner et al., 2023  
"Representation Engineering: A Top-Down Approach to AI Transparency"  
https://arxiv.org/abs/2310.01405  

Subramani et al., 2022  
"Extracting Latent Steering Vectors from Pretrained Language Models"  
https://arxiv.org/abs/2205.05124  

Meng et al., 2022  
"Locating and Editing Factual Associations in GPT"  
https://arxiv.org/abs/2202.05262  

Rimsky et al., 2024  
"Steering LLM Behavior with Activation Steering"  
https://arxiv.org/abs/2402  

Li et al., 2026  
"Steering Vector Fields for Context-Aware Inference-Time Control in Large Language Models"  
https://arxiv.org/abs/2602.01654  

---

Built as an experimental AI safety and cybersecurity research project.
