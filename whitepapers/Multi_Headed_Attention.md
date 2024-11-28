# Cornell Notes: Transformer Architecture

## **Cues**
- **Transformer Architecture**: What is it?
- **Encoder-Decoder**: How does it work?
- **Input Preparation**: What are the steps?
- **Self-Attention**: How does it function?
- **Multi-Head Attention**: Why is it important?
- **Layer Components**: What are the key parts?
- **Applications**: Where is it used?

---

### **Questions and Answers**

#### **Q1: What is the transformer architecture?**
- **A**: Developed by Google in 2017, the transformer is a sequence-to-sequence model designed for tasks like language translation. It uses an encoder to process input text into a representation and a decoder to generate output text autoregressively.

#### **Q2: How does the encoder-decoder structure function?**
- **A**: The encoder processes the input sequence (e.g., French sentence) into a contextual representation, while the decoder generates the output sequence (e.g., English sentence) using this representation step by step.

#### **Q3: What are the steps in input preparation and embedding?**
1. **Normalization**: Standardizes text (e.g., removes whitespace).  
2. **Tokenization**: Converts text into tokens mapped to IDs.  
3. **Embedding**: Maps token IDs to high-dimensional vectors.  
4. **Positional Encoding**: Adds sequence position info for word order.

#### **Q4: How does self-attention work in transformers?**
1. Compute **queries (Q)**, **keys (K)**, and **values (V)** using learned weight matrices.  
2. Calculate scores: $$ \text{Score} = Q \cdot K^T $$  
3. Normalize scores: $$ \text{Attention Weights} = \text{Softmax} \left(\frac{\text{Score}}{\sqrt{d_k}}\right) $$  
4. Compute weighted values: Combine attention weights with values to generate a context-aware representation.

#### **Q5: What is multi-head attention, and why is it useful?**
- **A**: Multi-head attention uses parallel sets of Q, K, V matrices (heads) to focus on different input relationships. It enhances the model's ability to process complex patterns and long-range dependencies.

---

### **Formulas**

#### **Self-Attention**
$$ 
\text{Attention}(Q, K, V) = \text{Softmax} \left( \frac{Q K^T}{\sqrt{d_k}} \right) V 
$$  
Where:
- \( Q, K, V \): Query, Key, and Value matrices.
- \( d_k \): Dimension of the keys.

---

### **Summary (Flashcard Review)**

- **Key Idea**: The transformer is a sequence-to-sequence model with an encoder-decoder structure designed for tasks like language translation.
- **Core Mechanism**: Self-attention captures long-range dependencies by assigning weights to input relationships based on relevance.
- **Input Processing**:
  - Normalize text, tokenize into tokens mapped to IDs, convert to embeddings, and add positional encoding for order information.
- **Multi-Head Attention**: 
  - Uses multiple attention heads to extract diverse patterns and improve understanding of complex inputs.
- **Encoder**:
  - Converts input sequence into contextual representations (e.g., French sentence → representation).
- **Decoder**:
  - Autoregressively generates output (e.g., representation → English sentence).
- **Why Self-Attention?**: Ensures the model focuses on relevant parts of the sequence, outperforming RNNs in speed and accuracy.
- **Applications**:
  - Translation, summarization, and question-answering.
- **Key Components of Layers**: Multi-Head Attention, Add & Norm, Feed-Forward, Linear, and Softmax layers.
- **Efficiency**: Multi-head attention and parallel processing enable transformers to handle complex tasks with scalability and speed.

---

These flashcard-style points can help you quickly recall critical aspects of the transformer architecture for future study sessions. 🌟
