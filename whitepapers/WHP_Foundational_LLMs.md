# 📘 FoundationalLLMs.md

## 🌟 Topic: Foundational Large Language Models & Text Generation

This is a summary of the **"Foundational Large Language Models & Text Generation"** whitepaper. I used [**"The Cornell Note-Taking System"**](https://lsc.cornell.edu/how-to-study/taking-notes/cornell-note-taking-system/) to create this summary. Reading the summary in this format before diving into the whitepaper helped me focus better and understand the content in half the time as usual.

### ✏️ **Cues**
- 🔍 Definition of LLMs and their importance.
- 🧠 Transformer architecture: self-attention, encoder-decoder.
- 🚀 Key advancements: GPTs, BERT, Chinchilla, Gemini.
- 🔧 Fine-tuning techniques: SFT, RLHF, PEFT.
- ⚡ Optimization: Quantization, Distillation.
- 💡 Applications: Translation, summarization, chatbots.

---

### ❓ **Questions and Answers**

#### **Q1: What are foundational LLMs?**
- **A**: Large Language Models trained on massive datasets to predict sequences of words, enabling tasks like translation, summarization, and text generation. 🌍

#### **Q2: Why are transformers superior to RNNs?**
- **A**: Transformers parallelize processing with self-attention, making them faster and better at capturing long-term dependencies. ⚡

#### **Q3: What are the steps of self-attention?**
1. Compute query (Q), key (K), and value (V) matrices. 🗂️  
2. Calculate attention scores:  
  ```math
   \text{Attention}(Q, K, V) = \text{Softmax} \left(\frac{QK^T}{\sqrt{d_k}}\right) V 
  ```
3. Combine weighted values for context. 🎯

#### **Q4: What is fine-tuning, and why is it important?**
- **A**: Adapting pre-trained LLMs for specific tasks using smaller datasets to improve performance without retraining from scratch. 🔧

#### **Q5: How does Reinforcement Learning from Human Feedback (RLHF) work?**
1. Train a Reward Model (RM) on human preferences. 👩‍🏫  
2. Use RM with reinforcement learning to fine-tune LLM behavior. 🏆

#### **Q6: What is Chinchilla's key contribution?**
- **A**: Balancing model size and data to achieve compute-optimal performance. 🐭

#### **Q7: What are the trade-offs in optimizing LLMs?**
- **A**:
  - **Quality vs Latency/Cost**: Smaller models or quantization trade accuracy for speed. ⚖️  
  - **Latency vs Throughput**: Parallelization improves bulk inference but may increase single-query latency. ⏳

---

### 🧮 **Formulas**

#### **🧠 Self-Attention**

```math
\text{Attention}(Q, K, V) = \text{Softmax} \left(\frac{QK^T}{\sqrt{d_k}}\right) V
```
Where:
- $` Q, K, V `$: Query, Key, Value matrices.  
- $` d_k `$: Key dimension.

#### **📏 Scaling Law for Compute (Chinchilla)**

```math
\text{Model Size} \propto C^{0.5}, \quad \text{Data Size} \propto C^{0.5}
```

#### **⚡ Quantization Precision**
- Default: 32-bit floats.  
- Reduced: 8-bit or 4-bit integers for speed and memory efficiency. 🔧

---

### 📝 **Summaries**

#### **🛠️ Transformer Basics**
- **Encoder-Decoder**: Encodes input into contextual embeddings; decodes to output sequence. 🔄
- **Self-Attention**: Captures dependencies across tokens. 🤔
- **Multi-Head Attention**: Processes diverse relationships in parallel. 🌐

#### **🌍 Key Model Evolution**
1. **GPT-1**: Decoder-only; first unsupervised pre-training model. 🚀
2. **BERT**: Encoder-only; excels at contextual understanding. 🧠
3. **Chinchilla**: Compute-efficient scaling; smaller yet superior. 🐭
4. **Gemini**: Multimodal reasoning across text, images, audio, and video. 🌟

#### **🔧 Fine-Tuning Techniques**
1. **SFT**: Supervised fine-tuning for task-specific improvements. ✅
2. **RLHF**: Aligns outputs with human preferences. 🤝
3. **PEFT**: Parameter-efficient tuning methods like LoRA and Adapters. 📉

#### **⚙️ Inference Optimization**
- **Quantization**: Reduces memory and computational load. 💾
- **Distillation**: Trains smaller models using larger ones as teachers. 🎓

💬

🏆

---

