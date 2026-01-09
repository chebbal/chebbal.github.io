# Papers on AI Model Compilers and Optimization

This list covers key innovations in compiling and optimizing neural networks for efficient execution, from early graph optimization to modern ML compilers, auto-scheduling, and hardware-specific code generation.

## Modern AI Compiler Papers (2017-2024)

### ML Compiler Frameworks

**TVM: An Automated End-to-End Optimizing Compiler (2018)**
- "TVM: An Automated End-to-End Optimizing Compiler for Deep Learning" by Chen et al. (OSDI 2018)
- End-to-end compilation stack
- Auto-tuning with machine learning
- Hardware-agnostic intermediate representation
- Foundation for modern ML compilers

**TVM: Learning to Optimize Tensor Programs (2018)**
- "Learning to Optimize Tensor Programs with Reinforcement Learning" by Chen et al. (NeurIPS 2018)
- AutoTVM: automated optimization
- RL-based schedule search
- Learns hardware-specific optimizations

**Ansor: Auto-Scheduling for TVM (2020)**
- "Ansor: Generating High-Performance Tensor Programs for Deep Learning" by Zheng et al. (OSDI 2020)
- Automated schedule generation
- Hierarchical search space
- Evolutionary search with learned cost model
- Outperforms hand-tuned kernels

**XLA: Optimizing Compiler for TensorFlow (2017)**
- "XLA: Optimizing Compiler for Machine Learning" by TensorFlow team
- Just-in-time (JIT) compilation for TensorFlow
- Fusion of operations
- Target-specific code generation
- Used in TPU and GPU execution

**Glow: Graph Lowering Compiler (2018)**
- "Glow: Graph Lowering Compiler Techniques for Neural Networks" by Rotem et al. (arXiv 2018)
- Two-phase IR design (high-level + low-level)
- Aggressive operator fusion
- Memory optimization
- Target: CPUs and accelerators

**MLIR: Multi-Level Intermediate Representation (2020)**
- "MLIR: A Compiler Infrastructure for the End of Moore's Law" by Lattner et al. (arXiv 2020)
- Extensible multi-level IR framework
- Progressive lowering through dialects
- Reusable optimization passes
- Foundation for many modern compilers

**torch.compile (Dynamo + Inductor) (2022)**
- "TorchDynamo: Fast Python execution with graph compilation" by PyTorch team
- Python bytecode analysis for graph capture
- TorchInductor backend for code generation
- Transparent acceleration for PyTorch
- 2x average speedup

**Triton: GPU Programming Language (2021)**
- "Triton: An Intermediate Language and Compiler for Tiled Neural Network Computations" by Tillet et al. (MAPL 2019)
- Python-based GPU kernel language
- Automatic memory management and optimization
- Block-level programming abstraction
- Used for FlashAttention and other kernels

**OpenAI Triton (2023)**
- Open-sourced version of Triton
- Community-driven development
- Integration with PyTorch
- Democratizes GPU kernel development

### Auto-Scheduling and Search

**FlexTensor (2020)**
- "FlexTensor: An Automatic Schedule Exploration and Optimization Framework for Tensor Computation on Heterogeneous System" by Zheng et al. (ASPLOS 2020)
- Unified schedule space representation
- Simulated annealing search
- Multi-objective optimization

**AutoScheduler Evolution (2021)**
- Various improvements to TVM auto-scheduling
- Meta-schedule framework
- Transfer learning across models

**Halide Auto-Scheduling (2019)**
- "Learning to Optimize Halide with Tree Search and Random Programs" by Adams et al. (SIGGRAPH 2019)
- Beam search for schedule exploration
- Learned cost models
- Specialized for image processing

**Rammer: Enabling Holistic DNN Optimization (2020)**
- "Rammer: Enabling Holistic Deep Learning Compiler Optimizations with rTasks" by Ma et al. (OSDI 2020)
- Holistic operator-level parallelism
- Task-based execution model
- Better hardware utilization

