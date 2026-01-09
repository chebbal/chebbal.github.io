# Foundational Papers: Vision-Language Models (VLMs) and Vision-Language-Action Models (VLAs)

## Vision-Language Models (VLMs)

### Foundational VLM Papers

**CLIP (2021)**
- "Learning Transferable Visual Models From Natural Language Supervision" by Radford et al.
- Introduced contrastive learning between images and text at scale
- One of the most influential papers for vision-language alignment

**ALIGN (2021)**
- "Scaling Up Visual and Vision-Language Representation Learning With Noisy Text Supervision" by Jia et al.
- Demonstrated that noisy web data at scale can work well for vision-language learning

**Flamingo (2022)**
- "Flamingo: a Visual Language Model for Few-Shot Learning" by Alayrac et al.
- Introduced interleaved vision-language modeling with few-shot capabilities
- Used frozen language models with cross-attention to visual features

**BLIP (2022)**
- "BLIP: Bootstrapping Language-Image Pre-training" by Li et al.
- Unified understanding and generation tasks
- Introduced caption bootstrapping with filtering

**BLIP-2 (2023)**
- "BLIP-2: Bootstrapping Language-Image Pre-training with Frozen Image Encoders and Large Language Models" by Li et al.
- Introduced Q-Former to bridge frozen vision and language models efficiently

**LLaVA (2023)**
- "Visual Instruction Tuning" by Liu et al.
- First to show instruction tuning works well for vision-language tasks
- Simple architecture connecting CLIP vision encoder to LLaMA

**GPT-4V/GPT-4 Vision (2023)**
- OpenAI's multimodal model (technical details in system card)
- Demonstrated state-of-the-art multimodal understanding

**Gemini (2023)**
- "Gemini: A Family of Highly Capable Multimodal Models" by Google DeepMind
- Natively multimodal architecture trained from scratch

### Must-Read Prerequisites for VLMs

**Transformer Architecture**
- "Attention Is All You Need" (2017) - Vaswani et al.
- Foundation for modern architectures

**Vision Transformers**
- "An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale" (ViT, 2020) - Dosovitskiy et al.
- Showed how to apply transformers directly to images

**Language Model Foundations**
- "Language Models are Few-Shot Learners" (GPT-3, 2020) - Brown et al.
- Demonstrated scaling laws and in-context learning
- "LLaMA: Open and Efficient Foundation Language Models" (2023) - Touvron et al.

**Contrastive Learning**
- "A Simple Framework for Contrastive Learning of Visual Representations" (SimCLR, 2020) - Chen et al.
- Core technique used in CLIP

**Self-Supervised Learning**
- "Momentum Contrast for Unsupervised Visual Representation Learning" (MoCo, 2020) - He et al.

**Instruction Tuning**
- "Finetuned Language Models Are Zero-Shot Learners" (FLAN, 2021) - Wei et al.
- Showed how instruction tuning improves generalization

## Vision-Language-Action Models (VLAs)

### Foundational VLA Papers

**RT-1 (2022)**
- "RT-1: Robotics Transformer for Real-World Control at Scale" by Brohan et al.
- First to show transformer-based policies work for real robot control at scale
- Trained on diverse robot manipulation tasks

**RT-2 (2023)**
- "RT-2: Vision-Language-Action Models Transfer Web Knowledge to Robotic Control" by Brohan et al.
- Co-fine-tuned VLMs (PaLI-X, PaLM-E) for robotic control
- Showed web-scale vision-language knowledge transfers to robotics

**PaLM-E (2023)**
- "PaLM-E: An Embodied Multimodal Language Model" by Driess et al.
- Integrated sensor modalities into large language models
- Demonstrated multi-embodiment and transfer across tasks

**OpenVLA (2024)**
- "OpenVLA: An Open-Source Vision-Language-Action Model" by Kim et al.
- Open-source 7B parameter VLA based on Prismatic VLMs
- Trained on Open X-Embodiment dataset

**Octo (2024)**
- "Octo: An Open-Source Generalist Robot Policy" by Team et al.
- Generalist robot policy trained on 800k+ trajectories
- Designed for fine-tuning to new robots and tasks

**RT-X (2023)**
- "Open X-Embodiment: Robotic Learning Datasets and RT-X Models" by Open X-Embodiment Collaboration
- Large-scale multi-robot dataset and models
- Demonstrated generalization across 22 robot embodiments

### Must-Read Prerequisites for VLAs

**All VLM prerequisites above**, plus:

**Imitation Learning**
- "A Reduction of Imitation Learning and Structured Prediction to No-Regret Online Learning" (DAgger, 2011) - Ross et al.
- "One-Shot Imitation Learning" (2017) - Duan et al.

**Behavioral Cloning**
- "End to End Learning for Self-Driving Cars" (2016) - Bojarski et al.
- Classic approach VLAs build upon

**Transformer for Sequential Decision Making**
- "Decision Transformer: Reinforcement Learning via Sequence Modeling" (2021) - Chen et al.
- Showed transformers can model policies as sequence modeling

**Offline RL**
- "Offline Reinforcement Learning: Tutorial, Review, and Perspectives on Open Problems" (2020) - Levine et al.

**Multi-Task Robot Learning**
- "Multi-Task Deep Reinforcement Learning with PopArt" (2018) - Hessel et al.
- "MT-Opt: Continuous Multi-Task Robotic Reinforcement Learning at Scale" (2021) - Kalashnikov et al.

**Large-Scale Robot Learning**
- "QT-Opt: Scalable Deep Reinforcement Learning for Vision-Based Robotic Manipulation" (2018) - Kalashnikov et al.

**Vision-Language for Robotics (Pre-VLA)**
- "CLIPort: What and Where Pathways for Robotic Manipulation" (2021) - Shridhar et al.
- Used CLIP for language-conditioned robot tasks

**Foundation Models for Control**
- "Do As I Can, Not As I Say: Grounding Language in Robotic Affordances" (SayCan, 2022) - Ahn et al.
- Combined LLMs with learned affordance functions

## Reading Path Recommendation

1. **Start with transformers and vision**: Transformer paper → ViT → CLIP
2. **Move to VLMs**: BLIP/BLIP-2 → LLaVA → Recent models (Gemini, GPT-4V papers)
3. **For VLAs, add robotics foundations**: Behavioral cloning basics → Decision Transformer
4. **Then VLA papers**: RT-1 → RT-2 → PaLM-E → OpenVLA/Octo

The field moves quickly, so papers from 2024-2025 may have emerged since my training data. Check recent conferences (CVPR, ICCV, NeurIPS, CoRL, ICRA) for the latest developments.
