<div align="center">

# 🌐 Awesome Generative Reconstruction

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Updated](https://img.shields.io/badge/updated-September%202026-6c5ce7.svg)](#-news--updates)
[![Star this repo](https://img.shields.io/badge/%E2%AD%90-Star_this_repo-yellow.svg)](https://github.com/yihangtao/Awesome-Generative-Reconstruction)

**📜 A curated list of research that unifies generation and reconstruction for spatially consistent worlds.**<br>
*From camera-controlled implicit worlds to explicit 3D reconstruction and space-time simulation.*

<p align="center">
  <img src="assets/hero.png" alt="Sparse observations becoming a generated and reconstructed 3D world" width="100%">
</p>

*Cover generated for this collection with OpenAI ImageGen.*

</div>

---

## 🚩 News & Updates

🔥 **[2026-09-09] Atlas-aligned taxonomy** — Reorganized the collection around four primary capabilities: **Camera-Controlled Generation**, **Spatial Reconstruction**, **Space-Time Simulation**, and **Image Generation**.

🎉 **[2026-09-02] Initial release** — Launched the repository with a screened local Zotero collection and a curated bibliography of generative reconstruction.

💡 **[Ongoing] Community Contributions Welcome** — Found a missing paper, project page, code release, or incorrect venue? Please open an issue or submit a pull request. See [CONTRIBUTING.md](CONTRIBUTING.md) for the entry format.

⭐ **[Ongoing] Support This Project** — If this collection is useful, please [star the repository](https://github.com/yihangtao/Awesome-Generative-Reconstruction) and share it with the community.

---

## Overview

- [Aim of the Project](#aim-of-the-project)
- [Definition and Scope](#definition-and-scope)
- [Atlas-Inspired Taxonomy](#atlas-inspired-taxonomy)
- [Camera-Controlled Generation](#-camera-controlled-generation-implicit-3d-modeling)
- [Spatial Reconstruction](#-spatial-reconstruction-explicit-3d-modeling)
- [Space-Time Simulation](#-space-time-simulation-dynamic-4d-modeling)
- [Image Generation](#-image-generation-spatially-grounded-2d-generation)
- [Foundations, Data, and Evaluation](#foundations-data-and-evaluation)
- [Contributing](#contributing)

## Aim of the Project

Generative reconstruction lies at the intersection of generative models, novel-view synthesis, 3D/4D reconstruction, and world modeling. It asks a model to preserve what has been observed, infer a coherent spatial structure, and plausibly generate what cameras have not seen. This repository tracks methods in which **generation and geometric reasoning are coupled**, rather than treating video generation and reconstruction as unrelated steps.

Our scope is scene- and world-centric. We include methods that primarily output camera-controlled images or videos when a persistent implicit 3D state, a geometry foundation model, an explicit reconstruction, or a 3D-aware training signal materially shapes generation. We also include methods that primarily output explicit 3D/4D assets when generative priors complete, repair, or directly model the scene.

## Definition and Scope

We use **generative reconstruction** as an umbrella term for models that jointly address four requirements:

1. **Observation fidelity** — outputs remain compatible with the available images, videos, text, or partial geometry.
2. **Generative completion** — unseen or weakly observed regions are synthesized rather than left empty.
3. **Spatial consistency** — views correspond to a coherent 3D or 4D world, represented explicitly or implicitly.
4. **Model-level coupling** — geometry affects generation through conditioning, memory, denoising, supervision, optimization, or a shared representation.

Pure text-to-video generation, conventional dense-view reconstruction, and standalone depth or pose estimation are outside the core list. Important backbones and geometry foundations are retained in [Foundations, Data, and Evaluation](#foundations-data-and-evaluation).

### Badge legend

- **Venue** badges are included only when an official conference or proceedings page is available.
- **arXiv** links point to the primary manuscript.
- **Website** and **Code** badges point to official project pages and author repositories.
- ⭐️ marks a representative or field-shaping work in its category. It is not a ranking.

## Atlas-Inspired Taxonomy

The organization follows the four capabilities used in the [Atlas technical overview](https://www.worldlabs.ai/blog/atlas). We apply a **primary-output rule** so that each paper appears in one main category rather than being duplicated across several pipeline stages.

| Category | Primary output | Role of 3D |
|---|---|---|
| Camera-Controlled Generation | Novel-view images or videos along a requested camera path | Implicit scene state, geometry condition, spatial memory, or reconstruction-guided generation |
| Spatial Reconstruction | Point cloud, NeRF, mesh, 3D Gaussian Splatting, or another explicit 3D asset | Geometry is the final persistent representation |
| Space-Time Simulation | Controllable dynamic views, 4D worlds, or real-to-sim environments | Geometry and time are modeled jointly |
| Image Generation | Individual views, view sets, or panoramas | Camera- and geometry-aware image synthesis without requiring an explicit final scene asset |

> **Omni-system spotlight — [Atlas: A World Model for Spatial Intelligence](https://www.worldlabs.ai/blog/atlas).** Atlas spans all four categories through a multimodal autoregressive diffusion transformer with shared spatial context. It accepts text, images, camera poses, and depth, and demonstrates camera-controlled video, explicit point-cloud/3DGS reconstruction, space-time simulation, and image generation. As of September 2026, detailed training resources, code, weights, and unrestricted public evaluation access have not been released.

## 🎥 Camera-Controlled Generation (Implicit 3D Modeling)

These methods primarily generate novel-view images or videos along specified camera trajectories. Their world is represented implicitly through geometry features, spatial memory, pose-aligned context, or a reconstruction model used inside the generation process.

### Geometry-conditioned video and novel-view generation

- [⭐️] **Lyra 2.0**, "Lyra 2.0: Explorable Generative 3D Worlds". [![arXiv](https://img.shields.io/badge/arXiv-2604.13036-b31b1b.svg)](https://arxiv.org/abs/2604.13036) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/sil/lyra2/)
- [⭐️] **RoGe**, "Novel View Synthesis via End-to-End Implicit Reconstruction and Generation". [![arXiv](https://img.shields.io/badge/arXiv-2609.02847-b31b1b.svg)](https://arxiv.org/abs/2609.02847) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://roge.github.io/)
- [⭐️] **WorldStereo**, "Bridging Camera-Guided Video Generation and Scene Reconstruction via 3D Geometric Memories". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Zhang_WorldStereo_Bridging_Camera-Guided_Video_Generation_and_Scene_Reconstruction_via_3D_CVPR_2026_paper.html)
- **CineScene**, "Implicit 3D as Effective Scene Representation for Cinematic Video Generation". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://karine-huang.github.io/CineScene/) [![arXiv](https://img.shields.io/badge/arXiv-2602.06959-b31b1b.svg)](https://arxiv.org/abs/2602.06959) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://karine-huang.github.io/CineScene/)
- **Geometry Forcing**, "Marrying Video Diffusion and 3D Representation for Consistent World Modeling". [![ICLR 2026](https://img.shields.io/badge/ICLR-2026-6f42c1.svg)](https://arxiv.org/abs/2507.07982) [![arXiv](https://img.shields.io/badge/arXiv-2507.07982-b31b1b.svg)](https://arxiv.org/abs/2507.07982)
- **PE-Field 4D**, "Video Generation Models as Canvas". [![SIGGRAPH Asia 2026](https://img.shields.io/badge/SIGGRAPH_Asia-2026-6f42c1.svg)](https://arxiv.org/abs/2607.15667) [![arXiv](https://img.shields.io/badge/arXiv-2607.15667-b31b1b.svg)](https://arxiv.org/abs/2607.15667) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/MTLab/PE-Field)
- **MVSplat360**, "Feed-Forward 360 Scene Synthesis from Sparse Views". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://arxiv.org/abs/2411.04924) [![arXiv](https://img.shields.io/badge/arXiv-2411.04924-b31b1b.svg)](https://arxiv.org/abs/2411.04924) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://donydchen.github.io/mvsplat360/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/donydchen/mvsplat)
- **ViewCrafter**, "Taming Video Diffusion Models for High-fidelity Novel View Synthesis". [![arXiv](https://img.shields.io/badge/arXiv-2409.02048-b31b1b.svg)](https://arxiv.org/abs/2409.02048) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://drexubery.github.io/ViewCrafter/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Drexubery/ViewCrafter)
- **Stable Virtual Camera**, "Generative View Synthesis with 3D Camera Control". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://arxiv.org/abs/2503.14489) [![arXiv](https://img.shields.io/badge/arXiv-2503.14489-b31b1b.svg)](https://arxiv.org/abs/2503.14489) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://stable-virtual-camera.github.io/)
- **Orbital Video Generation**, "Towards Realistic and Consistent Orbital Video Generation via 3D Foundation Priors". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://arxiv.org/abs/2604.12309) [![arXiv](https://img.shields.io/badge/arXiv-2604.12309-b31b1b.svg)](https://arxiv.org/abs/2604.12309)
- **MV-Forcing**, "Long Multi-View Video Generation via 4D-Grounded Spatio-Temporal Self-Forcing". [![arXiv](https://img.shields.io/badge/arXiv-2607.05376-b31b1b.svg)](https://arxiv.org/abs/2607.05376) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://galfiebelman.github.io/mv-forcing/)
- **VGGRPO**, "Towards World-Consistent Video Generation with 4D Latent Reward". [![arXiv](https://img.shields.io/badge/arXiv-2603.26599-b31b1b.svg)](https://arxiv.org/abs/2603.26599) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://zhaochongan.github.io/projects/VGGRPO/)

### Spatial memory and long-horizon generation

- [⭐️] **VMem**, "Consistent Interactive Video Scene Generation with Surfel-Indexed View Memory". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://v-mem.github.io/) [![arXiv](https://img.shields.io/badge/arXiv-2506.18903-b31b1b.svg)](https://arxiv.org/abs/2506.18903) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://v-mem.github.io/)
- **Context as Memory**, "Scene-Consistent Interactive Long Video Generation with Memory Retrieval". [![SIGGRAPH Asia 2025](https://img.shields.io/badge/SIGGRAPH_Asia-2025-6f42c1.svg)](https://context-as-memory.github.io/) [![arXiv](https://img.shields.io/badge/arXiv-2506.03141-b31b1b.svg)](https://arxiv.org/abs/2506.03141) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://context-as-memory.github.io/)
- **Spatial Memory**, "Video World Models with Long-term Spatial Memory". [![arXiv](https://img.shields.io/badge/arXiv-2506.05284-b31b1b.svg)](https://arxiv.org/abs/2506.05284) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://spmem.github.io/)
- **CausNVS**, "Causal Novel View Synthesis for Real-Time World Modeling". [![Website](https://img.shields.io/badge/Website-Link-blue)](https://kxhit.github.io/CausNVS.html)

## 🏗️ Spatial Reconstruction (Explicit 3D Modeling)

These methods primarily produce a persistent explicit asset such as a NeRF, mesh, point cloud, or 3D Gaussian scene. The generative model supplies missing observations, repairs unreliable renderings, distills prior knowledge, or directly predicts the 3D representation.

### Native and unified 3D generation–reconstruction

- [⭐️] **Lyra**, "Generative 3D Scene Reconstruction via Video Diffusion Model Self-Distillation". [![ICLR 2026](https://img.shields.io/badge/ICLR-2026-6f42c1.svg)](https://research.nvidia.com/labs/toronto-ai/lyra/) [![arXiv](https://img.shields.io/badge/arXiv-2509.19296-b31b1b.svg)](https://arxiv.org/abs/2509.19296) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/toronto-ai/lyra/)
- [⭐️] **FlashWorld**, "High-quality 3D Scene Generation within Seconds". [![ICLR 2026](https://img.shields.io/badge/ICLR-2026-6f42c1.svg)](https://arxiv.org/abs/2510.13678) [![arXiv](https://img.shields.io/badge/arXiv-2510.13678-b31b1b.svg)](https://arxiv.org/abs/2510.13678) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/imlixinyang/FlashWorld)
- **Free-Range Gaussians**, "Non-Grid-Aligned Generative 3D Gaussian Reconstruction". [![ECCV 2026](https://img.shields.io/badge/ECCV-2026-6f42c1.svg)](https://arxiv.org/abs/2604.04874) [![arXiv](https://img.shields.io/badge/arXiv-2604.04874-b31b1b.svg)](https://arxiv.org/abs/2604.04874) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://free-range-gaussians.github.io/)
- **Gen3R**, "3D Scene Generation Meets Feed-Forward Reconstruction". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://arxiv.org/abs/2601.04090) [![arXiv](https://img.shields.io/badge/arXiv-2601.04090-b31b1b.svg)](https://arxiv.org/abs/2601.04090) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://xdimlab.github.io/Gen3R/)
- **PixWorld**, "Unifying 3D Scene Generation and Reconstruction in Pixel Space". [![arXiv](https://img.shields.io/badge/arXiv-2607.05373-b31b1b.svg)](https://arxiv.org/abs/2607.05373) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://sensengao.github.io/PixWorld/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/SensenGao/PixWorld)
- **SPAR3S**, "Sparse Auto-Regressive Modeling for Scene Generation from Multi-View Images". [![arXiv](https://img.shields.io/badge/arXiv-2609.03931-b31b1b.svg)](https://arxiv.org/abs/2609.03931)
- **Generative Gaussian Splatting**, "Generating 3D Scenes with Video Diffusion Priors". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/ICCV2025/html/Schwarz_Generative_Gaussian_Splatting_Generating_3D_Scenes_with_Video_Diffusion_Priors_ICCV_2025_paper.html)
- **DMV3D**, "Denoising Multi-View Diffusion using 3D Large Reconstruction Model". [![ICLR 2024](https://img.shields.io/badge/ICLR-2024-6f42c1.svg)](https://arxiv.org/abs/2311.09217) [![arXiv](https://img.shields.io/badge/arXiv-2311.09217-b31b1b.svg)](https://arxiv.org/abs/2311.09217) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://justimyhxu.github.io/projects/dmv3d/)
- **DreamFusion**, "Text-to-3D using 2D Diffusion". [![ICLR 2023](https://img.shields.io/badge/ICLR-2023-6f42c1.svg)](https://arxiv.org/abs/2209.14988) [![arXiv](https://img.shields.io/badge/arXiv-2209.14988-b31b1b.svg)](https://arxiv.org/abs/2209.14988) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://dreamfusion3d.github.io/)

### Generate views first, then reconstruct

- [⭐️] **CAT3D**, "Create Anything in 3D with Multi-View Diffusion Models". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://arxiv.org/abs/2405.10314) [![arXiv](https://img.shields.io/badge/arXiv-2405.10314-b31b1b.svg)](https://arxiv.org/abs/2405.10314) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://cat3d.github.io/)
- **HY-World 2.0**, "A Multi-Modal World Model for Reconstructing, Generating, and Simulating 3D Worlds". [![arXiv](https://img.shields.io/badge/arXiv-2604.14268-b31b1b.svg)](https://arxiv.org/abs/2604.14268) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Tencent-Hunyuan/HY-World-2.0)
- **Matrix-3D**, "Omnidirectional Explorable 3D World Generation". [![arXiv](https://img.shields.io/badge/arXiv-2508.08086-b31b1b.svg)](https://arxiv.org/abs/2508.08086) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://matrix-3d.github.io/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/SkyworkAI/Matrix-3D)
- **WorldExplorer**, "Towards Generating Fully Navigable 3D Scenes". [![SIGGRAPH Asia 2025](https://img.shields.io/badge/SIGGRAPH_Asia-2025-6f42c1.svg)](https://arxiv.org/abs/2506.01799) [![arXiv](https://img.shields.io/badge/arXiv-2506.01799-b31b1b.svg)](https://arxiv.org/abs/2506.01799) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://mschneider456.github.io/world-explorer/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/mschneider456/WorldExplorer)
- **Scene Splatter**, "Momentum 3D Scene Generation from Single Image with Video Diffusion Model". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Zhang_Scene_Splatter_Momentum_3D_Scene_Generation_from_Single_Image_with_CVPR_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2504.02764-b31b1b.svg)](https://arxiv.org/abs/2504.02764)
- **ReconX**, "Reconstruct Any Scene from Sparse Views with Video Diffusion Model". [![arXiv](https://img.shields.io/badge/arXiv-2408.16767-b31b1b.svg)](https://arxiv.org/abs/2408.16767)
- **Text2Room**, "Extracting Textured 3D Meshes from 2D Text-to-Image Models". [![ICCV 2023](https://img.shields.io/badge/ICCV-2023-6f42c1.svg)](https://arxiv.org/abs/2303.11989) [![arXiv](https://img.shields.io/badge/arXiv-2303.11989-b31b1b.svg)](https://arxiv.org/abs/2303.11989) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://lukas-hoellein.github.io/text2room/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/lukasHoel/text2room)
- **WorldGen**, "From Text to Traversable and Interactive 3D Worlds". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Wang_WorldGen_From_Text_to_Traversable_and_Interactive_3D_Worlds_CVPR_2026_paper.html)

### Reconstruction–generation loops and repair

- [⭐️] **GenFusion**, "Closing the Loop between Reconstruction and Generation via Videos". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2503.21219) [![arXiv](https://img.shields.io/badge/arXiv-2503.21219-b31b1b.svg)](https://arxiv.org/abs/2503.21219) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Inception3D/GenFusion)
- **Geometry-as-Context**, "Modulating Explicit 3D in Scene-Consistent Video Generation to Geometry Context". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Hu_Geometry-as-context_Modulating_Explicit_3D_in_Scene-consistent_Video_Generation_to_Geometry_CVPR_2026_paper.html)
- **GaussFusion**, "Improving 3D Reconstruction in the Wild with a Geometry-Informed Video Generator". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Zhu_GaussFusion_Improving_3D_Reconstruction_in_the_Wild_with_A_Geometry-Informed_CVPR_2026_paper.html)
- **Scene-Grounding Guidance**, "Taming Video Diffusion Prior with Scene-Grounding Guidance for 3D Gaussian Splatting from Sparse Inputs". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2503.05082) [![arXiv](https://img.shields.io/badge/arXiv-2503.05082-b31b1b.svg)](https://arxiv.org/abs/2503.05082)
- **Generative Sparse-View Gaussian Splatting**, "Generative Sparse-View Gaussian Splatting". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Kong_Generative_Sparse-View_Gaussian_Splatting_CVPR_2025_paper.html)
- **ReconFusion**, "3D Reconstruction with Diffusion Priors". [![CVPR 2024](https://img.shields.io/badge/CVPR-2024-6f42c1.svg)](https://arxiv.org/abs/2312.02981) [![arXiv](https://img.shields.io/badge/arXiv-2312.02981-b31b1b.svg)](https://arxiv.org/abs/2312.02981) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://reconfusion.github.io/)
- **FaithFusion**, "Harmonizing Reconstruction and Generation via Pixel-wise Information Gain". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://arxiv.org/abs/2511.21113) [![arXiv](https://img.shields.io/badge/arXiv-2511.21113-b31b1b.svg)](https://arxiv.org/abs/2511.21113) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/wangyuanbiubiubiu/FaithFusion)
- **VidSplat**, "Gaussian Splatting Reconstruction with Geometry-Guided Video Diffusion Priors". [![arXiv](https://img.shields.io/badge/arXiv-2605.11424-b31b1b.svg)](https://arxiv.org/abs/2605.11424)
- **Sparse-to-Complete**, "From Sparse Image Captures to Complete 3D Scenes". [![arXiv](https://img.shields.io/badge/arXiv-2605.05664-b31b1b.svg)](https://arxiv.org/abs/2605.05664) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://gapszju.github.io/S2C-3D/)
- **Few Glimpses**, "Novel View Synthesis from A Few Glimpses via Test-Time Natural Video Completion". [![arXiv](https://img.shields.io/badge/arXiv-2511.17932-b31b1b.svg)](https://arxiv.org/abs/2511.17932)
- **Difix3D+**, "Improving 3D Reconstructions with Single-Step Diffusion Models". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2503.01774) [![arXiv](https://img.shields.io/badge/arXiv-2503.01774-b31b1b.svg)](https://arxiv.org/abs/2503.01774) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/toronto-ai/difix3d/)
- **GSFixer**, "Improving 3D Gaussian Splatting with Reference-Guided Video Diffusion Priors". [![arXiv](https://img.shields.io/badge/arXiv-2508.09667-b31b1b.svg)](https://arxiv.org/abs/2508.09667) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/GVCLab/GSFixer)
- **ArtiFixer**, "Enhancing and Extending 3D Reconstruction with Auto-Regressive Diffusion Models". [![arXiv](https://img.shields.io/badge/arXiv-2603.00492-b31b1b.svg)](https://arxiv.org/abs/2603.00492) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/sil/projects/artifixer)
- **GaussVid**, "Sparse-View Gaussian Splatting with 3D-Aware Video Diffusion Priors". [![arXiv](https://img.shields.io/badge/arXiv-2608.21849-b31b1b.svg)](https://arxiv.org/abs/2608.21849) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Xinhui-99/GaussVid)
- **FixAnything**, "3D-Consistent Rendering Refinement via Video Generative Priors". [![arXiv](https://img.shields.io/badge/arXiv-2608.23549-b31b1b.svg)](https://arxiv.org/abs/2608.23549)

## ⏱️ Space-Time Simulation (Dynamic 4D Modeling)

These works model both viewpoint and temporal evolution. The primary deliverable is a controllable dynamic world, a 4D representation, or a real-to-sim environment rather than a static scene or a single camera path.

- [⭐️] **CAT4D**, "Create Anything in 4D with Multi-View Video Diffusion Models". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2411.18613) [![arXiv](https://img.shields.io/badge/arXiv-2411.18613-b31b1b.svg)](https://arxiv.org/abs/2411.18613) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://cat-4d.github.io/)
- [⭐️] **WorldReel**, "4D Video Generation with Consistent Geometry and Motion Modeling". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Fang_WorldReel_4D_Video_Generation_with_Consistent_Geometry_and_Motion_Modeling_CVPR_2026_paper.html)
- **DimensionX**, "Create Any 3D and 4D Scenes from a Single Image with Decoupled Video Diffusion". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://arxiv.org/abs/2411.04928) [![arXiv](https://img.shields.io/badge/arXiv-2411.04928-b31b1b.svg)](https://arxiv.org/abs/2411.04928) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://chenshuo20.github.io/DimensionX/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/wenqsun/DimensionX)
- **DreamDrive**, "Generative 4D Scene Modeling from Street View Images". [![ICRA 2025](https://img.shields.io/badge/ICRA-2025-6f42c1.svg)](https://arxiv.org/abs/2501.00601) [![arXiv](https://img.shields.io/badge/arXiv-2501.00601-b31b1b.svg)](https://arxiv.org/abs/2501.00601) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/NVlabs/DreamDrive)
- **ViDAR**, "Video Diffusion-Aware 4D Reconstruction From Monocular Inputs". [![NeurIPS 2025](https://img.shields.io/badge/NeurIPS-2025-6f42c1.svg)](https://arxiv.org/abs/2506.18792) [![arXiv](https://img.shields.io/badge/arXiv-2506.18792-b31b1b.svg)](https://arxiv.org/abs/2506.18792) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://vidar-4d.github.io/)
- **Beyond Pixels**, "From Video Priors to 4D Worlds". [![arXiv](https://img.shields.io/badge/arXiv-2608.10744-b31b1b.svg)](https://arxiv.org/abs/2608.10744)
- **Geo4D**, "Leveraging Video Generators for Geometric 4D Scene Reconstruction". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://arxiv.org/abs/2504.07961) [![arXiv](https://img.shields.io/badge/arXiv-2504.07961-b31b1b.svg)](https://arxiv.org/abs/2504.07961)
- **DriveDreamer4D**, "World Models Are Effective Data Machines for 4D Driving Scene Representation". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2410.13571) [![arXiv](https://img.shields.io/badge/arXiv-2410.13571-b31b1b.svg)](https://arxiv.org/abs/2410.13571)

## 🖼️ Image Generation (Spatially Grounded 2D Generation)

These models generate individual novel views, view sets, or panoramas while explicitly modeling cameras or geometry. They are important precursors and components for generative reconstruction, even when they do not return a persistent explicit 3D asset.

- [⭐️] **PE-Field**, "Positional Encoding Field for Geometry-Grounded Generation". [![ICLR 2026](https://img.shields.io/badge/ICLR-2026-6f42c1.svg)](https://iclr.cc/virtual/2026/poster/10009405) [![arXiv](https://img.shields.io/badge/arXiv-2510.20385-b31b1b.svg)](https://arxiv.org/abs/2510.20385) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://yunpeng1998.github.io/PE-Field-HomePage/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/MTLab/PE-Field)
- **GenWarp**, "Single Image to Novel Views with Semantic-Preserving Generative Warping". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://arxiv.org/abs/2405.17251) [![arXiv](https://img.shields.io/badge/arXiv-2405.17251-b31b1b.svg)](https://arxiv.org/abs/2405.17251) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://genwarp-nvs.github.io/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/sony/genwarp)
- **ZeroNVS**, "Zero-Shot 360-Degree View Synthesis from a Single Image". [![CVPR 2024](https://img.shields.io/badge/CVPR-2024-6f42c1.svg)](https://arxiv.org/abs/2310.17994) [![arXiv](https://img.shields.io/badge/arXiv-2310.17994-b31b1b.svg)](https://arxiv.org/abs/2310.17994)
- **GeNVS**, "Generative Novel View Synthesis with 3D-Aware Diffusion Models". [![ICCV 2023](https://img.shields.io/badge/ICCV-2023-6f42c1.svg)](https://openaccess.thecvf.com/content/ICCV2023/html/Chan_Generative_Novel_View_Synthesis_with_3D-Aware_Diffusion_Models_ICCV_2023_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2304.02602-b31b1b.svg)](https://arxiv.org/abs/2304.02602) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://nvlabs.github.io/genvs/)
- **3DiM**, "Novel View Synthesis with Diffusion Models". [![ICLR 2023](https://img.shields.io/badge/ICLR-2023-6f42c1.svg)](https://arxiv.org/abs/2210.04628) [![arXiv](https://img.shields.io/badge/arXiv-2210.04628-b31b1b.svg)](https://arxiv.org/abs/2210.04628) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://3d-diffusion.github.io/)

## Foundations, Data, and Evaluation

### Geometry foundations and reconstruction backbones

- **VGGT**, "Visual Geometry Grounded Transformer". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2503.11651) [![arXiv](https://img.shields.io/badge/arXiv-2503.11651-b31b1b.svg)](https://arxiv.org/abs/2503.11651) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/facebookresearch/vggt)
- **π³**, "Permutation-Equivariant Visual Geometry Learning". [![arXiv](https://img.shields.io/badge/arXiv-2507.13347-b31b1b.svg)](https://arxiv.org/abs/2507.13347)
- **Depth Anything 3**, "Recovering the Visual Space from Any Views". [![arXiv](https://img.shields.io/badge/arXiv-2511.10647-b31b1b.svg)](https://arxiv.org/abs/2511.10647)
- **MoGe-3**, "Multi-View Geometry Estimation". [![arXiv](https://img.shields.io/badge/arXiv-2607.17967-b31b1b.svg)](https://arxiv.org/abs/2607.17967)
- **Long-LRM**, "Long-sequence Large Reconstruction Model for Wide-coverage Gaussian Splats". [![arXiv](https://img.shields.io/badge/arXiv-2410.12781-b31b1b.svg)](https://arxiv.org/abs/2410.12781)

### Common data regimes

- **Static scenes:** DL3DV-10K, RealEstate10K, ACID, ScanNet++, Tanks and Temples, Mip-NeRF 360, LLFF, and DTU.
- **Dynamic scenes:** DyCheck, Neural 3D Video, HyperNeRF, Kubric, and synthetic multi-view video.
- **Driving:** Waymo Open, KITTI, nuScenes, and PandaSet.
- **Object-centric pretraining:** Objaverse, CO3D, Google Scanned Objects, and synthetic multi-view renders.

### Evaluation dimensions

| Dimension | Representative measures |
|---|---|
| Observed-view fidelity | PSNR, SSIM, LPIPS, reference-view reprojection, identity and texture preservation |
| Novel-view realism | FID, FVD, KID, perceptual preference, extrapolation artifact rate |
| Geometry | Depth and point-map error, camera error, correspondence accuracy, rendered-flow consistency |
| Temporal and camera control | Trajectory adherence, motion smoothness, loop closure, long-horizon drift |
| Completion | Coverage, unseen-region plausibility, uncertainty calibration, conditional diversity |
| Efficiency | End-to-end wall time, denoising steps, preprocessing, scene optimization, peak VRAM, render FPS |

Efficiency numbers should be reported for the **full pipeline**. Video sampling time, reconstruction time, preprocessing, and per-scene optimization should not be conflated.

## Contributing

Contributions of papers, code releases, project pages, corrected venue information, and new categories are very welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

The original Zotero screening, including retained, adjacent, duplicate, and excluded records, is documented in [docs/zotero-screening.md](docs/zotero-screening.md).

## Acknowledgements

The presentation style is inspired by [Awesome World Models](https://github.com/knightnemo/Awesome-World-Models). The capability taxonomy follows [Atlas](https://www.worldlabs.ai/blog/atlas), while this repository retains a narrower focus on generation–reconstruction coupling.
