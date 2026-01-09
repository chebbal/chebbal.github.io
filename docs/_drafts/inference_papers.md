# Papers Enabling Large-Scale Model Inference

This list covers key innovations in efficient inference of large neural networks, from quantization and pruning to speculative decoding, KV cache optimization, and serving systems.

## Modern Large-Scale Inference Papers (2020-2024)

### Quantization for Inference

**LLM.int8() (2022)**
- "LLM.int8(): 8-bit Matrix Multiplication for Transformers at Scale" by Dettmers et al. (NeurIPS 2022)
- Mixed-precision decomposition for outlier features
- Zero degradation 8-bit inference for 175B models
- Enables inference on consumer GPUs

**GPTQ (2022)**
- "GPTQ: Accurate Post-Training Quantization for Generative Pre-trained Transformers" by Frantar et al. (ICLR 2023)
- One-shot weight quantization to 3-4 bits
- Optimal Brain Quantization-based approach
- Minimal accuracy loss with 4x compression

**AWQ: Activation-aware Weight Quantization (2023)**
- "AWQ: Activation-aware Weight Quantization for LLM Compression and Acceleration" by Lin et al. (MLSys 2024)
- Protects salient weights based on activation magnitudes
- 4-bit quantization with better accuracy than GPTQ
- 3x speedup with W4A16 quantization

**SmoothQuant (2022)**
- "SmoothQuant: Accurate and Efficient Post-Training Quantization for Large Language Models" by Xiao et al. (ICML 2023)
- INT8 weight and activation quantization
- Migrates difficulty from activations to weights via smoothing
- Enables W8A8 inference without accuracy loss

**QuIP: 2-Bit Quantization (2023)**
- "QuIP: 2-Bit Quantization of Large Language Models With Guarantees" by Chee et al. (NeurIPS 2023)
- Aggressive 2-bit quantization
- Adaptive rounding with incoherence preprocessing
- 8x compression with reasonable quality

**QuIP#: Even Better 2-Bit (2024)**
- "QuIP#: Even Better LLM Quantization with Hadamard Incoherence and Lattice Codebooks" by Tseng et al. (arXiv 2024)
- Improved 2-bit quantization
- Hadamard transformations for incoherence
- Better than QuIP with same compression

**ZeroQuant (2022)**
- "ZeroQuant: Efficient and Affordable Post-Training Quantization for Large-Scale Transformers" by Yao et al. (NeurIPS 2022)
- Hardware-friendly quantization
- Group-wise quantization
- Integrated into DeepSpeed

**SpQR: Sparse-Quantized Representation (2023)**
- "SpQR: A Sparse-Quantized Representation for Near-Lossless LLM Weight Compression" by Dettmers et al. (arXiv 2023)
- Identifies and isolates outlier weights
- 3-4 bit quantization for most weights
- Stores outliers in higher precision

### KV Cache Optimization

**Multi-Query Attention (MQA) (2019)**
- "Fast Transformer Decoding: One Write-Head is All You Need" by Shazeer (arXiv 2019)
- Single key-value head shared across query heads
- Dramatically reduces KV cache size
- Used in PaLM and Falcon

**Grouped-Query Attention (GQA) (2023)**
- "GQA: Training Generalized Multi-Query Transformer Models from Multi-Head Checkpoints" by Ainslie et al. (EMNLP 2023)
- Middle ground between MHA and MQA
- Groups of query heads share KV heads
- Better quality than MQA with most memory savings
- Used in Llama 2

**PagedAttention (2023)**
- "Efficient Memory Management for Large Language Model Serving with PagedAttention" by Kwon et al. (SOSP 2023)
- Virtual memory-inspired KV cache management
- Non-contiguous storage of KV cache
- Core innovation in vLLM
- Reduces memory waste and fragmentation

**H2O: Heavy-Hitter Oracle (2023)**
- "H2O: Heavy-Hitter Oracle for Efficient Generative Inference of Large Language Models" by Zhang et al. (NeurIPS 2023)
- Evicts less important KV cache entries
- Keeps "heavy hitter" tokens that contribute most to attention
- Reduces KV cache by 90% with minimal quality loss

