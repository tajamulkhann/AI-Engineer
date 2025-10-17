### Transformer

A neural architecture that uses self-attention to model relationships in sequences without recurrence.

<img width="1340" height="759" alt="image" src="https://github.com/user-attachments/assets/3796da0e-e176-46d0-ab87-6a16b6d04215" />

#### 🧠 Transformer Architecture — Simplified (For Interviews)

**Step 1: Tokenize**

Break paragraph into sentences or sentences into words.

**Step 2: Vectorize**

Convert words into static semantic-aware embeddings (numerical vectors).

**Step 3: Positional Embedding**

Add positional embeddings to retain order information of words in a sentence.

**Step 4: Attention Layer (Important)**

Contextualize words using Query (Q), Key (K), and Value (V) vectors.

- Process:

  - Calculate similarity score between Q and K → (Dot Product)

  - Convert result to probability → (Softmax)

  - Multiply probability (e.g., 0.7, 0.2) × actual vectors

  - Take weighted sum → (V₁ × w₁ + V₂ × w₂)

**Step 5: Add Residual & Normalize**

Combine Contextual Matrix and Attention Layer outputs.

Apply Layer Normalization to stabilize training.

**Step 6: Feed Forward Network**

Multi-Layer Perceptron (MLP):

MLP 1: Expands model dimension (e.g., 2048 × 4) → learns complex patterns

Apply activation functions:

  - GELU: allows slight negative effect

  - ReLU: removes negative values

MLP 2: Compresses back (e.g., 2048 × 4 → 2048)

**Step 7: Add & Norm (Again)**

Two layers are normalized:

Attention Layer

Feed Forward Layer

**Step 8: Repeat**

Repeat steps 4 to 7 for multiple layers (transformer blocks).

**Step 9: Unembedding: Vector → Words**

Convert contextualized vectors back into words (called Unembedding).

✅ In short:
Tokenize → Embed → Add Position → Apply Attention → Normalize → Feed Forward → Repeat → Decode

#### Input → Output (flow)

Tokenize → embed → add positional encodings

Encoder: repeated self-attention + FF to produce encoded representations

Decoder: masked self-attention → encoder–decoder attention → FF to produce logits

Linear + softmax → output token probabilities → greedy/beam decode.

#### # Recurrence (Old Models) vs Seq (Transformers)

| Aspect              | Recurrence (RNN/LSTM/GRU)                       | Seq (Transformer)                                  |
|---------------------|-------------------------------------------------|---------------------------------------------------|
| Processing          | Sequential (word by word, step by step)         | Parallel (all tokens processed at once)           |
| Dependency Handling | Struggles with long-term dependencies           | Captures long-range dependencies via attention    |
| Training Speed      | Slow (cannot parallelize easily)                | Fast (highly parallelizable on GPUs/TPUs)         |
| Memory              | Remembers context through hidden states         | Remembers via self-attention across full sequence |
| Bottleneck          | Vanishing/exploding gradients in long sequences | Computational cost of attention (quadratic in seq length) |
