# Quantization-Adjusted Scaling Law Pareto Frontiers: Investigating Inference-Optimal Scaling Laws for Neural Language Models

**Claim Statement**  
The compute-optimal allocation of model parameters and pretraining tokens as determined by Hoffmann et al. [1] changes when the resulting models are deployed under constrained inference memory budgets with low-precision quantization.  

**Core Hypothesis**  
Post-training quantization changes the relative performance of language models with different parameter-to-token ratios [2]. Consequently, the Hoffmann et al. [1] compute-optimal pretraining configuration may differ from the inference-optimal configuration under constrained deployment memory.

**Methodology**  
Using EleutherAI's Pythia model family suite on Hugging Face, I will investigate the relationship between model size *N*, pretraining data exposure *D*, and quantization precision *b* through two complementary experimental designs:  
  1. **Axis 1** – Fixed Pretraining Compute: Construct approximately isoFLOP configurations using ≈ 6*ND*. Compare model performance at FP16, INT8, and INT4 to investigate whether quantization changes the relative ranking of compute-equivalent configurations.  
  2. **Axis 2** – Fixed Inference Memory: Evaluate candidate configurations under predefined VRAM budgets (e.g. 2 GB, 4 GB and 8 GB). Measure predictive performance and actual inference-memory consumption to construct deployment-optimal Pareto frontiers.

**Experimental Grid**

| Dimension            | Values                                        |
| -------------------- | --------------------------------------------- |
| Model sizes          | 70M, 160M, 410M, 1B, 2.8B                     |
| Training checkpoints | 1K, 10K, 50K, 143K steps                      |
| Precision            | FP16, INT8, INT4                              |
| Evaluation           | Cross-entropy, perplexity, zero-shot accuracy |
| Deployment           | Peak VRAM and inference latency               |

**References**  
[1] J. Hoffmann et al., "Training compute-optimal large language models," in *Proc. 36th Conf. Neural Inf. Process. Syst.*, New Orleans, LA, USA, Nov. 28–Dec. 9, 2022, pp. 30016–30030.  
[2]  T. Kumar et al., "Scaling Laws for Precision," 2024, *arXiv:2411.04330v2*.

**Contributor**  
Nosa Omoregie (no239@njit.edu)

 