**StreamingLLM (2023)**
- "Efficient Streaming Language Models with Attention Sinks" by Xiao et al. (ICLR 2024)
- Keeps initial "attention sink" tokens + recent tokens
- Enables infinite sequence length with constant memory
- No recomputation needed for sliding window

**Scissorhands (2023)**
- "Scissorhands: Exploiting the Persistence of Importance Hypothesis for LLM KV Cache Compression at Test Time" by Liu et al. (NeurIPS 2023)
- Identifies and prunes unimportant KV cache entries
- Based on attention score patterns
- Dynamic pruning during generation

**KIVI: KV Cache in Integer (2024)**
- "KIVI: A Tuning-Free Asymmetric 2bit Quantization for KV Cache" by Liu et al. (arXiv 2024)
- 2-bit quantization of KV cache
- Per-channel quantization for keys, per-token for values
- Reduces KV cache memory by 16x

### Speculative Decoding and Parallel Sampling

**Speculative Decoding (2023)**
- "Fast Inference from Transformers via Speculative Decoding" by Leviathan et al. (ICML 2023)
- Draft model generates candidates
- Target model verifies in parallel
- 2-3x speedup with no quality change

**Medusa: Multiple Decoding Heads (2024)**
- "Medusa: Simple LLM Inference Acceleration Framework with Multiple Decoding Heads" by Cai et al. (ICML 2024)
- Multiple prediction heads for parallel token generation
- Self-speculative decoding
- 2.2x speedup without auxiliary models

**SpecInfer (2023)**
- "SpecInfer: Accelerating Generative Large Language Model Serving with Speculative Inference and Token Tree Verification" by Miao et al. (ASPLOS 2024)
- Tree-based speculative execution
- Multi-token speculation and verification
- Better parallelism than sequential speculation

**EAGLE: Early Exit with Layer-wise Speculation (2024)**
- "EAGLE: Speculative Sampling Requires Rethinking Feature Uncertainty" by Li et al. (ICML 2024)
- Auto-regressive draft model with feature borrowing
- Better draft quality than small separate models
- 3x speedup on average

**Lookahead Decoding (2023)**
- "Break the Sequential Dependency of LLM Inference Using Lookahead Decoding" by Fu et al. (arXiv 2023)
- Parallel token generation with N-gram verification
- No additional models needed
- 1.5-2x speedup

### Model Compression and Pruning

**Lottery Ticket Hypothesis (2018)**
- "The Lottery Ticket Hypothesis: Finding Sparse, Trainable Neural Networks" by Frankle & Carbin (ICLR 2019)
- Sparse subnetworks can match full network performance
- Motivated structured pruning research
- Foundation for compression techniques

**Structured Pruning (2021)**
- "Structured Pruning Learns Compact and Accurate Models" by Xia et al. (ACL 2022)
- Remove entire attention heads, FFN dimensions
- Maintains structured operations for hardware efficiency
- Better speedup than unstructured pruning

**SparseGPT (2023)**
- "SparseGPT: Massive Language Models Can Be Accurately Pruned in One-Shot" by Frantar & Alistarh (ICML 2023)
- One-shot pruning to 50% sparsity
- No retraining required
- Minimal accuracy degradation

**Wanda: Pruning by Weights and Activations (2023)**
- "A Simple and Effective Pruning Approach for Large Language Models" by Sun et al. (ICLR 2024)
- Prunes based on weight magnitude × input activation
- No retraining or weight update needed
- Outperforms magnitude pruning

**LLM-Pruner (2023)**
- "LLM-Pruner: On the Structural Pruning of Large Language Models" by Ma et al. (NeurIPS 2023)
- Task-agnostic structural pruning
- Removes coupled structures (layers, heads, dimensions)
- Efficient post-training recovery

**Shortened LLaMA (2023)**
- "Shortened LLaMA: Depth Pruning for Large Language Models with Comparison of Retraining Methods" by Kim et al. (EMNLP 2023)
- Layer removal strategies
- Efficient depth reduction
- Fast inference with acceptable quality loss