**TASO: Tensor Algebra SuperOptimizer (2019)**
- "TASO: Optimizing Deep Learning Computation with Automatic Generation of Graph Substitutions" by Jia et al. (SOSP 2019)
- Graph-level optimization via substitution
- Automated discovery of optimizations
- Verifies equivalence with SMT solver

**TENSAT: Tensor Saturation (2021)**
- "Equality Saturation for Tensor Graph Superoptimization" by Yang et al. (MLSys 2021)
- E-graph based optimization
- Explores many equivalent graphs simultaneously
- More optimizations than TASO

**Equality Saturation for Deep Learning (2023)**
- "3LA: A Framework for Accelerating Shallow Neural Network Inference" by various
- Advanced e-graph techniques for ML
- Multi-pattern matching
- Combines multiple optimization strategies

### Graph-Level Optimization

**TensorFlow Graph Transforms (2016)**
- Early optimization passes in TensorFlow
- Constant folding, operator fusion
- Dead code elimination
- Foundation for XLA

**ONNX Runtime Optimizations (2019)**
- "ONNX Runtime: Enabling Interoperability and Innovation in AI" by Cheng et al.
- Framework-agnostic optimizations
- Graph partitioning for heterogeneous execution
- Quantization and mixed precision

**TorchScript Optimizations (2019)**
- Graph optimization in TorchScript
- Operator fusion patterns
- Memory planning
- Export format for PyTorch

**IREE: Intermediate Representation Execution Environment (2020)**
- "IREE: A Retargetable MLIR Compiler and Runtime" by Google
- MLIR-based compiler
- Ahead-of-time and JIT compilation
- Multi-level optimization
- Targets CPUs, GPUs, mobile, accelerators

### Operator Fusion and Memory Optimization

**Operation Fusion Strategies (2018)**
- "Optimizing DNN Computation with Relaxed Graph Substitutions" by Jia et al. (SysML 2019)
- Element-wise fusion
- Vertical and horizontal fusion
- Memory access reduction

**Nimble: Lightweight Memory Management (2020)**
- "Nimble: Lightweight and Parallel GPU Task Scheduling for Deep Learning" by Kwon et al. (NeurIPS 2020)
- Fine-grained memory management
- Dynamic memory allocation
- Reduces memory fragmentation

**TASO Memory Planning (2019)**
- Integrated memory optimization in TASO
- Optimal memory reuse
- Reduces peak memory usage

**Checkmate: Memory Optimization (2020)**
- "Checkmate: Breaking the Memory Wall with Optimal Tensor Rematerialization" by Jain et al. (MLSys 2020)
- Optimal recomputation strategy
- ILP-based solver
- Trade compute for memory

### Quantization and Low-Precision Compilation

**TensorRT: High-Performance Inference (2016)**
- "TensorRT: Programmable Inference Accelerator" by NVIDIA
- INT8 and FP16 optimization
- Layer and tensor fusion
- Kernel auto-tuning
- Industry standard for inference

**TVM Quantization Support (2019)**
- "Relay: A High-Level IR for Deep Learning" by Roesch et al.
- Quantization-aware compilation
- Mixed-precision optimization
- Calibration integration

**FBGEMM: Facebook GEneral Matrix Multiplication (2019)**
- Optimized low-precision kernels
- INT8 and FP16 GEMM
- Used in PyTorch quantization
- CPU-optimized implementation

**cuDNN INT8 Support (2018)**
- NVIDIA's optimized INT8 primitives
- Tensor Core acceleration
- Integrated into frameworks

**Neural Compressor (2021)**
- "Neural Compressor: A Unified Framework for Neural Network Compression" by Intel
- Automatic quantization and pruning
- Multi-framework support
- Optimization for Intel hardware

### Specialized Hardware Compilation

**TPU Compiler (2017)**
- Part of XLA framework
- Specialized for Google TPUs
- Systolic array mapping
- Pipeline optimization

