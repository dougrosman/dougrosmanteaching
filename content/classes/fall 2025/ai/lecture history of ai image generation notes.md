---
title: Week 1 - 08/28/2025
draft: true
description: Introductions
---
## 2014

### Generative Adversarial Networks
![[Pasted image 20250909185437.png]]
**Original Paper:** [Generative Adversarial Networks](https://arxiv.org/abs/1406.2661) - Ian Goodfellow, June 10, 2014

**Model Diagram:**


**Abstract:** We propose a new framework for estimating generative models via an adversarial process, in which we simultaneously train two models: a **generative model G** that captures the data distribution, and a **discriminative model D** that estimates the probability that a sample came from the training data rather than G. The training procedure for G is to maximize the probability of D making a mistake. This framework corresponds to a minimax two-player game. In the space of arbitrary functions G and D, a unique solution exists, with G recovering the training data distribution and D equal to 1/2 everywhere. In the case where G and D are defined by multilayer perceptrons, the entire system can be trained with **backpropagation**. There is no need for any Markov chains or unrolled approximate inference networks during either training or generation of samples. Experiments demonstrate the potential of the framework through qualitative and quantitative evaluation of the generated samples.

**Summary:**

**Art Examples:**


**Further Reading:**
[What was the GAN? - Eryk Salvaggio](https://cyberneticforests.substack.com/p/what-was-the-gan)
# 2015: the spark

- **Generative Adversarial Networks** - [Original paper by Ian Goodfellow et al.](https://arxiv.org/abs/1406.2661)
	- find the earliest example
- **DeepDream** — gradient-ascent feature visualization turns into psychedelic art. [Google Research+1](https://research.google/blog/deepdream-a-code-example-for-visualizing-neural-networks/?utm_source=chatgpt.com)
	- ART EXAMPLE https://aiartists.org/alexander-mordvintsev
	- ART EXAMPLE https://aiartists.org/mike-tyka
- **Neural Style Transfer (Gatys et al.)** — separate “content” and “style” with CNN feature statistics; the first mainstream style-morphing. [arXiv](https://arxiv.org/abs/1508.06576?utm_source=chatgpt.com) 
	- ART EXAMPLE https://nwn.blogs.com/nwn/2021/02/stacey-abrams-nettrice-gasksins-ai-portrait.html
- **DCGAN** (late-2015) — CNNs make GAN training practical; births the modern GAN era. [arXiv](https://arxiv.org/abs/1503.03585?utm_source=chatgpt.com)
	- find the literal earliest example. like the first gan generated images
	- ART EXAMPLE: [A Book from the Sky - Gene Kogan](https://genekogan.com/works/a-book-from-the-sky/)
# 2016–2017: conditional + image-to-image

- **Text-to-image (early GANs)** — Reed et al. (GAN-CLS), **StackGAN/StackGAN++** stagewise refinement. [arXiv+1](https://arxiv.org/abs/2103.00020?utm_source=chatgpt.com)
	- [StackGAN](https://arxiv.org/abs/1612.03242)(Dec 10 2016)
	- [AttnGAN (Nov 28 2017)](https://arxiv.org/abs/1711.10485)
- **pix2pix** (paired I2I) & **CycleGAN** (unpaired I2I). These become the go-to for maps↔photos, edges↔objects, etc. [arXiv+1](https://arxiv.org/abs/1611.07004?utm_source=chatgpt.com)  
- **Inpainting**: Context Encoders (encoder–decoder + adversarial loss). [arXiv](https://arxiv.org/abs/1604.07379?utm_source=chatgpt.com)
- **Super-resolution**: **SRGAN** kicks off perceptual, adversarial SR; **ESRGAN** raises quality. [ResearchGate](https://www.researchgate.net/publication/320968363_Photo-Realistic_Single_Image_Super-Resolution_Using_a_Generative_Adversarial_Network?utm_source=chatgpt.com)[GitHub](https://github.com/xinntao/ESRGAN?utm_source=chatgpt.com)
# 2017–2019: scale & attention (GANs dominate)

- **Progressive Growing of GANs (PGGAN)** — grow resolution during training; big realism jump. [arXiv](https://arxiv.org/abs/1710.10196?utm_source=chatgpt.com)
- **BigGAN** — large-scale class-conditional GANs (ImageNet) with unprecedented fidelity. [arXiv](https://arxiv.org/abs/1809.11096?utm_source=chatgpt.com)
- **StyleGAN → StyleGAN2** — style-based synthesis; disentangled controls; then artifact fixes and quality boost. (StyleGAN3 lands in 2021 with alias-free convs.) [arXiv+1](https://arxiv.org/abs/1812.04948?utm_source=chatgpt.com)
	- only post the paper for stylegan 1, but include examples for the other 2
- **Semantic synthesis**: **SPADE/GauGAN** for segmentation-to-photo. [GitHub](https://github.com/NVIDIA/pix2pixHD?utm_source=chatgpt.com)[arXiv](https://arxiv.org/abs/1903.07291?utm_source=chatgpt.com)
	- **[GauGAN](https://blogs.nvidia.com/blog/gaugan-photorealistic-landscapes-nvidia-research/)**
- **VQ-VAE / VQ-VAE-2** — discrete image tokens; sets the stage for transformers & later VQGAN. [arXiv](https://arxiv.org/abs/2112.10752?utm_source=chatgpt.com)[Stability AI](https://stability.ai/news/celebrating-one-year-of-stable-diffusion?utm_source=chatgpt.com)

# 2020–early 2021: diffusion + discrete tokens + CLIP

- **DDPM (Ho et al., 2020)** & **score-based models** revive diffusion as top-tier likelihood models. [Google Colab](https://colab.research.google.com/github/justinjohn0306/VQGAN-CLIP/blob/main/VQGAN%2BCLIP%28Updated%29.ipynb?utm_source=chatgpt.com)
- **Image GPT (iGPT)** — autoregressive transformers on pixels; a bridge to DALL·E-style tokenization. [OpenAI](https://cdn.openai.com/papers/Generative_Pretraining_from_Pixels_V2.pdf?utm_source=chatgpt.com)
- **CLIP (2021)** — joint vision-language embedding that soon “steers” generation. [arXiv](https://arxiv.org/abs/2204.06125?utm_source=chatgpt.com)
- **DALL·E (2021)** — text→image with discrete VAE tokens + autoregressive transformer. [arXiv](https://arxiv.org/abs/2302.05543?utm_source=chatgpt.com)  
    _Play-adjacent:_ open replica **Craiyon (DALL·E mini)** on HF/hosted. [GitHub](https://github.com/borisdayma/dalle-mini?utm_source=chatgpt.com)[Hugging Face](https://huggingface.co/spaces/dalle-mini/dalle-mini?utm_source=chatgpt.com)
- **VQGAN+Transformer** (aka **VQGAN**) — codebook + autoregressive modeling; the VQGAN+CLIP “summer” follows with wildly popular notebooks. [Imagen](https://imagen.research.google/?utm_source=chatgpt.com)  
# Late 2021–2022: text-to-image goes mainstream (diffusion)

- **GLIDE** — text-guided diffusion for generation _and_ editing; introduces classifier-free guidance comparisons. [arXiv](https://arxiv.org/abs/2112.10741?utm_source=chatgpt.com)  
- **Classifier-Free Guidance** — simple conditional/unconditional trick that becomes ubiquitous. [João Rafael M](https://joaorafaelm.github.io/notebook/vqgan/clip/2021/08/14/vqgan-and-clip.html?utm_source=chatgpt.com)
- **Latent Diffusion (LDM)** — run diffusion in an autoencoder’s latent space → efficient high-res. Powers… **Stable Diffusion**. [GitHub](https://github.com/deep-floyd/IF?utm_source=chatgpt.com)
    
- **Stable Diffusion (2022)** — open, extensible T2I model; community explodes (web UIs, nodes, checkpoints). [arXiv](https://arxiv.org/abs/2307.01952?utm_source=chatgpt.com)  
    
    
- **DALL·E 2**, **Imagen**, **Parti**, **eDiff-I** — closed/proprietary showcases of photorealism and scaling. (Great for benchmarks/history.) [arXiv](https://arxiv.org/abs/1807.03039?utm_source=chatgpt.com)[Stability AI](https://stability.ai/news/stable-diffusion-3?utm_source=chatgpt.com)[Wikipedia](https://en.wikipedia.org/wiki/Flux_%28text-to-image_model%29?utm_source=chatgpt.com)
    
- **Personalization & editing**: **Textual Inversion**, **DreamBooth** make per-concept fine-tuning accessible. [arXiv](https://arxiv.org/abs/2012.09841?utm_source=chatgpt.com)[NeurIPS Papers](https://papers.nips.cc/paper/9625-generating-diverse-high-fidelity-images-with-vq-vae-2?utm_source=chatgpt.com)  
    
    
- **Community notebooks**: **Disco Diffusion** popularizes CLIP-guided diffusion art (and animation). [Google Colab](https://colab.research.google.com/github/alembics/disco-diffusion/blob/main/Disco_Diffusion.ipynb?utm_source=chatgpt.com)
    

# 2023: control & bigger backbones

- **ControlNet** — add pose/edges/depth/etc. as structural control to SD; huge leap in reproducibility for artists. [arXiv](https://arxiv.org/abs/1604.07379?utm_source=chatgpt.com)  
    
    
- **SDXL** — new SD architecture + larger latent space; better composition/typography and photorealism. [GitHub](https://github.com/NVIDIA/pix2pixHD?utm_source=chatgpt.com)
    
- **Restoration companions** remain staples: **Real-ESRGAN**, **GFPGAN** for upscaling/face fix. [CVF Open Access+1](https://openaccess.thecvf.com/content/ICCV2021W/AIM/papers/Wang_Real-ESRGAN_Training_Real-World_Blind_Super-Resolution_With_Pure_Synthetic_Data_ICCVW_2021_paper.pdf?utm_source=chatgpt.com)
    

# 2024–2025: new families & refreshed SD

- **Stable Diffusion 3** (multi-token attention; improved long-prompt handling; released 2024). [arXiv](https://arxiv.org/abs/1903.07291?utm_source=chatgpt.com)
    
- **FLUX (Black Forest Labs)** — high-quality open models/weights; fast community uptake in 2024.