### Knowledge Distillation

**DistilBERT (2019)**
- "DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter" by Sanh et al. (NeurIPS Workshop 2019)
- 40% size reduction, 60% speed increase
- Retains 97% of BERT's performance
- Triple loss: distillation, masked LM, cosine distance

**TinyBERT (2020)**
- "TinyBERT: Distilling BERT for Natural Language Understanding" by Jiao et al. (Findings of EMNLP 2020)
- Two-stage distillation (general + task-specific)
- 7.5x smaller, 9.4x faster
- Attention-based distillation

**MiniLM (2020)**
- "MiniLM: Deep Self-Attention Distillation for Task-Agnostic Compression of Pre-Trained Transformers" by Wang et al. (NeurIPS 2020)
- Self-attention distribution distillation
- Better than DistilBERT with same size
- Value-relation and attention transfer

**Task-Agnostic Distillation for LLMs (2023)**
- "Knowledge Distillation of Large Language Models" by Gu et al. (arXiv 2023)
- Distilling GPT-scale models
- Minimizes forward KL divergence
- Maintains reasoning capabilities

**GKD: Generalized Knowledge Distillation (2023)**
- "On-Policy Distillation of Language Models: Learning from Self-Generated Mistakes" by Agarwal et al. (ICLR 2024)
- On-policy student data generation
- Learns from student's own distribution
- Better than standard distillation

### Mixture-of-Experts (MoE) Inference

**MoE Layer Skip (2023)**
- "Accelerating Transformer Inference for Translation via Parallel Decoding" by various
- Skip inactive experts during inference
- Conditional computation benefits
- Sparse activation reduces compute

**Expert Offloading (2023)**
- "Fast Inference of Mixture-of-Experts Language Models with Offloading" by Eliseev & Mazur (arXiv 2023)
- Offload inactive experts to CPU/disk
- Load experts on-demand
- Enables large MoE inference on limited GPUs

**ExpertChoice: Better Load Balancing (2022)**
- "Mixture-of-Experts with Expert Choice Routing" by Zhou et al. (NeurIPS 2022)
- Experts select tokens instead of vice versa
- Better load balancing during inference
- More predictable latency

### Attention Mechanism Optimizations

**Flash-Decoding (2023)**
- "Flash-Decoding for long-context inference" by Dao (arXiv 2023)
- Optimized attention for decode phase
- Parallelizes attention over sequence length
- Up to 8x faster than standard decoding

**Multi-Head Latent Attention (MLA) (2024)**
- "DeepSeek-V2: A Strong, Economical, and Efficient Mixture-of-Experts Language Model" by DeepSeek-AI (arXiv 2024)
- Compresses KV cache via latent vectors
- Reduces KV cache significantly
- Used in DeepSeek-V2

**Linear Attention for Inference (2023)**
- Various papers on linear attention mechanisms
- O(N) complexity instead of O(N²)
- Trade-off between quality and speed
- Practical for very long contexts

### Batching and Scheduling

**Continuous Batching (2022)**
- "Orca: A Distributed Serving System for Transformer-Based Generative Models" by Yu et al. (OSDI 2022)
- Iteration-level scheduling
- Add/remove requests dynamically
- Much better GPU utilization than static batching

**Dynamic Batching Strategies (2023)**
- Various papers on request scheduling
- Priority-based scheduling
- Fair scheduling with SLO guarantees
- Throughput-latency trade-offs

**FastServe (2023)**
- "FastServe: Fast Distributed Inference Serving for Large Language Models" by Wu et al. (arXiv 2023)
- Preemptive scheduling
- Job migration between GPUs
- Optimizes for multiple objectives

### Serving Systems

**vLLM (2023)**
- "Efficient Memory Management for Large Language Model Serving with PagedAttention" by Kwon et al. (SOSP 2023)
- PagedAttention for memory management
- Continuous batching
- 24x higher throughput than HuggingFace
- De facto standard for LLM serving

**TensorRT-LLM (2023)**
- NVIDIA's optimized inference engine
- Fuses operations, optimizes kernels
- INT4/INT8/FP8 quantization support
- In-flight batching

