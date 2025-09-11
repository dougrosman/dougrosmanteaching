---
title: Assignment 2 - Inpainting
draft: false
description: Introductions
---
Notes for Beck
[AIartists.org](https://aiartists.org/ai-artist-founding-members)

**Things for each entry:**
1. 1-2 images from the original paper
2. 1-2 art examples (if you can find any)
3. image of the model diagram
4. link to the original paper with primary author
5. date the paper was published
6. quick summary of the model (you can ask AI for this)

gan-2014-paper-image1

## 2014

### Generative Adversarial Networks
![[GAN-Image-Distribution-1.png]]
**Original Paper:** [Generative Adversarial Networks](https://arxiv.org/abs/1406.2661) - Ian Goodfellow, June 10, 2014
**Model Diagram:**
![[Gan-Model-Architecture-1.png]]

**Abstract:** We propose a new framework for estimating generative models via an adversarial process, in which we simultaneously train two models: a **generative model G** that captures the data distribution, and a **discriminative model D** that estimates the probability that a sample came from the training data rather than G. The training procedure for G is to maximize the probability of D making a mistake. This framework corresponds to a minimax two-player game. In the space of arbitrary functions G and D, a unique solution exists, with G recovering the training data distribution and D equal to 1/2 everywhere. In the case where G and D are defined by multilayer perceptrons, the entire system can be trained with **backpropagation**. There is no need for any Markov chains or unrolled approximate inference networks during either training or generation of samples. Experiments demonstrate the potential of the framework through qualitative and quantitative evaluation of the generated samples.

**Summary:**
Trains a generator and a discriminator in opposition (minimax), until the generator can sample images that fool the critic. Enables fast “one-shot” sampling from noise, but training is fragile (instability, mode collapse), motivating many successors.

**Art Examples:**







**Further Reading:**
[What was the GAN? - Eryk Salvaggio](https://cyberneticforests.substack.com/p/what-was-the-gan)



# 2015

### Deep Dream
![[DeepDream-Image-Influence.jpg]]
**Original Paper:** [Original Google Blog Post](https://research.google/blog/inceptionism-going-deeper-into-neural-networks/)- Alexander Mordvintsev, June 18, 2015

**Model Diagram:**
![[DeepDream-Model-Architecture-1.png]]


**Summary:**
A feature-visualization technique that amplifies a classifier’s internal activations via gradient ascent on the input. It is not a learned generative model of a dataset; its outputs are diagnostic, hallucinatory patterns revealing what a trained CNN “sees.”

**Art Examples:**

![[Alexander-Mordvintsev-Father-Cat-2015.jpg]]
Alexander Mordvintsev, *Father Cat*, 2015


![[Mike-Tyka-hamidmansoor123-2017-1.jpg]]
Mike Tyka, *hamidmansoor123*, 2017



### Neural Style Transfer
![[Neural-Style-Transfer-Examples-1.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/pdf/1508.06576) - Leon A. Gatys, August 26, 2015

**Model Diagram:**![[Neural-Transfer-Model-Architecture-1.jpg]]

**Summary:**
Per-image optimization that matches content features of one image and Gram-matrix “style” statistics of another. Unlike dataset-trained generators, it does not learn a distribution; it’s a controllable, instance-wise synthesis method yielding painterly texture transfer.

**Art Examples:**
![[Nettrice-Gaskins-Stacey-Abrams-1.jpg]]
Nettrice Gaskins, *Stacey Abrams*, 2021

### DCGAN
![[DCGAN-Equation.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/abs/1511.06434) - Alec Radford, November 19, 2015

**Model Diagram:
![[DCGAN-Model-Architecture-1.jpg]]
**Summary:**
Introduces a stable convolutional architecture and training heuristics for GANs (e.g., strided convs, batch norm, ReLU/LeakyReLU). It markedly improves fidelity and training stability over vanilla GANs, enabling practical low-to-mid-resolution synthesis.

**Art Examples:**
![[Gene-Kogan-A-Book-From-The-Sky-2015-1.jpg]]
Gene Kogan, *A Book From The Sky*, 2015

# 2016

### Context Encoders - Inpainting
![[Context-Encoders-Examples-1.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/abs/1604.07379) - Deepak Pathak, April 26, 2016

**Model Diagram:
![[Context-Encoders-Model-Architecture-1.jpg]]
**Summary:**
An encoder–decoder with adversarial and reconstruction losses to fill missing regions from surrounding context. It initiates modern learned inpainting, emphasizing global plausibility with early limits on fine detail.






### Text-To-Image 
![[TTI-GAN-Zero-Shot-Generation-1.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/pdf/1605.05396) - Scott Reed, May 17, 2016

**Model Diagram:
![[TTI-GAN- Model-Architecture-1.jpg]]
**Summary:**
Conditions GAN generation on sentence embeddings to align images with captions. It inaugurates text conditioning but with limited resolution and loose fine-grained correspondence relative to later attention-based and diffusion models.






### SRGAN

![[SRGAN-Example-1.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/abs/1609.04802) - Christian Ledig, September 15, 2016

**Model Diagram:![[SRGAN-Model-Architecture-1.jpg]]

**Summary:**
Adds perceptual and adversarial losses to prioritize photo-realistic textures over pixelwise fidelity. It differs from PSNR-oriented methods by intentionally favoring perceptual realism.




### Pix2Pix
![[Pix2Pix-Examples-1.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/abs/1611.07004) - Phillip Isola, November 26, 2016

**Model Diagram:![[Pix2Pix-Model-Architecture-1.jpg]]

**Summary:**
A conditional GAN trained on paired data to learn direct mappings (e.g., edges→photo). Because it requires aligned pairs, it delivers precise, controllable translations unmatched by unpaired methods.







# 2017


### STACKGAN
![[STACKGAN-TTIGAN-Comparison-1.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/abs/1612.03242) - Han Zhang August 5, 2017

**Model Diagram:
![[STACKGAN-Model-Architecture-1.jpg]]
**Summary:**
Two-stage, coarse-to-fine GANs that first synthesize low-resolution images then refine to high resolution. The staged design improves sharpness and global structure compared with single-shot generators.






### PGGAN
![[PGGAN-Example-1.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/abs/1710.10196) - Tero Karras, October 27, 2017

**Model Diagram:![[PGGAN-Model-Archoitecture-1.jpg]]

**Summary:**
Trains by gradually increasing image resolution and network depth, stabilizing high-resolution synthesis. This curriculum enables the first consistently detailed, large-format GAN outputs.





### VQ-VAE
![[VQVAE-Comparison-1.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/abs/1711.00937) - Aaron van den Oord, November 2, 2017

**Model Diagram:![[VQVAE-Model-Architecture-1.jpg]]

**Summary:**
Discretizes latents via a learned codebook, enabling images to be represented as sequences of tokens. Unlike GANs, it emphasizes reconstruction through quantized latents, paving the way for token-based transformers.





# 2018


### BigGAN 
![[BigGAN-Examples-1.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/abs/1809.11096) - Andrew Brock, September 28, 2018

**Model Diagram:
![[BigGAN-Model-Architecture-1.png]]
**Summary:**
Scales class-conditional GANs on ImageNet with strong regularization and large batch sizes for unprecedented fidelity and diversity. Its label conditioning and scale distinguish it from unconditional, smaller-scale predecessors.




### StyleGAN 1/2/3
![[StyleGAN-Example-1.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/abs/1812.04948) - Tero Karras, December 12, 2018

**Model Diagram:
![[StyleGAN-Model-Architecture-1.png]]
**Summary:**
Introduces a style-based generator where latent “styles” modulate features at each layer, promoting disentanglement and fine control. This architectural shift separates coarse pose/structure from fine texture more effectively than prior GANs.




# 2019

### SPADE - GauGAN
![[SPADE-GauGAN-Example-1.jpg]]
**Original Paper:** [Original Paper](https://arxiv.org/abs/1903.07291) - Taesung Park, March 18, 2019

**Model Diagram:
![[SPADE-GauGAN-Model-Arechitecture.jpg]]
**Summary:**
Uses spatially adaptive normalization to inject semantic layouts (segmentation maps) directly into the generator. It excels at scene synthesis “from a map,” differing from text- or noise-conditioned GANs by enforcing explicit structure.













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