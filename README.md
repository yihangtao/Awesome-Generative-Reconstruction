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

📚 **[2026-09-09] Expanded reading list** — Added influential open world systems, recent top-venue papers, text-to-panorama generation, and dedicated survey resources.

🎉 **[2026-09-02] Initial release** — Launched the repository with a screened local Zotero collection and a curated bibliography of generative reconstruction.

💡 **[Ongoing] Community Contributions Welcome** — Found a missing paper, project page, code release, or incorrect venue? Please open an issue or submit a pull request. See [CONTRIBUTING.md](CONTRIBUTING.md) for the entry format.

⭐ **[Ongoing] Support This Project** — If this collection is useful, please [star the repository](https://github.com/yihangtao/Awesome-Generative-Reconstruction) and share it with the community.

---

## Overview

- [Aim of the Project](#aim-of-the-project)
- [Definition and Scope](#definition-and-scope)
- [Industry and Frontier Systems](#-industry-and-frontier-systems)
- [Atlas-Inspired Taxonomy](#atlas-inspired-taxonomy)
- [Camera-Controlled Generation](#-camera-controlled-generation-implicit-3d-modeling)
- [Spatial Reconstruction](#-spatial-reconstruction)
- [Space-Time Simulation](#-space-time-simulation-dynamic-4d-modeling)
- [Image Generation](#-image-generation-text-to-image-and-text-to-panorama)
- [Foundations, Data, and Evaluation](#foundations-data-and-evaluation)
- [Surveys and Related Collections](#surveys-and-related-collections)
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
- ⭐️ is reserved for established, high-impact work with strong community adoption, such as substantial GitHub activity, broad downstream use, or field-shaping influence. It is deliberately applied sparingly and is not a ranking.

## 🏢 Industry and Frontier Systems

The following systems illustrate how industry and large open-source efforts are turning spatial generation into products, research platforms, or reusable foundation models. Inclusion here does not imply that every system exposes an explicit 3D representation; systems such as MiniMax H3 are listed as influential multimodal generation foundations adjacent to generative reconstruction.

- **NVIDIA — Lyra 2.0**, an explorable-world system that generates long, camera-controlled, 3D-consistent video and subsequently converts it into 3DGS or meshes. [![arXiv](https://img.shields.io/badge/arXiv-2604.13036-b31b1b.svg)](https://arxiv.org/abs/2604.13036) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/sil/lyra2/)
- **World Labs — Atlas**, an omni world model spanning camera-controlled generation, explicit spatial reconstruction, space-time simulation, and text-driven image or panorama generation through a shared spatial context. [![Website](https://img.shields.io/badge/Website-Link-blue)](https://www.worldlabs.ai/blog/atlas) [![Access](https://img.shields.io/badge/Access-Early_Access-orange)](https://www.worldlabs.ai/blog/atlas)
- **MiniMax AI — MiniMax H3**, an open general-purpose multimodal video system supporting text, image, video, and audio context with native audio-video generation. It is an adjacent video foundation rather than an explicit reconstruction model. [![Website](https://img.shields.io/badge/Website-Link-blue)](https://www.minimax.io/blog/minimax-h3) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/MiniMax-AI/MiniMax-H3) [![Demo](https://img.shields.io/badge/Demo-Hailuo-orange)](https://hailuoai.video/)
- **Shanghai AI Laboratory — YUME 1.5**, an open text- and image-conditioned interactive world foundation model with long-context generation, streaming acceleration, and keyboard control. [![arXiv](https://img.shields.io/badge/arXiv-2512.22096-b31b1b.svg)](https://arxiv.org/abs/2512.22096) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://stdstu12.github.io/YUME-Project/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/stdstu12/YUME)
- **Robbyant — LingBot-World**, an open real-time interactive video world model with minute-level memory and sub-second response in its accelerated setting. [![arXiv](https://img.shields.io/badge/arXiv-2601.20540-b31b1b.svg)](https://arxiv.org/abs/2601.20540) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Robbyant/lingbot-world)
- **Tencent Hunyuan — HY-World 2.0**, an open multimodal family for reconstructing, generating, and simulating 3D worlds from text, images, and video. [![arXiv](https://img.shields.io/badge/arXiv-2604.14268-b31b1b.svg)](https://arxiv.org/abs/2604.14268) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Tencent-Hunyuan/HY-World-2.0)

## Atlas-Inspired Taxonomy

The organization follows the four capabilities used in the [Atlas technical overview](https://www.worldlabs.ai/blog/atlas). We apply a **primary-output rule** so that each paper appears in one main category rather than being duplicated across several pipeline stages.

| Category | Primary output | Role of 3D |
|---|---|---|
| Camera-Controlled Generation | Novel-view images or videos along a requested camera path | Implicit scene state, geometry condition, spatial memory, or reconstruction-guided generation |
| Spatial Reconstruction | Novel views that recover a scene or an explicit point cloud, NeRF, mesh, or 3D Gaussian asset | Geometry is inferred through generative NVS or returned as a persistent representation |
| Space-Time Simulation | Controllable dynamic views, 4D worlds, or real-to-sim environments | Geometry and time are modeled jointly |
| Image Generation | Images or 360° panoramas generated from text | Text-conditioned appearance generation, including globally coherent spherical imagery |

## 🎥 Camera-Controlled Generation (Implicit 3D Modeling)

These methods primarily generate novel-view images or videos along specified camera trajectories. Their world is represented implicitly through geometry features, spatial memory, pose-aligned context, or a reconstruction model used inside the generation process.

### Geometry-conditioned video and novel-view generation

- [⭐️] **Lyra 2.0**, "Lyra 2.0: Explorable Generative 3D Worlds". [![arXiv](https://img.shields.io/badge/arXiv-2604.13036-b31b1b.svg)](https://arxiv.org/abs/2604.13036) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/sil/lyra2/)
- **RoGe**, "Novel View Synthesis via End-to-End Implicit Reconstruction and Generation". [![arXiv](https://img.shields.io/badge/arXiv-2609.02847-b31b1b.svg)](https://arxiv.org/abs/2609.02847) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://roge.github.io/)
- **WorldStereo**, "Bridging Camera-Guided Video Generation and Scene Reconstruction via 3D Geometric Memories". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Zhang_WorldStereo_Bridging_Camera-Guided_Video_Generation_and_Scene_Reconstruction_via_3D_CVPR_2026_paper.html)
- **CineScene**, "Implicit 3D as Effective Scene Representation for Cinematic Video Generation". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://karine-huang.github.io/CineScene/) [![arXiv](https://img.shields.io/badge/arXiv-2602.06959-b31b1b.svg)](https://arxiv.org/abs/2602.06959) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://karine-huang.github.io/CineScene/)
- **Geometry Forcing**, "Marrying Video Diffusion and 3D Representation for Consistent World Modeling". [![ICLR 2026](https://img.shields.io/badge/ICLR-2026-6f42c1.svg)](https://arxiv.org/abs/2507.07982) [![arXiv](https://img.shields.io/badge/arXiv-2507.07982-b31b1b.svg)](https://arxiv.org/abs/2507.07982)
- **PE-Field 4D**, "Video Generation Models as Canvas". [![SIGGRAPH Asia 2026](https://img.shields.io/badge/SIGGRAPH_Asia-2026-6f42c1.svg)](https://arxiv.org/abs/2607.15667) [![arXiv](https://img.shields.io/badge/arXiv-2607.15667-b31b1b.svg)](https://arxiv.org/abs/2607.15667) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/MTLab/PE-Field)
- **MVSplat360**, "Feed-Forward 360 Scene Synthesis from Sparse Views". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://arxiv.org/abs/2411.04924) [![arXiv](https://img.shields.io/badge/arXiv-2411.04924-b31b1b.svg)](https://arxiv.org/abs/2411.04924) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://donydchen.github.io/mvsplat360/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/donydchen/mvsplat)
- [⭐️] **ViewCrafter**, "Taming Video Diffusion Models for High-fidelity Novel View Synthesis". [![TPAMI 2025](https://img.shields.io/badge/TPAMI-2025-6f42c1.svg)](https://github.com/Drexubery/ViewCrafter) [![arXiv](https://img.shields.io/badge/arXiv-2409.02048-b31b1b.svg)](https://arxiv.org/abs/2409.02048) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://drexubery.github.io/ViewCrafter/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Drexubery/ViewCrafter)
- **GEN3C**, "3D-Informed World-Consistent Video Generation with Precise Camera Control". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Ren_GEN3C_3D-Informed_World-Consistent_Video_Generation_with_Precise_Camera_Control_CVPR_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2503.03751-b31b1b.svg)](https://arxiv.org/abs/2503.03751) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/nv-tlabs/GEN3C)
- **Stable Virtual Camera**, "Generative View Synthesis with 3D Camera Control". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://arxiv.org/abs/2503.14489) [![arXiv](https://img.shields.io/badge/arXiv-2503.14489-b31b1b.svg)](https://arxiv.org/abs/2503.14489) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://stable-virtual-camera.github.io/)
- **Orbital Video Generation**, "Towards Realistic and Consistent Orbital Video Generation via 3D Foundation Priors". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://arxiv.org/abs/2604.12309) [![arXiv](https://img.shields.io/badge/arXiv-2604.12309-b31b1b.svg)](https://arxiv.org/abs/2604.12309)
- **MV-Forcing**, "Long Multi-View Video Generation via 4D-Grounded Spatio-Temporal Self-Forcing". [![arXiv](https://img.shields.io/badge/arXiv-2607.05376-b31b1b.svg)](https://arxiv.org/abs/2607.05376) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://galfiebelman.github.io/mv-forcing/)
- **VGGRPO**, "Towards World-Consistent Video Generation with 4D Latent Reward". [![arXiv](https://img.shields.io/badge/arXiv-2603.26599-b31b1b.svg)](https://arxiv.org/abs/2603.26599) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://zhaochongan.github.io/projects/VGGRPO/)
- **Collaborative Video Diffusion**, "Consistent Multi-video Generation with Camera Control". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://proceedings.neurips.cc/paper_files/paper/2024/hash/1d49235669869ab737c1da9d64b7c769-Abstract-Conference.html)

### Spatial memory and long-horizon generation

- **VMem**, "Consistent Interactive Video Scene Generation with Surfel-Indexed View Memory". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://v-mem.github.io/) [![arXiv](https://img.shields.io/badge/arXiv-2506.18903-b31b1b.svg)](https://arxiv.org/abs/2506.18903) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://v-mem.github.io/)
- **Context as Memory**, "Scene-Consistent Interactive Long Video Generation with Memory Retrieval". [![SIGGRAPH Asia 2025](https://img.shields.io/badge/SIGGRAPH_Asia-2025-6f42c1.svg)](https://context-as-memory.github.io/) [![arXiv](https://img.shields.io/badge/arXiv-2506.03141-b31b1b.svg)](https://arxiv.org/abs/2506.03141) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://context-as-memory.github.io/)
- **Spatial Memory**, "Video World Models with Long-term Spatial Memory". [![arXiv](https://img.shields.io/badge/arXiv-2506.05284-b31b1b.svg)](https://arxiv.org/abs/2506.05284) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://spmem.github.io/)
- **CausNVS**, "Causal Novel View Synthesis for Real-Time World Modeling". [![Website](https://img.shields.io/badge/Website-Link-blue)](https://kxhit.github.io/CausNVS.html)

## 🏗️ Spatial Reconstruction

These methods recover a scene from visual observations or generative priors. The output may be implicit novel-view synthesis or a persistent NeRF, mesh, point cloud, or 3D Gaussian scene. This broader definition follows the reconstruction objective: newly generated views should explain the same underlying space, even when no explicit asset is returned.

### Generative novel-view synthesis and implicit reconstruction

- **FrameCrafter**, "Novel View Synthesis as Video Completion". [![arXiv](https://img.shields.io/badge/arXiv-2604.08500-b31b1b.svg)](https://arxiv.org/abs/2604.08500) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://frame-crafter.github.io/)
- **PE-Field**, "Positional Encoding Field for Geometry-Grounded Generation". [![ICLR 2026](https://img.shields.io/badge/ICLR-2026-6f42c1.svg)](https://iclr.cc/virtual/2026/poster/10009405) [![arXiv](https://img.shields.io/badge/arXiv-2510.20385-b31b1b.svg)](https://arxiv.org/abs/2510.20385) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://yunpeng1998.github.io/PE-Field-HomePage/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/MTLab/PE-Field)
- **MVGD**, "Zero-Shot Novel View and Depth Synthesis with Multi-View Geometric Diffusion". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Guizilini_Zero-Shot_Novel_View_and_Depth_Synthesis_with_Multi-View_Geometric_Diffusion_CVPR_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2501.18804-b31b1b.svg)](https://arxiv.org/abs/2501.18804) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://mvgd.github.io/)
- **GenWarp**, "Single Image to Novel Views with Semantic-Preserving Generative Warping". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://arxiv.org/abs/2405.17251) [![arXiv](https://img.shields.io/badge/arXiv-2405.17251-b31b1b.svg)](https://arxiv.org/abs/2405.17251) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://genwarp-nvs.github.io/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/sony/genwarp)
- **ZeroNVS**, "Zero-Shot 360-Degree View Synthesis from a Single Image". [![CVPR 2024](https://img.shields.io/badge/CVPR-2024-6f42c1.svg)](https://arxiv.org/abs/2310.17994) [![arXiv](https://img.shields.io/badge/arXiv-2310.17994-b31b1b.svg)](https://arxiv.org/abs/2310.17994)
- **GeNVS**, "Generative Novel View Synthesis with 3D-Aware Diffusion Models". [![ICCV 2023](https://img.shields.io/badge/ICCV-2023-6f42c1.svg)](https://openaccess.thecvf.com/content/ICCV2023/html/Chan_Generative_Novel_View_Synthesis_with_3D-Aware_Diffusion_Models_ICCV_2023_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2304.02602-b31b1b.svg)](https://arxiv.org/abs/2304.02602) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://nvlabs.github.io/genvs/)
- **3DiM**, "Novel View Synthesis with Diffusion Models". [![ICLR 2023](https://img.shields.io/badge/ICLR-2023-6f42c1.svg)](https://arxiv.org/abs/2210.04628) [![arXiv](https://img.shields.io/badge/arXiv-2210.04628-b31b1b.svg)](https://arxiv.org/abs/2210.04628) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://3d-diffusion.github.io/)

### Native and unified 3D generation–reconstruction

- [⭐️] **Lyra**, "Generative 3D Scene Reconstruction via Video Diffusion Model Self-Distillation". [![ICLR 2026](https://img.shields.io/badge/ICLR-2026-6f42c1.svg)](https://research.nvidia.com/labs/toronto-ai/lyra/) [![arXiv](https://img.shields.io/badge/arXiv-2509.19296-b31b1b.svg)](https://arxiv.org/abs/2509.19296) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/toronto-ai/lyra/)
- **FlashWorld**, "High-quality 3D Scene Generation within Seconds". [![ICLR 2026](https://img.shields.io/badge/ICLR-2026-6f42c1.svg)](https://arxiv.org/abs/2510.13678) [![arXiv](https://img.shields.io/badge/arXiv-2510.13678-b31b1b.svg)](https://arxiv.org/abs/2510.13678) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/imlixinyang/FlashWorld)
- **Free-Range Gaussians**, "Non-Grid-Aligned Generative 3D Gaussian Reconstruction". [![ECCV 2026](https://img.shields.io/badge/ECCV-2026-6f42c1.svg)](https://arxiv.org/abs/2604.04874) [![arXiv](https://img.shields.io/badge/arXiv-2604.04874-b31b1b.svg)](https://arxiv.org/abs/2604.04874) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://free-range-gaussians.github.io/)
- **Gen3R**, "3D Scene Generation Meets Feed-Forward Reconstruction". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://arxiv.org/abs/2601.04090) [![arXiv](https://img.shields.io/badge/arXiv-2601.04090-b31b1b.svg)](https://arxiv.org/abs/2601.04090) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://xdimlab.github.io/Gen3R/)
- **PixWorld**, "Unifying 3D Scene Generation and Reconstruction in Pixel Space". [![arXiv](https://img.shields.io/badge/arXiv-2607.05373-b31b1b.svg)](https://arxiv.org/abs/2607.05373) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://sensengao.github.io/PixWorld/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/SensenGao/PixWorld)
- **SPAR3S**, "Sparse Auto-Regressive Modeling for Scene Generation from Multi-View Images". [![arXiv](https://img.shields.io/badge/arXiv-2609.03931-b31b1b.svg)](https://arxiv.org/abs/2609.03931)
- **Generative Gaussian Splatting**, "Generating 3D Scenes with Video Diffusion Priors". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/ICCV2025/html/Schwarz_Generative_Gaussian_Splatting_Generating_3D_Scenes_with_Video_Diffusion_Priors_ICCV_2025_paper.html)
- **DMV3D**, "Denoising Multi-View Diffusion using 3D Large Reconstruction Model". [![ICLR 2024](https://img.shields.io/badge/ICLR-2024-6f42c1.svg)](https://arxiv.org/abs/2311.09217) [![arXiv](https://img.shields.io/badge/arXiv-2311.09217-b31b1b.svg)](https://arxiv.org/abs/2311.09217) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://justimyhxu.github.io/projects/dmv3d/)
- **DreamFusion**, "Text-to-3D using 2D Diffusion". [![ICLR 2023](https://img.shields.io/badge/ICLR-2023-6f42c1.svg)](https://arxiv.org/abs/2209.14988) [![arXiv](https://img.shields.io/badge/arXiv-2209.14988-b31b1b.svg)](https://arxiv.org/abs/2209.14988) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://dreamfusion3d.github.io/)
- **Director3D**, "Real-World Camera Trajectory and 3D Scene Generation from Text". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://proceedings.neurips.cc/paper_files/paper/2024/hash/89566c18d5b3e9836e8e16fde010b41d-Abstract-Conference.html)

### Generate views first, then reconstruct

- **CAT3D**, "Create Anything in 3D with Multi-View Diffusion Models". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://arxiv.org/abs/2405.10314) [![arXiv](https://img.shields.io/badge/arXiv-2405.10314-b31b1b.svg)](https://arxiv.org/abs/2405.10314) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://cat3d.github.io/)
- [⭐️] **HY-World 2.0**, "A Multi-Modal World Model for Reconstructing, Generating, and Simulating 3D Worlds". [![arXiv](https://img.shields.io/badge/arXiv-2604.14268-b31b1b.svg)](https://arxiv.org/abs/2604.14268) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Tencent-Hunyuan/HY-World-2.0)
- **Matrix-3D**, "Omnidirectional Explorable 3D World Generation". [![arXiv](https://img.shields.io/badge/arXiv-2508.08086-b31b1b.svg)](https://arxiv.org/abs/2508.08086) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://matrix-3d.github.io/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/SkyworkAI/Matrix-3D)
- **WorldExplorer**, "Towards Generating Fully Navigable 3D Scenes". [![SIGGRAPH Asia 2025](https://img.shields.io/badge/SIGGRAPH_Asia-2025-6f42c1.svg)](https://arxiv.org/abs/2506.01799) [![arXiv](https://img.shields.io/badge/arXiv-2506.01799-b31b1b.svg)](https://arxiv.org/abs/2506.01799) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://mschneider456.github.io/world-explorer/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/mschneider456/WorldExplorer)
- **Scene Splatter**, "Momentum 3D Scene Generation from Single Image with Video Diffusion Model". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Zhang_Scene_Splatter_Momentum_3D_Scene_Generation_from_Single_Image_with_CVPR_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2504.02764-b31b1b.svg)](https://arxiv.org/abs/2504.02764)
- **ReconX**, "Reconstruct Any Scene from Sparse Views with Video Diffusion Model". [![arXiv](https://img.shields.io/badge/arXiv-2408.16767-b31b1b.svg)](https://arxiv.org/abs/2408.16767)
- **Text2Room**, "Extracting Textured 3D Meshes from 2D Text-to-Image Models". [![ICCV 2023](https://img.shields.io/badge/ICCV-2023-6f42c1.svg)](https://arxiv.org/abs/2303.11989) [![arXiv](https://img.shields.io/badge/arXiv-2303.11989-b31b1b.svg)](https://arxiv.org/abs/2303.11989) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://lukas-hoellein.github.io/text2room/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/lukasHoel/text2room)
- **WorldGen**, "From Text to Traversable and Interactive 3D Worlds". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Wang_WorldGen_From_Text_to_Traversable_and_Interactive_3D_Worlds_CVPR_2026_paper.html)
- **WonderWorld**, "Interactive 3D Scene Generation from a Single Image". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Yu_WonderWorld_Interactive_3D_Scene_Generation_from_a_Single_Image_CVPR_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2406.09394-b31b1b.svg)](https://arxiv.org/abs/2406.09394)
- **DreamScene360**, "Unconstrained Text-to-3D Scene Generation with Panoramic Gaussian Splatting". [![ECCV 2024](https://img.shields.io/badge/ECCV-2024-6f42c1.svg)](https://dreamscene360.github.io/) [![arXiv](https://img.shields.io/badge/arXiv-2404.06903-b31b1b.svg)](https://arxiv.org/abs/2404.06903) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://dreamscene360.github.io/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/ShijieZhou-UCLA/DreamScene360)
- **LucidDreamer**, "Domain-Free Generation of 3D Gaussian Splatting Scenes". [![TVCG 2025](https://img.shields.io/badge/TVCG-2025-6f42c1.svg)](https://luciddreamer-cvlab.github.io/) [![arXiv](https://img.shields.io/badge/arXiv-2311.13384-b31b1b.svg)](https://arxiv.org/abs/2311.13384) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/luciddreamer-cvlab/LucidDreamer)
- **SGAM**, "Building a Virtual 3D World through Simultaneous Generation and Mapping". [![NeurIPS 2022](https://img.shields.io/badge/NeurIPS-2022-6f42c1.svg)](https://proceedings.neurips.cc/paper_files/paper/2022/hash/8ae9cf363ea625161f885b798c1f1f78-Abstract-Conference.html)

### Reconstruction–generation loops and repair

- **GenFusion**, "Closing the Loop between Reconstruction and Generation via Videos". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2503.21219) [![arXiv](https://img.shields.io/badge/arXiv-2503.21219-b31b1b.svg)](https://arxiv.org/abs/2503.21219) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Inception3D/GenFusion)
- **Geometry-as-Context**, "Modulating Explicit 3D in Scene-Consistent Video Generation to Geometry Context". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Hu_Geometry-as-context_Modulating_Explicit_3D_in_Scene-consistent_Video_Generation_to_Geometry_CVPR_2026_paper.html)
- **GaussFusion**, "Improving 3D Reconstruction in the Wild with a Geometry-Informed Video Generator". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Zhu_GaussFusion_Improving_3D_Reconstruction_in_the_Wild_with_A_Geometry-Informed_CVPR_2026_paper.html)
- **Scene-Grounding Guidance**, "Taming Video Diffusion Prior with Scene-Grounding Guidance for 3D Gaussian Splatting from Sparse Inputs". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2503.05082) [![arXiv](https://img.shields.io/badge/arXiv-2503.05082-b31b1b.svg)](https://arxiv.org/abs/2503.05082)
- **Generative Sparse-View Gaussian Splatting**, "Generative Sparse-View Gaussian Splatting". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Kong_Generative_Sparse-View_Gaussian_Splatting_CVPR_2025_paper.html)
- **ReconFusion**, "3D Reconstruction with Diffusion Priors". [![CVPR 2024](https://img.shields.io/badge/CVPR-2024-6f42c1.svg)](https://arxiv.org/abs/2312.02981) [![arXiv](https://img.shields.io/badge/arXiv-2312.02981-b31b1b.svg)](https://arxiv.org/abs/2312.02981) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://reconfusion.github.io/)
- **FaithFusion**, "Harmonizing Reconstruction and Generation via Pixel-wise Information Gain". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://arxiv.org/abs/2511.21113) [![arXiv](https://img.shields.io/badge/arXiv-2511.21113-b31b1b.svg)](https://arxiv.org/abs/2511.21113) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/wangyuanbiubiubiu/FaithFusion)
- **VidSplat**, "Gaussian Splatting Reconstruction with Geometry-Guided Video Diffusion Priors". [![arXiv](https://img.shields.io/badge/arXiv-2605.11424-b31b1b.svg)](https://arxiv.org/abs/2605.11424)
- **Sparse-to-Complete**, "From Sparse Image Captures to Complete 3D Scenes". [![arXiv](https://img.shields.io/badge/arXiv-2605.05664-b31b1b.svg)](https://arxiv.org/abs/2605.05664) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://gapszju.github.io/S2C-3D/)
- **Few Glimpses**, "Novel View Synthesis from A Few Glimpses via Test-Time Natural Video Completion". [![arXiv](https://img.shields.io/badge/arXiv-2511.17932-b31b1b.svg)](https://arxiv.org/abs/2511.17932)
- [⭐️] **Difix3D+**, "Improving 3D Reconstructions with Single-Step Diffusion Models". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2503.01774) [![arXiv](https://img.shields.io/badge/arXiv-2503.01774-b31b1b.svg)](https://arxiv.org/abs/2503.01774) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/toronto-ai/difix3d/)
- **GSFixer**, "Improving 3D Gaussian Splatting with Reference-Guided Video Diffusion Priors". [![arXiv](https://img.shields.io/badge/arXiv-2508.09667-b31b1b.svg)](https://arxiv.org/abs/2508.09667) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/GVCLab/GSFixer)
- **ArtiFixer**, "Enhancing and Extending 3D Reconstruction with Auto-Regressive Diffusion Models". [![arXiv](https://img.shields.io/badge/arXiv-2603.00492-b31b1b.svg)](https://arxiv.org/abs/2603.00492) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/sil/projects/artifixer)
- **GaussVid**, "Sparse-View Gaussian Splatting with 3D-Aware Video Diffusion Priors". [![arXiv](https://img.shields.io/badge/arXiv-2608.21849-b31b1b.svg)](https://arxiv.org/abs/2608.21849) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Xinhui-99/GaussVid)
- **FixAnything**, "3D-Consistent Rendering Refinement via Video Generative Priors". [![arXiv](https://img.shields.io/badge/arXiv-2608.23549-b31b1b.svg)](https://arxiv.org/abs/2608.23549)
- **WonderFree**, "Enhancing Novel View Quality and Cross-View Consistency for 3D Scene Exploration". [![arXiv](https://img.shields.io/badge/arXiv-2506.20590-b31b1b.svg)](https://arxiv.org/abs/2506.20590)

## ⏱️ Space-Time Simulation (Dynamic 4D Modeling)

These works model both viewpoint and temporal evolution. The primary deliverable is a controllable dynamic world, a 4D representation, or a real-to-sim environment rather than a static scene or a single camera path.

### Interactive video world models

- [⭐️] **YUME 1.5**, "A Text-Controlled Interactive World Generation Model". [![arXiv](https://img.shields.io/badge/arXiv-2512.22096-b31b1b.svg)](https://arxiv.org/abs/2512.22096) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://stdstu12.github.io/YUME-Project/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/stdstu12/YUME)
- [⭐️] **LingBot-World**, "Advancing Open-Source World Models". [![arXiv](https://img.shields.io/badge/arXiv-2601.20540-b31b1b.svg)](https://arxiv.org/abs/2601.20540) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Robbyant/lingbot-world)
- **LingBot-World 2.0**, "Infinite Worlds with Versatile Interactions". [![arXiv](https://img.shields.io/badge/arXiv-2607.07534-b31b1b.svg)](https://arxiv.org/abs/2607.07534) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Robbyant/lingbot-world-v2)
- **BiWM**, "Advancing Open-Source Interactive Video World Models with Bidirectional Autoregression". [![arXiv](https://img.shields.io/badge/arXiv-2606.10135-b31b1b.svg)](https://arxiv.org/abs/2606.10135)

### Dynamic 4D generation and reconstruction

- **CAT4D**, "Create Anything in 4D with Multi-View Video Diffusion Models". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2411.18613) [![arXiv](https://img.shields.io/badge/arXiv-2411.18613-b31b1b.svg)](https://arxiv.org/abs/2411.18613) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://cat-4d.github.io/)
- **WorldReel**, "4D Video Generation with Consistent Geometry and Motion Modeling". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Fang_WorldReel_4D_Video_Generation_with_Consistent_Geometry_and_Motion_Modeling_CVPR_2026_paper.html)
- **DimensionX**, "Create Any 3D and 4D Scenes from a Single Image with Decoupled Video Diffusion". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://arxiv.org/abs/2411.04928) [![arXiv](https://img.shields.io/badge/arXiv-2411.04928-b31b1b.svg)](https://arxiv.org/abs/2411.04928) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://chenshuo20.github.io/DimensionX/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/wenqsun/DimensionX)
- **DreamDrive**, "Generative 4D Scene Modeling from Street View Images". [![ICRA 2025](https://img.shields.io/badge/ICRA-2025-6f42c1.svg)](https://arxiv.org/abs/2501.00601) [![arXiv](https://img.shields.io/badge/arXiv-2501.00601-b31b1b.svg)](https://arxiv.org/abs/2501.00601) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/NVlabs/DreamDrive)
- **ViDAR**, "Video Diffusion-Aware 4D Reconstruction From Monocular Inputs". [![NeurIPS 2025](https://img.shields.io/badge/NeurIPS-2025-6f42c1.svg)](https://arxiv.org/abs/2506.18792) [![arXiv](https://img.shields.io/badge/arXiv-2506.18792-b31b1b.svg)](https://arxiv.org/abs/2506.18792) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://vidar-4d.github.io/)
- **Beyond Pixels**, "From Video Priors to 4D Worlds". [![arXiv](https://img.shields.io/badge/arXiv-2608.10744-b31b1b.svg)](https://arxiv.org/abs/2608.10744)
- **Geo4D**, "Leveraging Video Generators for Geometric 4D Scene Reconstruction". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://arxiv.org/abs/2504.07961) [![arXiv](https://img.shields.io/badge/arXiv-2504.07961-b31b1b.svg)](https://arxiv.org/abs/2504.07961)
- **DriveDreamer4D**, "World Models Are Effective Data Machines for 4D Driving Scene Representation". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2410.13571) [![arXiv](https://img.shields.io/badge/arXiv-2410.13571-b31b1b.svg)](https://arxiv.org/abs/2410.13571)

## 🖼️ Image Generation (Text-to-Image and Text-to-Panorama)

This category follows Atlas's narrower image-generation capability: models synthesize images or globally coherent 360° panoramas from text. Reference-conditioned novel-view synthesis belongs to [Spatial Reconstruction](#-spatial-reconstruction), rather than this section.

- **PanFusion**, "Taming Stable Diffusion for Text to 360 Panorama Image Generation". [![CVPR 2024](https://img.shields.io/badge/CVPR-2024-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2024/html/Zhang_Taming_Stable_Diffusion_for_Text_to_360_Panorama_Image_Generation_CVPR_2024_paper.html)
- **CubeDiff**, "Repurposing Diffusion-Based Image Models for Panorama Generation". [![ICLR 2025](https://img.shields.io/badge/ICLR-2025-6f42c1.svg)](https://proceedings.iclr.cc/paper_files/paper/2025/hash/c9ef471a579197c4ed99df2aa542ce97-Abstract-Conference.html)
- **StitchDiffusion**, "Customizing 360-Degree Panoramas through Text-to-Image Diffusion Models". [![WACV 2024](https://img.shields.io/badge/WACV-2024-6f42c1.svg)](https://openaccess.thecvf.com/content/WACV2024/html/Wang_Customizing_360-Degree_Panoramas_Through_Text-to-Image_Diffusion_Models_WACV_2024_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2310.18840-b31b1b.svg)](https://arxiv.org/abs/2310.18840) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/littlewhitesea/StitchDiffusion)
- **Text2Light**, "Zero-Shot Text-Driven HDR Panorama Generation". [![SIGGRAPH Asia 2022](https://img.shields.io/badge/SIGGRAPH_Asia-2022-6f42c1.svg)](https://arxiv.org/abs/2209.09898) [![arXiv](https://img.shields.io/badge/arXiv-2209.09898-b31b1b.svg)](https://arxiv.org/abs/2209.09898) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/FrozenBurning/Text2Light)
- **UniPano**, "What Makes for Text to 360-Degree Panorama Generation with Stable Diffusion?". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/ICCV2025/html/Ni_What_Makes_for_Text_to_360-degree_Panorama_Generation_with_Stable_ICCV_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2505.22129-b31b1b.svg)](https://arxiv.org/abs/2505.22129) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/jinhong-ni/UniPano)

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

## Surveys and Related Collections

- **Generative 3D Reconstruction Survey**, "A Survey of Recent Advances in Generative 3D Reconstruction". [![JCST 2025](https://img.shields.io/badge/JCST-2025-6f42c1.svg)](https://jcst.ict.ac.cn/article/doi/10.1007/s11390-025-5462-4)
- **3D Scene Generation Survey**, "3D Scene Generation: A Survey". [![arXiv](https://img.shields.io/badge/arXiv-2505.05474-b31b1b.svg)](https://arxiv.org/abs/2505.05474) [![Collection](https://img.shields.io/badge/Collection-GitHub-green)](https://github.com/hzxie/Awesome-3D-Scene-Generation)
- **3D and 4D World Modeling Survey**, "3D and 4D World Modeling: A Survey". [![arXiv](https://img.shields.io/badge/arXiv-2509.07996-b31b1b.svg)](https://arxiv.org/abs/2509.07996) [![Collection](https://img.shields.io/badge/Collection-GitHub-green)](https://github.com/worldbench/survey)
- **Multimodal Generative Models Survey**, "Simulating the Real World: A Unified Survey of Multimodal Generative Models". [![TPAMI 2026](https://img.shields.io/badge/TPAMI-2026-6f42c1.svg)](https://arxiv.org/abs/2503.04641) [![arXiv](https://img.shields.io/badge/arXiv-2503.04641-b31b1b.svg)](https://arxiv.org/abs/2503.04641) [![Collection](https://img.shields.io/badge/Collection-GitHub-green)](https://github.com/ALEEEHU/World-Simulator)
- **Immersive Video Survey**, "Generative AI for Immersive Video: Recent Advances and Future Opportunities". [![IJCAI 2025](https://img.shields.io/badge/IJCAI-2025-6f42c1.svg)](https://www.ijcai.org/proceedings/2025/1162.pdf)
- **Text-to-Panorama Survey**, "A Survey on Text-Driven 360-Degree Panorama Generation". [![arXiv](https://img.shields.io/badge/arXiv-2502.14799-b31b1b.svg)](https://arxiv.org/abs/2502.14799)

## Contributing

Contributions of papers, code releases, project pages, corrected venue information, and new categories are very welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

The original Zotero screening, including retained, adjacent, duplicate, and excluded records, is documented in [docs/zotero-screening.md](docs/zotero-screening.md).

## Acknowledgements

The presentation style is inspired by [Awesome World Models](https://github.com/knightnemo/Awesome-World-Models). The capability taxonomy follows [Atlas](https://www.worldlabs.ai/blog/atlas), while this repository retains a narrower focus on generation–reconstruction coupling.