**Text Generation Inference (TGI) (2023)**
- HuggingFace's production-ready serving
- Continuous batching
- Tensor parallelism
- Flash attention integration

**DeepSpeed-Inference (2022)**
- "DeepSpeed Inference: Enabling Efficient Inference of Transformer Models at Unprecedented Scale" by Aminabadi et al. (SC 2022)
- Inference-optimized kernels
- Tensor parallelism for inference
- ZeRO-Inference for large models

**FlexGen (2023)**
- "FlexGen: High-Throughput Generative Inference of Large Language Models with a Single GPU" by Sheng et al. (ICML 2023)
- Offloading strategy for single GPU
- Throughput-oriented design
- Trades latency for higher throughput

**LightLLM (2023)**
- "LightLLM: A Lightweight and High-Performance LLM Inference Framework" by Bytedance
- Optimized inference kernels
- Token attention for fine-grained scheduling
- SLO-aware scheduling

### Model Architecture for Efficient Inference

**Retentive Networks (RetNet) (2023)**
- "Retentive Network: A Successor to Transformer for Large Language Models" by Sun et al. (arXiv 2023)
- O(1) complexity per step during inference
- Parallel training, recurrent inference
- Competitive with Transformers

**RWKV: RNN with Transformer Performance (2023)**
- "RWKV: Reinventing RNNs for the Transformer Era" by Peng et al. (EMNLP 2023)
- Linear attention with RNN inference
- Constant memory and computation during generation
- Scales to billions of parameters

**Mamba: Selective State Space Models (2023)**
- "Mamba: Linear-Time Sequence Modeling with Selective State Spaces" by Gu & Dao (arXiv 2023)
- Selective SSM mechanism
- O(N) scaling for training and inference
- Competitive with Transformers on language tasks

**Hyena Hierarchy (2023)**
- "Hyena Hierarchy: Towards Larger Convolutional Language Models" by Poli et al. (ICML 2023)
- Subquadratic attention alternative
- Long convolutions with gating
- 100x faster than attention for long sequences

### Low-Precision Inference

**FP8 Inference (2022)**
- "FP8 Formats for Deep Learning" by Micikevicius et al. (arXiv 2022)
- 8-bit floating point formats (E4M3, E5M2)
- Maintained accuracy vs FP16
- 2x speedup on H100 GPUs

**INT4 Inference (2023)**
- Various papers on 4-bit integer inference
- Optimal formats (INT4, NF4)
- Activation quantization strategies
- Supported by modern hardware

**GGML and llama.cpp (2023)**
- "ggml: Tensor library for machine learning" by Gerganov
- CPU-optimized inference
- Quantization (Q4, Q5, Q8)
- Enables local inference on CPUs

### Prompt Caching and Reuse

**Prompt Caching (2023)**
- Various implementations by API providers
- Cache KV states for repeated prompts
- Significant cost and latency reduction
- System prompts cached automatically

**SGLang: Structured Generation Language (2023)**
- "SGLang: Efficient Execution of Structured Language Model Programs" by Zheng et al. (arXiv 2023)
- Automatic prefix caching
- Shared computation for common prefixes
- 5x speedup for multi-turn conversations

**RadixAttention (2024)**
- "SGLang: Efficient Execution of Structured Language Model Programs" by Zheng et al.
- LRU-based automatic KV cache management
- Shared KV cache across requests
- Reduces redundant computation

## Foundational Papers These Build Upon

### Quantization Foundations

**Fixed-Point Quantization (2015)**
- "Deep Compression: Compressing Deep Neural Networks with Pruning, Trained Quantization and Huffman Coding" by Han et al. (ICLR 2016)
- Pioneered DNN quantization
- Pruning + quantization + coding
- 35-49x compression

**Binary Neural Networks (2016)**
- "Binarized Neural Networks" by Courbariaux et al. (NeurIPS 2016)
- Extreme 1-bit quantization
- Showed feasibility of ultra-low precision

**Quantization-Aware Training (2018)**
- "Quantization and Training of Neural Networks for Efficient Integer-Arithmetic-Only Inference" by Jacob et al. (CVPR 2018)
- Training with quantization simulation
- Integer-only inference
- Industry standard approach

