# Papers Enabling Large-Scale Model Training

This list covers key innovations in training large-scale neural networks, from optimization techniques to distributed training methods, mixed precision, and architectural innovations.

## Modern Large-Scale Training Papers (2017-2024)

### Mixed Precision and Efficient Training

**Mixed Precision Training (2017)**
- "Mixed Precision Training" by Micikevicius et al. (ICLR 2018)
- FP16 computation with FP32 master weights
- Loss scaling to prevent underflow
- 2-3x speedup with minimal accuracy loss
- Foundation for modern GPU training

**Automatic Mixed Precision for Deep Learning (2019)**
- Micikevicius et al. (NVIDIA Technical Report)
- Automated AMP in PyTorch/TensorFlow
- Dynamic loss scaling

### Distributed Training and Parallelism

**Megatron-LM (2019)**
- "Megatron-LM: Training Multi-Billion Parameter Language Models Using Model Parallelism" by Shoeybi et al. (arXiv 2019)
- Tensor model parallelism
- Efficient intra-layer parallelism
- Trained 8.3B parameter models

**Megatron-LM 2 (2021)**
- "Efficient Large-Scale Language Model Training on GPU Clusters Using Megatron-LM" by Narayanan et al. (SC 2021)
- Pipeline parallelism combined with tensor parallelism
- PTD-P (Pipeline, Tensor, Data Parallelism)
- Interleaved pipeline schedules
- Trained 1 trillion parameter models

**ZeRO: Memory Optimizations Toward Training Trillion Parameter Models (2019)**
- Rajbhandari et al. (SC 2020)
- Zero Redundancy Optimizer
- Partitions optimizer states, gradients, and parameters
- ZeRO-1, ZeRO-2, ZeRO-3 stages
- Enables massive model training with limited memory

**ZeRO-Infinity (2021)**
- "ZeRO-Infinity: Breaking the GPU Memory Wall for Extreme Scale Deep Learning" by Rajbhandari et al. (SC 2021)
- Offloading to CPU and NVMe
- Trains models with trillions of parameters
- Memory-centric tiling and bandwidth-centric partitioning

**PyTorch FSDP (2021)**
- "Fully Sharded Data Parallel: faster AI training with fewer GPUs" by Zhao et al.
- PyTorch's implementation of ZeRO concepts
- Integrated into PyTorch core
- Simplified API for sharded training

**DeepSpeed (2020)**
- "DeepSpeed: System Optimizations Enable Training Deep Learning Models with Over 100 Billion Parameters" by Rasley et al. (KDD 2020)
- Comprehensive training optimization library
- Implements ZeRO and many other optimizations
- Used to train many large models

**GPipe (2019)**
- "GPipe: Efficient Training of Giant Neural Networks using Pipeline Parallelism" by Huang et al. (NeurIPS 2019)
- Synchronous pipeline parallelism
- Gradient accumulation across micro-batches
- Re-materialization for memory efficiency

**PipeDream (2019)**
- "PipeDream: Generalized Pipeline Parallelism for DNN Training" by Narayanan et al. (SOSP 2019)
- Asynchronous pipeline parallelism
- Weight stashing to handle version inconsistency
- Better hardware utilization than GPipe

### Gradient Accumulation and Memory Optimization

**Gradient Checkpointing (2016)**
- "Training Deep Nets with Sublinear Memory Cost" by Chen et al. (arXiv 2016)
- Trade computation for memory
- Recompute activations during backward pass
- Also called activation checkpointing/recomputation

**Checkmate (2020)**
- "Checkmate: Breaking the Memory Wall with Optimal Tensor Rematerialization" by Jain et al. (MLSys 2020)
- Optimal recomputation schedules
- Automatic memory-computation tradeoff
- ILP-based solver for checkpointing

**FlashAttention (2022)**
- "FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness" by Dao et al. (NeurIPS 2022)
- IO-aware attention algorithm
- Reduces memory from O(N²) to O(N)
- 2-4x speedup on long sequences
- Critical for training with long contexts

**FlashAttention-2 (2023)**
- "FlashAttention-2: Faster Attention with Better Parallelism and Work Partitioning" by Dao (arXiv 2023)
- 2x faster than FlashAttention-1
- Better parallelism across batch and heads
- Reduced non-matmul operations

### Optimization Algorithms for Large Scale

**LAMB: Large Batch Optimization for Deep Learning (2019)**
- "Large Batch Optimization for Deep Learning: Training BERT in 76 minutes" by You et al. (ICLR 2020)
- Layer-wise adaptive learning rates
- Enables very large batch sizes (32k+)
- Maintains accuracy with faster training

