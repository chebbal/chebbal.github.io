# Prior Works That Transformers Build Upon

The "Attention Is All You Need" (2017) paper by Vaswani et al. builds on several key prior works in sequence modeling, attention mechanisms, and neural network architectures.

## Core Attention Mechanism Foundations

### Attention for Neural Machine Translation

**Neural Machine Translation by Jointly Learning to Align and Translate (2014)**
- Bahdanau, Cho & Bengio (ICLR 2015)
- Introduced attention mechanism for seq2seq models
- Soft alignment between encoder and decoder states
- Foundation for modern attention mechanisms

**Effective Approaches to Attention-based Neural Machine Translation (2015)**
- Luong, Pham & Manning (EMNLP 2015)
- Global vs local attention variants
- Different attention score functions (dot, general, concat)
- Simplified attention formulations

### Self-Attention Precursors

**Long Short-Term Memory-Networks for Machine Reading (2016)**
- Cheng, Dong & Lapata (EMNLP 2016)
- Introduced self-attention over sequences
- Attention mechanism within same sequence

**A Structured Self-attentive Sentence Embedding (2017)**
- Lin et al. (ICLR 2017)
- Self-attention for sentence embeddings
- Multiple attention heads concept emerged here

## Sequence-to-Sequence Models

**Sequence to Sequence Learning with Neural Networks (2014)**
- Sutskever, Vinyals & Le (NeurIPS 2014)
- Encoder-decoder architecture with RNNs
- Foundation for neural sequence transduction
- Introduced teacher forcing

**Learning Phrase Representations using RNN Encoder-Decoder (2014)**
- Cho et al. (EMNLP 2014)
- Introduced GRU (Gated Recurrent Unit)
- Alternative to LSTM with simpler gating mechanism

## Recurrent Neural Networks (RNNs)

**Long Short-Term Memory (1997)**
- Hochreiter & Schmidhuber (Neural Computation 1997)
- Solved vanishing gradient problem in RNNs
- Cell state and gating mechanisms
- Standard architecture before Transformers

**Empirical Evaluation of Gated Recurrent Neural Networks on Sequence Modeling (2014)**
- Chung et al.
- Comparative study of LSTM vs GRU
- Established best practices for RNN architectures

**On the Properties of Neural Machine Translation: Encoder-Decoder Approaches (2014)**
- Cho et al. (SSST 2014)
- Analysis of encoder-decoder limitations
- Motivated need for attention mechanisms

## Position Encoding and Representations

**Convolutional Sequence to Sequence Learning (2017)**
- Gehring et al. (ICML 2017)
- Used positional embeddings
- CNNs for sequence modeling (faster than RNNs)
- Demonstrated parallelization advantages

**Depthwise Separable Convolutions for Neural Machine Translation (2017)**
- Kaiser et al.
- Efficient convolution operations
- Influenced efficient transformer designs

## Multi-Head and Parallel Attention Concepts

**Outrageously Large Neural Networks: The Sparsely-Gated Mixture-of-Experts Layer (2017)**
- Shazeer et al. (ICLR 2017)
- Parallel expert networks concept
- Influenced multi-head attention design

**Massive Exploration of Neural Machine Translation Architectures (2017)**
- Britz et al. (EMNLP 2017)
- Systematic architecture search for NMT
- Identified key architectural components

## Layer Normalization and Residual Connections

**Layer Normalization (2016)**
- Ba, Kiros & Hinton
- Normalization technique for RNNs
- Critical for training deep transformers
- Alternative to batch normalization for sequences

**Deep Residual Learning for Image Recognition (2015)**
- He et al. (CVPR 2016)
- Residual connections (skip connections)
- Enabled training of very deep networks
- Used extensively in transformer layers

**Identity Mappings in Deep Residual Networks (2016)**
- He et al. (ECCV 2016)
- Pre-activation residual blocks
- Improved gradient flow

## Optimization and Training Techniques

**Adam: A Method for Stochastic Optimization (2014)**
- Kingma & Ba (ICLR 2015)
- Adaptive learning rate optimization
- Standard optimizer for transformers

**Dropout: A Simple Way to Prevent Neural Networks from Overfitting (2014)**
- Srivastava et al. (JMLR 2014)
- Regularization technique
- Used throughout transformer architecture

**Batch Normalization: Accelerating Deep Network Training (2015)**
- Ioffe & Szegedy (ICML 2015)
- Although transformers use layer norm, this motivated normalization importance