**Post-Training Quantization (2019)**
- "Data-Free Quantization Through Weight Equalization and Bias Correction" by Nagel et al. (ICCV 2019)
- No training data needed
- Cross-layer equalization
- Practical deployment approach

### Pruning Foundations

**Optimal Brain Damage (1989)**
- "Optimal Brain Damage" by LeCun et al. (NeurIPS 1989)
- Second-order derivative information for pruning
- Theoretical foundation for modern pruning

**Optimal Brain Surgeon (1992)**
- "Optimal Brain Surgeon and General Network Pruning" by Hassibi et al.
- Improved OBD with better approximations
- Foundation for GPTQ

**Magnitude Pruning (2015)**
- "Learning both Weights and Connections for Efficient Neural Networks" by Han et al. (NeurIPS 2015)
- Simple magnitude-based pruning
- Iterative pruning and fine-tuning
- Baseline for all pruning work

### Distillation Foundations

**Knowledge Distillation (2015)**
- "Distilling the Knowledge in a Neural Network" by Hinton et al. (NeurIPS Workshop 2014)
- Teacher-student framework
- Temperature-scaled softmax
- Foundation for all distillation work

**Feature Distillation (2017)**
- "Paying More Attention to Attention: Improving the Performance of Convolutional Neural Networks via Attention Transfer" by Zagoruyko & Komodakis (ICLR 2017)
- Attention map distillation
- Intermediate feature matching

### Attention and Memory

**Attention Is All You Need (2017)**
- Vaswani et al. (NeurIPS 2017)
- Original transformer architecture
- Foundation for all modern LLMs
- Defines the inference problem

**Efficient Transformers Survey (2020)**
- "Efficient Transformers: A Survey" by Tay et al. (ACM Computing Surveys 2022)
- Comprehensive survey of attention variants
- Categorizes efficiency approaches
- Guides research directions

**Sparse Attention Patterns (2019)**
- "Generating Long Sequences with Sparse Transformers" by Child et al. (arXiv 2019)
- Factorized sparse attention
- O(N√N) complexity
- Inspired efficient attention research

**Linformer (2020)**
- "Linformer: Self-Attention with Linear Complexity" by Wang et al. (arXiv 2020)
- Linear attention via low-rank approximation
- Theoretical foundation for linear attention

**Reformer (2020)**
- "Reformer: The Efficient Transformer" by Kitaev et al. (ICLR 2020)
- LSH attention for efficiency
- Reversible layers for memory
- Comprehensive efficiency approach

### Memory Management

**Virtual Memory Concepts**
- Classic OS papers on paging
- Inspired PagedAttention design
- Memory allocation strategies

**Tensor Memory Management (2018)**
- Various papers on tensor allocation
- Memory pool strategies
- Influenced inference serving design

### Parallel Decoding Foundations

**Parallel Decoding Basics (2018)**
- Early work on non-autoregressive generation
- Motivated parallel sampling research

**Non-Autoregressive Translation (2018)**
- "Non-Autoregressive Neural Machine Translation" by Gu et al. (ICLR 2018)
- Generate all tokens in parallel
- Trade quality for speed
- Inspired speculative decoding

**Blockwise Parallel Decoding (2018)**
- "Blockwise Parallel Decoding for Deep Autoregressive Models" by Stern et al. (NeurIPS 2018)
- Early parallel generation ideas
- Verify-and-correct approach

### Model Architecture Alternatives

**State Space Models (2021)**
- "Efficiently Modeling Long Sequences with Structured State Spaces" by Gu et al. (ICLR 2022)
- S4 model foundation
- Inspired Mamba and others

**Linear RNNs (2021)**
- Various papers reviving RNN research
- Linear complexity alternatives to attention

### Hardware and Systems

**GPU Architecture Understanding**
- CUDA programming guides
- Memory hierarchy (HBM, SRAM, registers)
- Roofline model for performance

**CUDA Programming**
- Parallel programming patterns
- Kernel optimization techniques
- Foundation for custom kernels