**LARS: Layer-wise Adaptive Rate Scaling (2017)**
- "Large Batch Training of Convolutional Networks" by You et al. (arXiv 2017)
- Layer-wise learning rate adaptation
- Enables batch sizes up to 32k for ImageNet
- Precursor to LAMB

**AdaFactor (2018)**
- "Adafactor: Adaptive Learning Rates with Sublinear Memory Cost" by Shazeer & Stern (ICML 2018)
- Memory-efficient optimizer
- Factored second moment estimation
- Reduces optimizer memory overhead

**Adafactor Improvements (2020)**
- Used in T5 and subsequent large models
- Better stability for large-scale training

### Learning Rate Schedules and Warmup

**Accurate, Large Minibatch SGD (2017)**
- "Accurate, Large Minibatch SGD: Training ImageNet in 1 Hour" by Goyal et al. (arXiv 2017)
- Linear learning rate scaling with batch size
- Gradual warmup strategy
- Standard practice for large batch training

**Cyclical Learning Rates (2017)**
- "Cyclical Learning Rates for Training Neural Networks" by Smith (WACV 2017)
- Varying learning rates in cycles
- One-cycle policy
- Faster convergence

**Super-Convergence (2018)**
- "Super-Convergence: Very Fast Training of Neural Networks Using Large Learning Rates" by Smith & Topin (arXiv 2018)
- Extremely large learning rates with one-cycle
- Dramatically faster training

### Model Architecture Optimizations

**Switch Transformers (2021)**
- "Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity" by Fedus et al. (JMLR 2022)
- Sparse mixture-of-experts
- Simplified routing (top-1)
- Trained 1.6T parameter model
- 4x speedup over dense models

**GShard (2020)**
- "GShard: Scaling Giant Models with Conditional Computation and Automatic Sharding" by Lepikhin et al. (ICLR 2021)
- Mixture-of-experts for transformers
- Automatic sharding across devices
- 600B parameter translation model

**GLaM (2021)**
- "GLaM: Efficient Scaling of Language Models with Mixture-of-Experts" by Du et al. (ICML 2022)
- 1.2T parameters with MoE
- More efficient than dense models
- Quality comparable to GPT-3 with less compute

**Expert Choice Routing (2022)**
- "Mixture-of-Experts Meets Instruction Tuning" by Shen et al. (arXiv 2022)
- Experts choose tokens (not tokens choose experts)
- Better load balancing
- Improved training stability

### Stability and Normalization

**Root Mean Square Layer Normalization (RMSNorm) (2019)**
- "Root Mean Square Layer Normalization" by Zhang & Sennrich (NeurIPS 2019)
- Simpler than LayerNorm
- 10-15% speedup
- Used in LLaMA and other modern models

**Pre-Layer Normalization (2020)**
- "On Layer Normalization in the Transformer Architecture" by Xiong et al. (ICML 2020)
- Pre-LN instead of Post-LN
- Better training stability for deep models
- Standard in modern transformers

**Learning Rate Schedules (2019)**
- "Learning Rate Schedules for Training Neural Networks" (various)
- Cosine annealing
- Inverse square root schedules
- Critical for large model convergence

### Gradient Clipping and Numerical Stability

**Gradient Clipping for Training Very Deep Networks (2013)**
- "On the difficulty of training Recurrent Neural Networks" by Pascanu et al. (ICML 2013)
- Gradient clipping by norm or value
- Prevents gradient explosion
- Standard practice in large models

**Automatic Gradient Clipping (2020)**
- "Automatic Gradient Clipping: Improving Gradient Descent" by various
- Adaptive clipping strategies
- Used in GPT-3 and similar models

### Communication Optimization

**Ring-AllReduce (2017)**
- "Bringing HPC Techniques to Deep Learning" by Sergeev & Del Balso (NIPS Workshop 2017)
- Bandwidth-optimal gradient aggregation
- Foundation of Horovod

**Horovod (2018)**
- Sergeev & Del Balso (Uber Engineering)
- Distributed training framework
- Implements ring-allreduce
- Easy-to-use data parallelism

**NCCL: Optimized Primitives for Collective Multi-GPU Communication (2017)**
- "NCCL 2.0" by NVIDIA
- Optimized collective operations
- Used by PyTorch and TensorFlow
- Critical for multi-GPU training

**ByteScheduler (2019)**
- "A Generic Communication Scheduler for Distributed DNN Training Acceleration" by Peng et al. (SOSP 2019)
- Optimizes communication scheduling
- Overlaps computation and communication
- Works with various parallelism strategies