## Word Embeddings and Representations

**Word2Vec: Efficient Estimation of Word Representations in Vector Space (2013)**
- Mikolov et al.
- Distributed word representations
- Foundation for embedding layers

**GloVe: Global Vectors for Word Representation (2014)**
- Pennington, Socher & Manning (EMNLP 2014)
- Alternative word embedding approach
- Widely used in pre-transformer NLP

**Distributed Representations of Sentences and Documents (2014)**
- Le & Mikolov (ICML 2014)
- Doc2Vec and paragraph vectors
- Sequence-level representations

## Neural Machine Translation Context

**Neural Machine Translation of Rare Words with Subword Units (2015)**
- Sennrich, Haddow & Birch (ACL 2016)
- Byte-pair encoding (BPE)
- Subword tokenization used in transformers

**Google's Neural Machine Translation System (2016)**
- Wu et al.
- Large-scale NMT system with attention
- Demonstrated attention's effectiveness at scale

## Theoretical Foundations

**On the difficulty of training Recurrent Neural Networks (2013)**
- Pascanu, Mikolov & Bengio (ICML 2013)
- Analysis of vanishing/exploding gradients
- Motivated alternatives to RNNs

**Understanding the difficulty of training deep feedforward neural networks (2010)**
- Glorot & Bengio (AISTATS 2010)
- Xavier initialization
- Training stability principles

## Memory and External Attention

**Neural Turing Machines (2014)**
- Graves, Wayne & Danihelka
- External memory with attention
- Content-based addressing
- Influenced attention as memory mechanism

**Memory Networks (2014)**
- Weston, Chopra & Bordes (ICLR 2015)
- Explicit memory component with attention
- Question answering with memory

**End-To-End Memory Networks (2015)**
- Sukhbaatar et al. (NeurIPS 2015)
- Multiple attention hops over memory
- Influenced multi-layer attention stacking

## Architecture Search and Design Principles

**Neural Architecture Search with Reinforcement Learning (2016)**
- Zoph & Le (ICLR 2017)
- Automated architecture design
- Influenced thinking about optimal architectures

## Parallel and Efficient Computation

**Factorization tricks for LSTM networks (2017)**
- Kuchaiev & Ginsburg (ICLR Workshop 2017)
- Efficient computation techniques
- Motivated parallelization in transformers

## Key Insights That Led to Transformers

The transformer architecture emerged from several key insights derived from these prior works:

1. **Attention is powerful**: Bahdanau attention showed alignment helps
2. **Self-attention works**: Several 2016-2017 papers showed self-attention on same sequence
3. **Parallelization matters**: ConvS2S showed benefits over sequential RNNs
4. **Position information needed**: Learned from convolutional approaches
5. **Residual connections enable depth**: ResNet principles applied to NLP
6. **Layer normalization stabilizes training**: Critical for deep architectures
7. **Multi-head captures different relations**: Inspired by ensemble and mixture approaches

## Reading Path Recommendation

### Essential Core (Read First):
1. **Seq2Seq foundation**: Sutskever et al. (2014)
2. **Attention mechanism**: Bahdanau et al. (2014)
3. **LSTM**: Hochreiter & Schmidhuber (1997) - at least understand the concept
4. **Residual connections**: He et al. (2015)
5. **Layer Normalization**: Ba et al. (2016)

### Important Context (Read Second):
6. **Luong attention**: Luong et al. (2015)
7. **Self-attention**: Cheng et al. (2016), Lin et al. (2017)
8. **ConvS2S**: Gehring et al. (2017)
9. **Adam optimizer**: Kingma & Ba (2014)

### Background Knowledge (Optional but Helpful):
10. **Word embeddings**: Word2Vec, GloVe
11. **Memory networks**: Weston et al., Sukhbaatar et al.
12. **Neural Turing Machines**: Graves et al.
13. **Dropout**: Srivastava et al.

The transformer paper synthesized these ideas into a novel architecture that:
- Removed recurrence entirely (unlike RNNs)
- Used pure attention mechanisms (scaled dot-product)
- Introduced multi-head attention
- Combined with residual connections and layer normalization
- Achieved parallelization and superior performance

This made it revolutionary because it took the best ideas from multiple research threads and showed they could work together without recurrence, leading to the modern era of transformers and large language models.