**GraphCore Poplar (2019)**
- "Poplar: A Programmable Intermediate Representation and Compiler for Graph Processing" by Graphcore
- IPU-specific compilation
- Tile-level parallelism
- BSP (Bulk Synchronous Parallel) model

**AWS Neuron Compiler (2019)**
- Compiler for AWS Inferentia and Trainium
- Optimizes for matrix multiplication engines
- Graph partitioning for multiple chips

**Qualcomm SNPE (Snapdragon Neural Processing Engine)**
- Mobile/edge device compilation
- Power and memory optimization
- Heterogeneous execution (CPU/GPU/DSP)

**Apple Neural Engine Compiler**
- Part of Core ML
- Optimizes for ANE hardware
- On-device inference optimization

### Polyhedral Compilation for ML

**Tensor Comprehensions (2018)**
- "Tensor Comprehensions: Framework-Agnostic High-Performance Machine Learning Abstractions" by Vasilache et al. (arXiv 2018)
- Polyhedral compilation for DL
- Automatic code generation from high-level spec
- ISL (Integer Set Library) based

**Tiramisu (2019)**
- "Tiramisu: A Polyhedral Compiler for Expressing Fast and Portable Code" by Baghdadi et al. (CGO 2019)
- Polyhedral model for optimization
- Separation of algorithm and schedule
- Targets CPUs, GPUs, FPGAs

**RISE: Functional IR (2020)**
- "RISE: A Functional Pattern-Based Dialect in MLIR" by Hagedorn et al.
- Functional programming for optimization
- Pattern-based rewriting
- Composable transformations

### Dataflow and Scheduling

**Spatial Accelerators Compilation (2019)**
- "Spatial: A Language and Compiler for Application Accelerators" by Koeplinger et al. (PLDI 2018)
- High-level language for accelerators
- Automatic parallelization
- FPGA and ASIC targets

**Stream Dataflow (2020)**
- Various papers on dataflow compilation
- Pipeline parallel execution
- Memory streaming optimization

**Stateful Dataflow Multigraphs (2019)**
- "Stateful Dataflow Multigraphs: A Data-Centric Model for Performance Portability" by Ben-Nun et al. (SC 2019)
- DaCe (Data-Centric) framework
- Explicit data movement
- Multi-level optimization

### Auto-Differentiation in Compilers

**JAX: Composable Transformations (2018)**
- "JAX: Autograd and XLA" by Google
- Composable function transformations
- jit, grad, vmap, pmap
- XLA backend for compilation
- Pure functional approach

**Enzyme: Automatic Differentiation (2020)**
- "Instead of Rewriting Foreign Code for Machine Learning, Automatically Synthesize Fast Gradients" by Moses & Churavy (NeurIPS 2020)
- LLVM-based automatic differentiation
- Language-agnostic AD
- Mixed-mode differentiation

**Zygote.jl (2019)**
- "Don't Unroll Adjoint: Differentiating SSA-Form Programs" by Innes et al.
- Source-to-source AD for Julia
- Efficient reverse-mode AD
- Integrates with Julia compiler

### Domain-Specific Languages

**Halide (2013)**
- "Halide: A Language and Compiler for Optimizing Parallelism, Locality, and Recomputation in Image Processing Pipelines" by Ragan-Kelley et al. (PLDI 2013)
- Separation of algorithm and schedule
- Stencil computation optimization
- Foundational for many ML compilers

**TensorFlow MLIR Dialects (2020)**
- TF dialect, HLO dialect, Linalg dialect
- Progressive lowering strategy
- Reusable transformations

**Relay: High-Level IR for TVM (2018)**
- "Relay: A High-Level Compiler for Deep Learning" by Roesch et al. (PLDI 2018)
- Functional programming for ML graphs
- Type system for tensors
- Enables high-level optimizations

**ONNX-MLIR (2020)**
- ONNX compiler based on MLIR
- Standard operator definitions
- Framework interoperability

### Sparse Tensor Compilation

**TACO: Tensor Algebra Compiler (2017)**
- "The Tensor Algebra Compiler" by Kjolstad et al. (OOPSLA 2017)
- Sparse tensor computation
- Format-agnostic optimization
- Generates efficient code for any sparsity

