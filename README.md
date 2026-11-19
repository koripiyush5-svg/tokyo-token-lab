# ⚡ TOKYO TOKEN LAB (東京トークン研究所)
> **"Every Word Has Its Own Story. Words Break, Tokens Remain."**

[![License: MIT](https://img.shields.io/badge/License-MIT-crimson.svg)](https://opensource.org/licenses/MIT)
[![Technology](https://img.shields.io/badge/Tech-WebGL%20%7C%20Plotly.js%20%7C%20TailwindCSS-gold.svg)](#technical-architecture)
[![Theme](https://img.shields.io/badge/Theme-Tokyo%20Revengers%20Dark%20Cinematic-101114.svg)](#visual-identity)

**TOKYO TOKEN LAB** is a high-performance, client-side interactive AI developer playground and educational laboratory designed to illuminate how Artificial Intelligence transforms human language into discrete numerical tokens, builds subword vocabularies via Byte Pair Encoding (BPE), and projects high-dimensional semantic sentence embeddings into interactive 3D vector space via Principal Component Analysis (PCA).

Styled with a dark cinematic visual identity inspired by Tokyo Revengers — featuring graphite surfaces, muted crimson accents (`#C83C45`), antique gold highlights (`#C5A66A`), ambient floating particles, and Japanese urban typography.

---

## 🌟 Key Features

### 1. Interactive Tokenizer Studio
- **4 Distinct Tokenization Paradigms**:
  1. **Pretrained BPE (GPT Byte-Level)**: Byte-level subword tokenization (`cl100k_base` style) with `Ġ` (`\u0120`) leading space byte preservation and deterministic token IDs.
  2. **Educational BPE**: Character bigram merge algorithm using statistical rules learned from corpus training.
  3. **Word-Based Tokenizer**: Whitespace & punctuation segmentation demonstrating vocabulary explosion and OOV (Out-of-Vocabulary) failure modes.
  4. **Character-Based Tokenizer**: 1-gram Unicode decomposition showing sequence expansion.
- **Dynamic Token Visualizer**:
  - Interactive token pills with position indices and hover states.
  - **Token Inspector Modal**: Click any token to view Token ID, Character Length, Byte Length, and UTF-8 Hex sequences (`0x...`).
- **Live Statistics Engine**: Real-time calculation of Characters, Words, Tokens, Unique Tokens, Average Characters per Token, and Token-to-Word compression ratio.

### 2. Token Breakdown Table
- Interactive table displaying Position, Token, Token ID, Character Length, and UTF-8 byte sequences.
- Real-time search filter and column sorting (by Position, Token ID, Length, or Alphabetical).
- Duplicate token highlighting toggle.
- One-click export to CSV and JSON clipboard copy.

### 3. Vocabulary Lab — Byte Pair Encoding (BPE) Builder
- Educational BPE algorithm implementation from scratch.
- Training corpus presets (`Toy Example`, `Tokyo Cyberpunk Narrative`, `AI Research Corpus`).
- Configurable target merge count slider (2 to 25 merges).
- Step-by-step merge operations timeline with frequency statistics and merge animations.
- Initial vocabulary vs. final expanded vocabulary pill inspector.

### 4. Token Battle — 4-Way Comparison
- Head-to-head tokenizer comparison on identical sentences.
- Preset test suites for contractions, code snippets, Japanese characters, and multi-byte emojis.
- Side-by-side token count breakdown, segment chips, and compression efficiency analysis.

### 5. 3D Embedding Explorer (Major Feature)
- **High-Dimensional Vectorization Engine**: Generates 32-D semantic feature vectors across topical anchors (AI/Data, NLP/Code, Tokyo/Urban, Skills/Human).
- **Exact Mathematical PCA (Principal Component Analysis)**:
  - Computes empirical mean centroid $\mu$.
  - Centers data and builds $D \times D$ Covariance Matrix $C = \frac{X_c^T X_c}{N - 1}$.
  - Extracts top 3 principal components (PC1, PC2, PC3) via Power Iteration with Hotelling Deflation and Gram-Schmidt orthogonalization.
  - Displays variance explained along each axis.
- **Interactive 3D WebGL Scatter Plot (Plotly.js)**:
  - Cyan circular markers for sample sentences; Crimson diamond markers with gold rings for user-added sentences.
  - Camera control buttons: `3D Iso`, `PC1-PC2`, `PC1-PC3`, and `Reset View`.
  - Point click inspection and hover tooltips.
- **"TRY A WORD OR SENTENCE"**: Real-time projection of user-added text into the **exact same fitted PCA coordinate system** ($W$).
- **"EDIT SAMPLE SENTENCES"**: Expandable editor for the 7 foundational sample sentences with add, edit, delete, and re-fit controls.
- **Authentic Cosine Similarity Metric**:
  $$\cos \theta = \frac{u \cdot v}{\|u\| \|v\|}$$
  Calculated on the full high-dimensional embedding vectors with beginner-friendly interpretation.

### 6. Token Explorer & Intelligence Inspector
- Substring and pattern search across active token stream.
- Token frequency distribution bar chart.
- Repeated n-gram sequence detector and lexical diversity rating.

### 7. Learning Corner
9 comprehensive educational modules with interactive expandable cards:
1. What is tokenization?
2. Why do LLMs use tokens?
3. What are token IDs?
4. What is Byte Pair Encoding?
5. What is vocabulary size?
6. How are emojis tokenized?
7. What are context windows?
8. What are sentence embeddings?
9. How does PCA work?

---

## 🎨 Visual Identity & Theme

- **Background**: `#101114` (Deep Obsidian)
- **Secondary Background**: `#191B20` (Dark Graphite)
- **Surfaces**: `#15171D` (Card Surface) / `#1F2229` (Hover)
- **Primary Accent**: `#C83C45` (Muted Crimson)
- **Secondary Accent**: `#C5A66A` (Antique Gold)
- **Typography**: `Cinzel`, `Noto Sans JP`, `Inter`, and `JetBrains Mono`
- **Particles**: Hardware-accelerated canvas particle simulation

---

## 🚀 Getting Started

### Local Setup
No build steps or Node modules required — runs as a zero-dependency standalone web application.

```bash
# Clone the repository
git clone https://github.com/koripiyush5-svg/tokyo-token-lab.git
cd tokyo-token-lab

# Start a local web server (Python 3)
python3 -m http.server 4173

# Or with Node.js
npx serve .
```

Open your browser at `http://localhost:4173/index.html`.

---

## 📐 Mathematical Foundations

### Byte Pair Encoding (BPE)
Given an initial vocabulary $V$ containing all unique characters and an end-of-word marker `</w>`, BPE iteratively counts the frequency of all adjacent token pairs:

$$\text{argmax}_{(t_i, t_j)} \text{freq}(t_i, t_j)$$

The most frequent pair is merged into a new vocabulary token $t_{\text{new}} = t_i \oplus t_j$, repeated until the target vocabulary size or merge threshold is reached.

### Principal Component Analysis (PCA)
For sentence embedding vectors $X \in \mathbb{R}^{N \times D}$:
1. Center data: $X_c = X - \mathbf{1}\mu^T$ where $\mu = \frac{1}{N}\sum_{i=1}^N x_i$.
2. Form sample covariance: $C = \frac{1}{N-1} X_c^T X_c$.
3. Find eigenvectors $v_1, v_2, v_3$ satisfying $C v_k = \lambda_k v_k$.
4. Project any vector $x \in \mathbb{R}^D$ into 3D coordinates:
   $$z = (x - \mu) W_{3D}, \quad W_{3D} = [v_1, v_2, v_3] \in \mathbb{R}^{D \times 3}$$

---

## 📄 License
MIT License. Created by [Piyush Kori](https://github.com/koripiyush5-svg).