### Training at Scale: System Papers

**Pathways (2022)**
- "Pathways: Asynchronous Distributed Dataflow for ML" by Barham et al. (MLSys 2022)
- Google's next-gen infrastructure
- Asynchronous computation
- Used to train PaLM and Gemini

**Singularity (2022)**
- "Singularity: Planet-Scale, Preemptible and Elastic Scheduling of AI Workloads" by Qiao et al. (arXiv 2022)
- Microsoft's training infrastructure
- Preemptible training
- Efficient scheduling at scale

**Alpa (2022)**
- "Alpa: Automating Inter- and Intra-Operator Parallelism for Distributed Deep Learning" by Zheng et al. (OSDI 2022)
- Automatic parallelization strategy search
- Combines different parallelism types
- Compiler-based approach

### Efficient Fine-Tuning at Scale

**LoRA (2021)**
- "LoRA: Low-Rank Adaptation of Large Language Models" by Hu et al. (ICLR 2022)
- Low-rank decomposition for adaptation
- Trains only 0.01% of parameters
- Maintains full model quality
- Enables fine-tuning on consumer hardware

**QLoRA (2023)**
- "QLoRA: Efficient Finetuning of Quantized LLMs" by Dettmers et al. (NeurIPS 2023)
- 4-bit quantization + LoRA
- Fine-tune 65B models on single GPU
- Double quantization and paged optimizers

**Prefix Tuning (2021)**
- "Prefix-Tuning: Optimizing Continuous Prompts for Generation" by Li & Liang (ACL 2021)
- Learn continuous prompts
- Keep model frozen
- Efficient for multiple tasks

**Adapter Layers (2019)**
- "Parameter-Efficient Transfer Learning for NLP" by Houlsby et al. (ICML 2019)
- Small bottleneck layers between transformer blocks
- Train only adapters
- Multiple adapters per model

### Quantization for Training

**Mixed Precision Quantization (2020)**
- Various papers on training with quantization
- Reduces memory and computation
- Enables larger models

**8-bit Optimizers (2021)**
- "8-bit Optimizers via Block-wise Quantization" by Dettmers et al. (ICLR 2022)
- Quantize optimizer states
- No accuracy degradation
- Reduces optimizer memory by 4x

### Curriculum and Data Strategies

**Curriculum Learning (2009)**
- "Curriculum Learning" by Bengio et al. (ICML 2009)
- Start with easy examples
- Gradually increase difficulty
- Improves convergence

**Dynamic Data Scheduling (2021)**
- Various papers on data ordering
- Impacts training efficiency
- Quality-aware sampling

## Foundational Papers These Build Upon

### Early Distributed Training

**Large Scale Distributed Deep Networks (2012)**
- Dean et al. (NeurIPS 2012)
- Parameter server architecture
- Asynchronous SGD
- Foundation of distributed training at Google

**Downpour SGD and Sandblaster L-BFGS (2012)**
- Part of Dean et al. (2012)
- Asynchronous distributed optimization
- Early large-scale training methods

**Revisiting Distributed Synchronous SGD (2016)**
- Chen et al. (ICLR Workshop 2016)
- Synchronous vs asynchronous trade-offs
- Motivated synchronous approaches

### Optimization Fundamentals

**Adam: A Method for Stochastic Optimization (2014)**
- Kingma & Ba (ICLR 2015)
- Adaptive learning rates
- Foundation for most modern optimizers
- Standard baseline for comparison

**SGD with Momentum (1999)**
- "On the momentum term in gradient descent learning algorithms" by Qian
- Accelerated convergence
- Foundation for modern optimization

**RMSprop (2012)**
- Tieleman & Hinton (Coursera lecture)
- Adaptive per-parameter learning rates
- Precursor to Adam

**AdaGrad (2011)**
- "Adaptive Subgradient Methods for Online Learning and Stochastic Optimization" by Duchi et al. (JMLR 2011)
- First adaptive learning rate method
- Foundation for Adam and variants

### Batch Normalization and Normalization

**Batch Normalization (2015)**
- "Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift" by Ioffe & Szegedy (ICML 2015)
- Normalize activations
- Enables higher learning rates
- Foundation for training deep networks

**Group Normalization (2018)**
- "Group Normalization" by Wu & He (ECCV 2018)
- Works better with small batches
- Alternative to batch norm

**Layer Normalization (2016)**
- Ba, Kiros & Hinton (arXiv 2016)
- Normalization for sequences
- Used in transformers
- Independent of batch size

### Residual Connections