**Sparse Tensor Core Support (2020)**
- "Automatic Generation of High-Performance Quantized Machine Learning Kernels" by Shao et al. (CGO 2020)
- Structured sparsity compilation
- Tensor Core acceleration for sparse ops

**SparseTIR (2023)**
- "SparseTIR: Composable Abstractions for Sparse Compilation in Deep Learning" by Ye et al. (ASPLOS 2023)
- TVM extension for sparse tensors
- Composable sparse formats
- Automatic schedule generation

### Memory Hierarchy Optimization

**Polly: Polyhedral Optimization in LLVM (2012)**
- "Polly - Performing Polyhedral Optimizations on a Low-Level Intermediate Representation" by Grosser et al. (PPoPP 2012)
- Cache optimization
- Loop tiling and fusion
- Influenced ML compiler design

**PlaidML (2018)**
- "PlaidML: A Portable Tensor Compiler" by Vertex.AI
- Tile-based optimization
- Portable across hardware
- Polynomial constraint solving

**Loop Transformations for ML (2019)**
- Various papers on tiling, unrolling
- Memory hierarchy awareness
- Cache-oblivious algorithms

### Automated Kernel Generation

**CUTLASS (2018)**
- "CUTLASS: Fast Linear Algebra in CUDA C++" by NVIDIA
- Template library for GEMM
- Systematic exploration of optimizations
- Building blocks for custom kernels

**MIOpen (2017)**
- AMD's kernel library
- Auto-tuned kernels
- Similar approach to cuDNN

**oneDNN/DNNL (2019)**
- Intel's optimized primitives
- JIT compilation for kernels
- CPU and GPU support

**CK: Composable Kernel (2022)**
- "Composable Kernel: A Composable Framework for Generating High-Performance GPU Kernels" by AMD
- Template metaprogramming approach
- Composition of optimizations
- Competitive with vendor libraries

### Profile-Guided Optimization

**AutoPhase (2019)**
- "AutoPhase: Compiler Phase-Ordering for HLS with Deep Reinforcement Learning" by various
- RL for optimization ordering
- Profile-guided decisions

**Learned Cost Models (2021)**
- Various papers on ML for cost estimation
- Faster than empirical tuning
- Transfer across hardware

**PGO for Neural Networks (2020)**
- Profile-guided graph optimization
- Runtime profiling integration
- Dynamic recompilation

### Multi-Device and Distributed Compilation

**Ray Serve Compilation (2020)**
- Compilation for distributed serving
- Graph partitioning across nodes
- Communication optimization

**OneFlow Compiler (2021)**
- "OneFlow: Redesign the Distributed Deep Learning Framework from Scratch" by Yuan et al. (arXiv 2021)
- Actor-based compilation
- Pipeline and tensor parallelism
- Static and dynamic graphs

**Alpa Compiler (2022)**
- "Alpa: Automating Inter- and Intra-Operator Parallelism for Distributed Deep Learning" by Zheng et al. (OSDI 2022)
- Automatic parallelization strategy
- Hierarchical optimization
- Compiler-based approach

**GSPMD: General and Scalable Parallelization (2021)**
- "GSPMD: General and Scalable Parallelization for ML Computation Graphs" by Xu et al. (arXiv 2021)
- Compiler-based sharding
- Automatic partitioning
- Used in JAX and TensorFlow

**Mesh-TensorFlow (2018)**
- "Mesh-TensorFlow: Deep Learning for Supercomputers" by Shazeer et al. (NeurIPS 2018)
- Language for distributed computation
- Explicit mesh of processors
- Compiler generates parallel code

### Recent Advances and Future Directions

**AITemplate (2022)**
- "AITemplate: A Unified Inference Framework for Fast, Stable Diffusion Models" by Meta
- Specialized for generative models
- Fusion and memory optimization
- 2-10x speedup for diffusion models