**Tensor Cores**
- Mixed precision matrix multiplication
- Hardware acceleration for quantization
- Influences algorithm design

### Batching and Scheduling

**GPU Job Scheduling (2020s)**
- Various systems papers on GPU sharing
- Fair scheduling algorithms
- SLO-aware resource allocation

**Request Batching (2010s)**
- Early work on dynamic batching
- Online serving optimization
- Latency-throughput tradeoffs

## Reading Path Recommendation

### Essential Fundamentals (Read First):
1. **Quantization basics**: Deep Compression (2016) → QAT (2018) → PTQ (2019)
2. **Distillation**: Hinton et al. (2015) → DistilBERT (2019)
3. **Pruning**: Magnitude Pruning (2015) → Lottery Ticket (2018)
4. **Attention efficiency**: Transformer (2017) → Efficient Transformers Survey (2020)

### Modern Quantization (Read Second):
5. **8-bit**: LLM.int8() (2022) → SmoothQuant (2022)
6. **4-bit**: GPTQ (2022) → AWQ (2023)
7. **2-bit**: QuIP (2023) → QuIP# (2024)

### KV Cache Optimization (Read Second):
8. **Attention variants**: MQA (2019) → GQA (2023)
9. **Cache management**: PagedAttention (2023) → H2O (2023) → StreamingLLM (2023)
10. **Cache quantization**: KIVI (2024)

### Parallel Generation (Read Third):
11. **Speculative decoding**: Leviathan et al. (2023) → Medusa (2024) → EAGLE (2024)
12. **System support**: SpecInfer (2023)

### Pruning and Compression (Read Third):
13. **LLM pruning**: SparseGPT (2023) → Wanda (2023) → LLM-Pruner (2023)
14. **Structured pruning**: Layer removal approaches

### Serving Systems (Read Fourth):
15. **Memory management**: vLLM/PagedAttention (2023)
16. **Batching**: Orca (2022) → Continuous batching approaches
17. **Production systems**: DeepSpeed-Inference (2022) → TensorRT-LLM (2023)
18. **Offloading**: FlexGen (2023) → MoE offloading (2023)

### Advanced Topics (Optional):
19. **Alternative architectures**: Mamba (2023) → RWKV (2023) → RetNet (2023)
20. **Prompt optimization**: SGLang (2023) → RadixAttention (2024)
21. **Low precision**: FP8 (2022) → INT4 approaches
22. **Flash attention**: Flash-Decoding (2023) → MLA (2024)

## Key Innovation Timeline

- **2015-2017**: Quantization, pruning, and distillation foundations
- **2018-2019**: QAT, PTQ, DistilBERT, MQA
- **2020-2021**: Efficient attention variants, serving basics
- **2022**: LLM.int8(), GPTQ, SmoothQuant, Orca, DeepSpeed-Inference
- **2023**: AWQ, PagedAttention/vLLM, speculative decoding, H2O, SparseGPT, Wanda, alternative architectures (Mamba, RWKV)
- **2024**: Medusa, EAGLE, KIVI, QuIP#, advanced serving, MLA

## Key Breakthroughs Enabling Practical Inference

1. **Quantization**: 4-bit quantization (GPTQ, AWQ) enables running 70B models on consumer GPUs
2. **KV Cache**: PagedAttention reduces memory waste by 80%+, enabling 2-4x higher throughput
3. **Speculative Decoding**: 2-3x speedup without quality loss
4. **GQA**: 90% KV cache reduction vs MHA with minimal quality loss
5. **Continuous Batching**: 10x+ throughput improvement vs static batching
6. **Flash Attention**: Enables long context inference
7. **MoE Offloading**: Makes trillion-parameter models accessible
8. **Alternative Architectures**: Linear complexity models (Mamba) for very long contexts

These innovations collectively enable:
- Running 70B models on single consumer GPUs (quantization + efficient attention)
- Serving thousands of users with reasonable latency (vLLM + continuous batching)
- Processing 100k+ token contexts (Flash attention + streaming)
- 2-10x cost reduction for inference (quantization + batching + speculative decoding)