**Deep Residual Learning (2015)**
- He et al. (CVPR 2016)
- Skip connections enable very deep networks
- Foundation for training depth
- Critical for large models

**Identity Mappings in Deep Residual Networks (2016)**
- He et al. (ECCV 2016)
- Pre-activation residuals
- Better gradient flow

### Memory Management

**Memory-Efficient Backpropagation Through Time (2016)**
- Gruslys et al. (NeurIPS 2016)
- Early work on memory-computation tradeoffs
- Foundation for gradient checkpointing

**vDNN: Virtualized Deep Neural Networks (2016)**
- Rhu et al. (MICRO 2016)
- Offloading to host memory
- Motivated modern memory optimizations

### Parallelism Foundations

**Model Parallelism in Neural Networks (1988)**
- Early work by various researchers
- Split models across devices
- Foundation for modern model parallelism

**Data Parallelism (2010s)**
- Standard approach before model parallelism
- Foundation: split data, replicate model
- Synchronous vs asynchronous updates

**Alex Krizhevsky's Data Parallelism (2014)**
- "One weird trick for parallelizing convolutional neural networks" by Krizhevsky (arXiv 2014)
- Practical data parallelism for CNNs
- Influenced distributed training practices

### Numerical Precision

**Reduced Precision Training (2016)**
- "Training Deep Neural Networks with Low Precision Multiplications" by Courbariaux et al. (ICLR 2015)
- Early work on low-precision training
- Motivated mixed precision research

**BinaryConnect and BinaryNet (2015-2016)**
- Courbariaux et al.
- Binary weights during forward pass
- Extreme quantization research

### Communication Efficiency

**Gradient Compression (2017)**
- "Deep Gradient Compression" by Lin et al. (ICLR 2018)
- Reduce communication overhead
- Sparsification and quantization of gradients

**PowerSGD (2019)**
- "PowerSGD: Practical Low-Rank Gradient Compression for Distributed Optimization" by Vogels et al. (NeurIPS 2019)
- Low-rank gradient approximation
- Reduces communication in distributed training

### Hardware Considerations

**Understanding Deep Learning Requires Rethinking Generalization (2016)**
- Zhang et al. (ICLR 2017)
- Showed neural networks can fit random labels
- Motivated research on regularization and optimization

**GPU Architecture Papers**
- NVIDIA CUDA and GPU computing papers
- Hardware foundations for parallel training
- Tensor cores for mixed precision

## Reading Path Recommendation

### Essential Fundamentals (Read First):
1. **Optimization**: Adam (2014) → Batch Normalization (2015) → ResNets (2015)
2. **Distributed basics**: Dean et al. (2012) → Krizhevsky (2014)
3. **Mixed precision**: Micikevicius et al. (2017)

### Core Large-Scale Training (Read Second):
4. **Memory optimization**: Gradient Checkpointing (2016) → ZeRO (2019)
5. **Parallelism**: GPipe (2019) → Megatron-LM (2019) → Megatron-LM 2 (2021)
6. **Systems**: DeepSpeed (2020) → FSDP (2021)
7. **Attention efficiency**: FlashAttention (2022)

### Advanced Techniques (Read Third):
8. **Large batches**: LARS (2017) → LAMB (2019)
9. **Sparse models**: GShard (2020) → Switch Transformers (2021)
10. **Efficient fine-tuning**: LoRA (2021) → QLoRA (2023)
11. **Communication**: Ring-AllReduce → NCCL → Gradient Compression

### System-Level (Optional but Valuable):
12. **Infrastructure**: Pathways (2022) → Alpa (2022)
13. **Scheduling**: ByteScheduler → Singularity
14. **Hardware**: GPU architecture understanding

## Key Innovations Timeline

- **2012-2015**: Distributed training basics, Adam, BatchNorm, ResNets
- **2016-2017**: Gradient checkpointing, mixed precision, LARS
- **2018-2019**: Layer norm variants, GPipe, Megatron, ZeRO, LAMB
- **2020-2021**: DeepSpeed, Switch Transformers, LoRA, Megatron-2
- **2022-2023**: FlashAttention, QLoRA, improved systems
- **2024+**: Continued optimizations and new paradigms

These innovations collectively enable training models with hundreds of billions to trillions of parameters, which was impossible just a few years ago. The key breakthroughs were:
1. Mixed precision (2-3x speedup)
2. ZeRO and memory optimizations (10-100x parameter scaling)
3. Pipeline and tensor parallelism (efficient multi-GPU scaling)
4. FlashAttention (longer contexts)
5. Efficient fine-tuning (democratized access)