**TensorIR Evolution (2022)**
- "TensorIR: An Abstraction for Automatic Tensorized Program Optimization" by Feng et al. (ASPLOS 2023)
- Next-gen TVM IR
- Tensor program abstraction
- Better auto-scheduling

**Hidet (2023)**
- "Hidet: Task-Mapping Programming Paradigm for Deep Learning Tensor Programs" by Ding et al. (ASPLOS 2023)
- Explicit task mapping
- Symbolic shape compilation
- Outperforms TVM and TensorRT

**Welder: Scheduling Deep Learning Memory (2023)**
- "Welder: Scheduling Deep Learning Memory Access via Tile-graph" by Shi et al. (OSDI 2023)
- Memory access scheduling
- Tile-graph abstraction
- 20-90% speedup over baselines

**Roller: Fast and Efficient Tensor Compilation (2022)**
- "Roller: Fast and Efficient Tensor Compilation for Deep Learning" by Zhu et al. (OSDI 2022)
- Efficient schedule search
- Construction-based search space
- Faster than Ansor

**Buddy Compiler (2023)**
- MLIR-based educational compiler
- Modern compiler techniques
- Open-source and extensible

## Foundational Papers These Build Upon

### Classical Compiler Theory

**Dragon Book: Compilers (1986)**
- "Compilers: Principles, Techniques, and Tools" by Aho et al.
- IR design principles
- Optimization theory
- Foundation for all compilers

**SSA Form (1991)**
- "Efficiently Computing Static Single Assignment Form and the Control Dependence Graph" by Cytron et al.
- Static Single Assignment
- Enables many optimizations
- Standard IR format

**LLVM Architecture (2004)**
- "LLVM: A Compilation Framework for Lifelong Program Analysis & Transformation" by Lattner & Adve (CGO 2004)
- Modern compiler infrastructure
- Modular design
- Reusable optimization passes
- Foundation for many ML compilers

**GCC Optimization Passes**
- Decades of compiler optimization research
- Loop optimizations
- Dead code elimination
- Constant propagation

### Polyhedral Compilation

**Polyhedral Model (1988+)**
- "Computation of the Periodic Dependence Distances and the Optimal Permutation of Loops" by various
- Mathematical framework for loop optimization
- Affine transformations
- Foundation for memory optimization

**Integer Set Library (ISL)**
- "Integer Set Library Manual" by Verdoolaege
- Polyhedral operations
- Used by many compilers
- Set operations for optimization

**Scheduling Theory (1990s)**
- Feautrier's papers on array dataflow analysis
- Automatic parallelization theory
- Optimal scheduling algorithms

### Functional Programming for Compilation

**Continuation-Passing Style (1970s)**
- Functional programming technique
- Explicit control flow
- Used in some ML compilers

**Fusion in Functional Languages (1990s)**
- "Functional Programming with Bananas, Lenses, Envelopes and Barbed Wire" by various
- Deforestation techniques
- Optimizing functional programs
- Influenced ML graph optimization

**Rewrite Rules (1980s)**
- Term rewriting systems
- Pattern matching and substitution
- Foundation for graph optimizations like TASO

### Loop Optimization

**Loop Tiling/Blocking (1980s)**
- "The Cache Performance and Optimizations of Blocked Algorithms" by Lam et al.
- Improve cache locality
- Foundation for tensor tiling

**Loop Unrolling (1970s)**
- Classic optimization technique
- Reduces loop overhead
- Exposes instruction-level parallelism

**Loop Fusion and Fission (1980s)**
- Combining/splitting loops
- Balance locality and parallelism
- Foundation for operator fusion

### Auto-Tuning and Search

**ATLAS: Automatically Tuned Linear Algebra Software (1998)**
- "Automatically Tuned Linear Algebra Software" by Whaley & Dongarra
- Empirical optimization
- Install-time tuning
- Foundation for AutoTVM

**FFTW: Fastest Fourier Transform in the West (1998)**
- "FFTW: An Adaptive Software Architecture for the FFT" by Frigo & Johnson
- Code generation with auto-tuning
- Runtime adaptation
- Inspired ML auto-tuning

**PHiPAC (1997)**
- "PHiPAC: A Portable, High-Performance, ANSI C Coding Methodology" by Bilmes et al.
- Parameterized code generation
- Search for best parameters
- Early auto-tuning work

### Tensor Algebra

**Tensor Contraction Engine (2003)**
- "A high-level abstraction for the synthesis of high-performance algorithms" by Baumgartner et al.
- Domain-specific compilation for quantum chemistry
- Tensor operation optimization
- Influenced TACO

**BLAS/LAPACK (1970s-1990s)**
- Standardized linear algebra APIs
- Highly optimized implementations
- Foundation for deep learning kernels

**Tensor Network Contraction (2005+)**
- Physics community work on tensor operations
- Optimal contraction ordering
- Influenced sparse tensor compilation

### Graph Optimization

**Instruction Selection via Rewriting (1990s)**
- "Engineering a Simple, Efficient Code-Generator Generator" by Fraser et al.
- Tree pattern matching
- Dynamic programming for selection
- Influenced operator fusion

**Peephole Optimization (1965)**
- McKeeman's early work
- Local pattern matching
- Foundation for graph substitution

**Program Synthesis**
- "Program Synthesis" by Gulwani et al. (2017 survey)
- Automated code generation
- Search-based approaches
- Influenced TASO and equality saturation

### Hardware-Specific Optimization

**CUDA Programming Guide (2007)**
- NVIDIA's parallel programming model
- Memory hierarchy management
- Thread organization
- Foundation for GPU compilation

**OpenCL Specification (2009)**
- Cross-platform parallel programming
- Portable kernel language
- Influenced portable ML compilers

**Roofline Model (2009)**
- "Roofline: An Insightful Visual Performance Model" by Williams et al.
- Performance analysis framework
- Guides optimization decisions
- Used in ML compiler tuning

### Dataflow and Scheduling

**Dataflow Programming (1970s)**
- Dennis's dataflow machine concepts
- Asynchronous execution
- Influenced modern ML execution models

**Kahn Process Networks (1974)**
- "The Semantics of a Simple Language for Parallel Programming" by Kahn
- Deterministic parallel execution
- Foundation for dataflow graphs

**Synchronous Dataflow (1987)**
- "Synchronous Data Flow" by Lee & Messerschmitt
- Static scheduling
- Compile-time analysis
- Used in some ML compilers

### Program Verification

**SMT Solvers (2000s)**
- Z3, CVC4, and others
- Automated theorem proving
- Used in TASO for equivalence checking

**Bounded Model Checking (1990s)**
- Verification techniques
- Influenced compiler correctness

### Memory Management

**Garbage Collection (1960s+)**
- McCarthy's early work
- Various GC algorithms
- Influenced tensor memory management

**Region-Based Memory Management (1990s)**
- "Region-Based Memory Management" by Tofte & Talpin
- Explicit memory regions
- Influenced ML memory planning

### High-Performance Computing

**Loop Nest Optimization (LNO)**
- Classic HPC compiler techniques
- Decades of research
- Directly applicable to ML

**Vectorization (1970s+)**
- SIMD optimization
- Auto-vectorization techniques
- Foundation for tensor operations

**Cache-Oblivious Algorithms (1999)**
- "Cache-Oblivious Algorithms" by Frigo et al.
- Optimal cache use without tuning
- Influenced ML tiling strategies

## Reading Path Recommendation

### Essential Foundations (Read First):
1. **Compiler basics**: Dragon Book concepts → SSA form → LLVM architecture
2. **Hardware**: CUDA programming basics → Roofline model
3. **Classical optimization**: Loop tiling → Loop fusion → Vectorization
4. **Auto-tuning**: ATLAS (1998) → FFTW (1998)

### Core ML Compiler Papers (Read Second):
5. **Frameworks**: Halide (2013) → TVM (2018) → MLIR (2020)
6. **Auto-scheduling**: AutoTVM (2018) → Ansor (2020)
7. **Graph optimization**: TASO (2019) → TENSAT (2021)
8. **Domain-specific**: XLA (2017) → Glow (2018)

### Modern Techniques (Read Third):
9. **Advanced scheduling**: FlexTensor (2020) → Roller (2022) → Hidet (2023)
10. **Operator fusion**: Rammer (2020) → Advanced fusion strategies
11. **Memory optimization**: Checkmate (2020) → Welder (2023)
12. **Quantization**: TensorRT concepts → TVM quantization

### Specialized Topics (Read Fourth):
13. **Polyhedral**: Tensor Comprehensions (2018) → Tiramisu (2019)
14. **Sparse**: TACO (2017) → SparseTIR (2023)
15. **User-friendly**: Triton (2021) → torch.compile (2022)
16. **Distributed**: GSPMD (2021) → Alpa (2022)

### Advanced and Recent (Optional):
17. **Tensor algebra**: Advanced TACO papers
18. **Dataflow**: DaCe framework
19. **Auto-diff**: JAX → Enzyme (2020)
20. **Verification**: TASO equivalence checking
21. **Recent systems**: AITemplate (2022) → TensorIR (2022)

### Hardware-Specific (As Needed):
22. **GPU**: CUTLASS → CK
23. **Mobile**: SNPE concepts
24. **Accelerators**: TPU compiler → Spatial (2018)

## Key Innovation Timeline

- **1970s-1990s**: Classical compiler theory, loop optimization, BLAS
- **1998-2003**: Auto-tuning (ATLAS, FFTW), early tensor algebra
- **2004-2013**: LLVM (2004), Halide (2013)
- **2013-2017**: Halide (2013), TensorRT (2016), XLA (2017), TACO (2017)
- **2018**: TVM, Glow, Relay, Tensor Comprehensions, Mesh-TensorFlow
- **2019**: AutoTVM, TASO, Tiramisu, Ansor announced
- **2020**: MLIR, Ansor, FlexTensor, Rammer, Checkmate, Enzyme
- **2021**: TENSAT, GSPMD, Neural Compressor, Triton open-source
- **2022**: torch.compile, AITemplate, Roller, Alpa, CK, SpQR
- **2023**: Hidet, SparseTIR, Welder, TensorIR, advanced quantization
- **2024**: Continued evolution, better integration, hardware-specific optimizations

## Key Breakthroughs Enabling Practical Compilation

1. **Separation of concerns**: Halide's algorithm/schedule separation
2. **Auto-tuning**: ATLAS/FFTW → AutoTVM → Ansor (eliminates manual tuning)
3. **Multi-level IR**: MLIR enables composable optimizations
4. **Graph-level optimization**: TASO/TENSAT find non-obvious optimizations
5. **User-friendly**: Triton and torch.compile democratize GPU programming
6. **Quantization support**: TensorRT and TVM enable efficient inference
7. **Distributed compilation**: GSPMD and Alpa automate parallelization
8. **Memory optimization**: Checkmate and Welder optimize memory usage
9. **Sparse support**: TACO and SparseTIR enable efficient sparse computation
10. **Hardware portability**: MLIR and TVM support diverse backends

## Impact on ML Systems

These compiler innovations enable:
- **10-100x speedup** over naive implementations
- **Automatic optimization** replacing hand-tuned kernels
- **Hardware portability** across CPUs, GPUs, TPUs, mobile, etc.
- **Memory efficiency** for large models
- **Quantization and pruning** with minimal code changes
- **Rapid experimentation** with new architectures
- **Deployment optimization** for production systems
- **Accessible GPU programming** via high-level languages

The field continues to evolve rapidly, with current focus on:
- Better auto-scheduling for diverse hardware
- Compiler support for emerging hardware (AI accelerators)
- Integration with quantization and sparsity
- Distributed compilation for large-scale training
- User-friendly interfaces (like Triton and torch.compile)
- Formal verification of optimizations
- ML-guided optimization decisions
