<div align="center">

# 🌐 Awesome Generative Reconstruction

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Updated](https://img.shields.io/badge/updated-September%202026-6c5ce7.svg)](#-news--updates)
[![Star this repo](https://img.shields.io/badge/%E2%AD%90-Star_this_repo-yellow.svg)](https://github.com/yihangtao/Awesome-Generative-Reconstruction)

**📜 A curated list of research that unifies generation and reconstruction for spatially consistent worlds.**<br>
*From 3D-guided video generation to generation-guided reconstruction and post-reconstruction refinement.*

<p align="center">
  <img src="assets/hero.png" alt="Sparse observations becoming a generated and reconstructed 3D world" width="100%">
</p>

*Cover generated for this collection with OpenAI ImageGen.*

</div>

---

## 🚩 News & Updates

🔥 **[2026-09-11] Pipeline-aware taxonomy** — Reorganized the collection by how geometry and generation interact: **3D-guided video generation**, **generation-guided 3D reconstruction**, and **generative refinement after reconstruction**.

📚 **[2026-09-09] Expanded reading list** — Added influential open world systems, recent top-venue papers, and dedicated survey resources.

🎉 **[2026-09-02] Initial release** — Launched the repository with a curated bibliography of generative reconstruction.

💡 **[Ongoing] Community Contributions Welcome** — Found a missing paper, project page, code release, or incorrect venue? Please open an issue or submit a pull request. See [CONTRIBUTING.md](CONTRIBUTING.md) for the entry format.

⭐ **[Ongoing] Support This Project** — If this collection is useful, please [star the repository](https://github.com/yihangtao/Awesome-Generative-Reconstruction) and share it with the community.

---

## Overview

- [Aim of the Project](#aim-of-the-project)
- [Definition and Scope](#definition-and-scope)
- [Industry and Frontier Systems](#-industry-and-frontier-systems)
- [Taxonomy](#taxonomy)
- [3D-Guided Video Generation](#-3d-guided-video-generation)
- [Generation-Guided 3D Reconstruction](#-generation-guided-3d-reconstruction)
- [Generative Refinement of 3D Reconstructions](#-generative-refinement-of-3d-reconstructions)
- [Foundation Models](#-foundation-models)
- [Surveys and Related Collections](#surveys-and-related-collections)
- [Contributing](#contributing)

## Aim of the Project

Generative reconstruction studies how generative priors and spatial reconstruction can be coupled to build complete, explorable scenes from incomplete observations. Reconstruction preserves visible evidence and supplies geometric structure, while generation fills regions that were never observed. A successful system must therefore produce a coherent world that remains faithful to the reference inputs, extends naturally beyond them, and supports high-quality rendering from new viewpoints.

Many recent methods combine two complementary representation spaces: the visual latent of a video diffusion model and the geometric latent or explicit scene representation produced by a 3D foundation model. This connection is also closely related to unified visual understanding and generation: geometry provides structured scene understanding, while the generative model supplies appearance and completion priors. This repository focuses on scene- and world-level methods in which these components materially affect one another, rather than appearing as unrelated stages.

## Definition and Scope

We use **generative reconstruction** as an umbrella term for models that jointly address four requirements:

1. **Observation fidelity** — outputs remain compatible with the available images, videos, text, or partial geometry.
2. **Generative completion** — unseen or weakly observed regions are synthesized rather than left empty.
3. **Spatial consistency** — views correspond to a coherent 3D or 4D world, represented explicitly or implicitly.
4. **Model-level coupling** — geometry affects generation, or generation affects reconstruction, through conditioning, memory, denoising, supervision, optimization, decoding, or rendering refinement.

Pure text-to-video generation, conventional dense-view reconstruction without a generative component, generic image enhancement detached from a 3D scene, and standalone depth or pose estimation are outside the core list. General-purpose enabling backbones are listed separately under [Foundation Models](#-foundation-models).

### Badge legend

- **Venue** badges are included only when an official conference or proceedings page is available.
- **arXiv** links point to the primary manuscript.
- **Website** and **Code** badges point to official project pages and author repositories.
- ⭐️ is reserved for established, high-impact work with strong community adoption, such as substantial GitHub activity, broad downstream use, or field-shaping influence. It is deliberately applied sparingly and is not a ranking.

## 🏢 Industry and Frontier Systems

The following systems illustrate how industry and large open-source efforts are turning spatial generation into products, research platforms, or reusable foundation models. Inclusion here does not imply that every system exposes an explicit 3D representation; systems such as MiniMax H3 are listed as influential multimodal generation foundations adjacent to generative reconstruction. Systems are ordered by their first official public release.

- **World Labs — Atlas**, an omni world model spanning camera-controlled generation, explicit spatial reconstruction, and space-time simulation through a shared spatial context. [![Website](https://img.shields.io/badge/Website-Link-blue)](https://www.worldlabs.ai/blog/atlas) [![Access](https://img.shields.io/badge/Access-Early_Access-orange)](https://www.worldlabs.ai/blog/atlas)
- **MiniMax AI — MiniMax H3**, an open general-purpose multimodal video system supporting text, image, video, and audio context with native audio-video generation. It is an adjacent video foundation rather than an explicit reconstruction model. [![Website](https://img.shields.io/badge/Website-Link-blue)](https://www.minimax.io/blog/minimax-h3) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/MiniMax-AI/MiniMax-H3) [![Demo](https://img.shields.io/badge/Demo-Hailuo-orange)](https://hailuoai.video/)
- **Tencent Hunyuan — HY-World 2.0**, an open multimodal family for reconstructing, generating, and simulating 3D worlds from text, images, and video. [![arXiv](https://img.shields.io/badge/arXiv-2604.14268-b31b1b.svg)](https://arxiv.org/abs/2604.14268) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Tencent-Hunyuan/HY-World-2.0)
- **NVIDIA — Lyra 2.0**, an explorable-world system that generates long, camera-controlled, 3D-consistent video and subsequently converts it into 3DGS or meshes. [![arXiv](https://img.shields.io/badge/arXiv-2604.13036-b31b1b.svg)](https://arxiv.org/abs/2604.13036) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://nv-tlabs.github.io/Project-Lyra/)
- **Robbyant — LingBot-World**, an open real-time interactive video world model with minute-level memory and sub-second response in its accelerated setting. [![arXiv](https://img.shields.io/badge/arXiv-2601.20540-b31b1b.svg)](https://arxiv.org/abs/2601.20540) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Robbyant/lingbot-world)
- **Shanghai AI Laboratory — Yume-1.5**, an open text- and image-conditioned interactive world foundation model with long-context generation, streaming acceleration, and keyboard control. [![arXiv](https://img.shields.io/badge/arXiv-2512.22096-b31b1b.svg)](https://arxiv.org/abs/2512.22096) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://stdstu12.github.io/YUME-Project/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/stdstu12/YUME)

## Taxonomy

The list is organized by the **direction of information flow between generation and reconstruction**. Each work appears in one primary category, chosen according to its main output and the stage at which the generative or geometric prior is introduced. Input type is used only as a secondary grouping.

| Direction | Primary output | Core interaction |
|---|---|---|
| 3D-Guided Video Generation | Camera-controlled, spatially consistent video or novel-view sequence | A 3D prior, reconstruction, depth, correspondence, memory, or geometric reward constrains video generation |
| Generation-Guided 3D Reconstruction | Reusable 3D/4D representation such as 3DGS, NeRF, mesh, point cloud, or geometry field | A pretrained image/video generator supplies missing observations, optimization guidance, or a generative decoder |
| Generative Refinement of 3D Reconstructions | Repaired renderings and, in some methods, an improved underlying scene | A generative model operates after an initial reconstruction to remove rendering artifacts or complete under-observed regions |

## 🎥 3D-Guided Video Generation

These methods use reconstruction or geometric reasoning to improve generation. A 3D foundation model, explicit proxy, depth sequence, correspondence field, spatial memory, or geometric reward constrains the video model so that the generated views follow a requested trajectory and remain compatible with the reference scene. The primary output is a video or novel-view sequence; any reconstructed geometry mainly serves generation.

### Text

- **VGGRPO**, "VGGRPO: Towards World-Consistent Video Generation with 4D Latent Reward". [![ECCV 2026](https://img.shields.io/badge/ECCV-2026-6f42c1.svg)](https://arxiv.org/abs/2603.26599) [![arXiv](https://img.shields.io/badge/arXiv-2603.26599-b31b1b.svg)](https://arxiv.org/abs/2603.26599) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://zhaochongan.github.io/projects/VGGRPO/)
- **WorldReel**, "WorldReel: 4D Video Generation with Consistent Geometry and Motion Modeling". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Fang_WorldReel_4D_Video_Generation_with_Consistent_Geometry_and_Motion_Modeling_CVPR_2026_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2512.07821-b31b1b.svg)](https://arxiv.org/abs/2512.07821)
- **CVD**, "Collaborative Video Diffusion: Consistent Multi-video Generation with Camera Control". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://proceedings.neurips.cc/paper_files/paper/2024/hash/1d49235669869ab737c1da9d64b7c769-Abstract-Conference.html) [![arXiv](https://img.shields.io/badge/arXiv-2405.17414-b31b1b.svg)](https://arxiv.org/abs/2405.17414) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://collaborativevideodiffusion.github.io/)

### Text / Image

- **GeoVideo**, "GeoVideo: Introducing Geometric Regularization into Video Generation Model". [![NeurIPS 2025](https://img.shields.io/badge/NeurIPS-2025-6f42c1.svg)](https://proceedings.neurips.cc/paper_files/paper/2025/hash/536d18fbb454f80221465f1a42c6f389-Abstract-Conference.html) [![arXiv](https://img.shields.io/badge/arXiv-2512.03453-b31b1b.svg)](https://arxiv.org/abs/2512.03453) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://geovideo.github.io/GeoVideo/)
- **ViCoDR**, "View-Consistent Diffusion Representations for 3D-Consistent Video Generation". [![arXiv](https://img.shields.io/badge/arXiv-2511.18991-b31b1b.svg)](https://arxiv.org/abs/2511.18991) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://danier97.github.io/ViCoDR/)
- **Epipolar Geometry**, "Epipolar Geometry Improves Video Generation Models". [![arXiv](https://img.shields.io/badge/arXiv-2510.21615-b31b1b.svg)](https://arxiv.org/abs/2510.21615)

### Single Image

- [⭐️] **Lyra 2.0**, "Lyra 2.0: Explorable Generative 3D Worlds". [![arXiv](https://img.shields.io/badge/arXiv-2604.13036-b31b1b.svg)](https://arxiv.org/abs/2604.13036) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://nv-tlabs.github.io/Project-Lyra/)
- **Orbital Video Generation**, "Towards Realistic and Consistent Orbital Video Generation via 3D Foundation Priors". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://arxiv.org/abs/2604.12309) [![arXiv](https://img.shields.io/badge/arXiv-2604.12309-b31b1b.svg)](https://arxiv.org/abs/2604.12309)
- **WorldStereo**, "WorldStereo: Bridging Camera-Guided Video Generation and Scene Reconstruction via 3D Geometric Memories". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Zhang_WorldStereo_Bridging_Camera-Guided_Video_Generation_and_Scene_Reconstruction_via_3D_CVPR_2026_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2603.02049-b31b1b.svg)](https://arxiv.org/abs/2603.02049)
- **Geometry-as-Context**, "Geometry-as-context: Modulating Explicit 3D in Scene-consistent Video Generation to Geometry Context". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Hu_Geometry-as-context_Modulating_Explicit_3D_in_Scene-consistent_Video_Generation_to_Geometry_CVPR_2026_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2602.21929-b31b1b.svg)](https://arxiv.org/abs/2602.21929)
- **VideoGPA**, "VideoGPA: Distilling Geometry Priors for 3D-Consistent Video Generation". [![arXiv](https://img.shields.io/badge/arXiv-2601.23286-b31b1b.svg)](https://arxiv.org/abs/2601.23286) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://hongyang-du.github.io/VideoGPA-Website/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Hongyang-Du/VideoGPA)
- **DualCamCtrl**, "DualCamCtrl: Dual-Branch Diffusion Model for Geometry-Aware Camera-Controlled Video Generation". [![arXiv](https://img.shields.io/badge/arXiv-2511.23127-b31b1b.svg)](https://arxiv.org/abs/2511.23127) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://soyouthinkyoucantell.github.io/dualcamctrl-page/)
- **PE-Field**, "Positional Encoding Field". [![arXiv](https://img.shields.io/badge/arXiv-2510.20385-b31b1b.svg)](https://arxiv.org/abs/2510.20385) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://yunpeng1998.github.io/PE-Field-HomePage/)
- **Geometry Forcing**, "Geometry Forcing: Marrying Video Diffusion and 3D Representation for Consistent World Modeling". [![ICLR 2026](https://img.shields.io/badge/ICLR-2026-6f42c1.svg)](https://arxiv.org/abs/2507.07982) [![arXiv](https://img.shields.io/badge/arXiv-2507.07982-b31b1b.svg)](https://arxiv.org/abs/2507.07982)
- **WonderFree**, "WonderFree: Enhancing Novel View Quality and Cross-View Consistency for 3D Scene Exploration". [![arXiv](https://img.shields.io/badge/arXiv-2506.20590-b31b1b.svg)](https://arxiv.org/abs/2506.20590)
- **VMem**, "VMem: Consistent Interactive Video Scene Generation with Surfel-Indexed View Memory". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://arxiv.org/abs/2506.18903) [![arXiv](https://img.shields.io/badge/arXiv-2506.18903-b31b1b.svg)](https://arxiv.org/abs/2506.18903) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://v-mem.github.io/)
- **Spatial Memory**, "Video World Models with Long-term Spatial Memory". [![arXiv](https://img.shields.io/badge/arXiv-2506.05284-b31b1b.svg)](https://arxiv.org/abs/2506.05284) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://spmem.github.io/)
- **Context-as-Memory**, "Context as Memory: Scene-Consistent Interactive Long Video Generation with Memory Retrieval". [![SIGGRAPH Asia 2025](https://img.shields.io/badge/SIGGRAPH_Asia-2025-6f42c1.svg)](https://arxiv.org/abs/2506.03141) [![arXiv](https://img.shields.io/badge/arXiv-2506.03141-b31b1b.svg)](https://arxiv.org/abs/2506.03141) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://context-as-memory.github.io/)
- **WorldMem**, "WorldMem: Long-term Consistent World Simulation with Memory". [![NeurIPS 2025](https://img.shields.io/badge/NeurIPS-2025-6f42c1.svg)](https://proceedings.neurips.cc/paper_files/paper/2025/hash/470629a47e2d65ce0606c40055df5d26-Abstract-Conference.html) [![arXiv](https://img.shields.io/badge/arXiv-2504.12369-b31b1b.svg)](https://arxiv.org/abs/2504.12369) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://xizaoqu.github.io/worldmem/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/xizaoqu/WorldMem)
- **Uni3C**, "Uni3C: Unifying Precisely 3D-Enhanced Camera and Human Motion Controls for Video Generation". [![SIGGRAPH Asia 2025](https://img.shields.io/badge/SIGGRAPH_Asia-2025-6f42c1.svg)](https://doi.org/10.1145/3757377.3763842) [![arXiv](https://img.shields.io/badge/arXiv-2504.14899-b31b1b.svg)](https://arxiv.org/abs/2504.14899) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://ewrfcas.github.io/Uni3C/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/alibaba-damo-academy/Uni3C)
- **I2V3D**, "I2V3D: Controllable image-to-video generation with 3D guidance". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/ICCV2025/html/Zhang_I2V3D_Controllable_Image-to-video_Generation_with_3D_Guidance_ICCV_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2503.09733-b31b1b.svg)](https://arxiv.org/abs/2503.09733) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://bestzzhang.github.io/I2V3D/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/bestzzhang/I2V3D_code)
- **Diffusion as Shader**, "Diffusion as Shader: 3D-aware Video Diffusion for Versatile Video Generation Control". [![arXiv](https://img.shields.io/badge/arXiv-2501.03847-b31b1b.svg)](https://arxiv.org/abs/2501.03847) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://igl-hkust.github.io/das/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/IGL-HKUST/DiffusionAsShader)
- **DimensionX**, "DimensionX: Create Any 3D and 4D Scenes from a Single Image with Controllable Video Diffusion". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://arxiv.org/abs/2411.04928) [![arXiv](https://img.shields.io/badge/arXiv-2411.04928-b31b1b.svg)](https://arxiv.org/abs/2411.04928) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://chenshuo20.github.io/DimensionX/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/wenqsun/DimensionX)
- **MultiDiff**, "MultiDiff: Consistent Novel View Synthesis from a Single Image". [![CVPR 2024](https://img.shields.io/badge/CVPR-2024-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2024/html/Muller_MultiDiff_Consistent_Novel_View_Synthesis_from_a_Single_Image_CVPR_2024_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2406.18524-b31b1b.svg)](https://arxiv.org/abs/2406.18524) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://www.normanm.de/MultiDiff/)
- **GenWarp**, "GenWarp: Single Image to Novel Views with Semantic-Preserving Generative Warping". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://proceedings.neurips.cc/paper_files/paper/2024/hash/92e886487a8354b03d8bf4416eae6d7d-Abstract-Conference.html) [![arXiv](https://img.shields.io/badge/arXiv-2405.17251-b31b1b.svg)](https://arxiv.org/abs/2405.17251) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/sony/genwarp)
- **ZeroNVS**, "ZeroNVS: Zero-Shot 360-Degree View Synthesis from a Single Real Image". [![CVPR 2024](https://img.shields.io/badge/CVPR-2024-6f42c1.svg)](https://arxiv.org/abs/2310.17994) [![arXiv](https://img.shields.io/badge/arXiv-2310.17994-b31b1b.svg)](https://arxiv.org/abs/2310.17994)
- **GeNVS**, "GeNVS: Generative Novel View Synthesis with 3D-Aware Diffusion Models". [![ICCV 2023](https://img.shields.io/badge/ICCV-2023-6f42c1.svg)](https://arxiv.org/abs/2304.02698) [![arXiv](https://img.shields.io/badge/arXiv-2304.02698-b31b1b.svg)](https://arxiv.org/abs/2304.02698) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://nvlabs.github.io/genvs/)
- **3DiM**, "3DiM: Learning Single-Image 3D Reconstruction with Generative Models". [![ICLR 2023](https://img.shields.io/badge/ICLR-2023-6f42c1.svg)](https://arxiv.org/abs/2210.04628) [![arXiv](https://img.shields.io/badge/arXiv-2210.04628-b31b1b.svg)](https://arxiv.org/abs/2210.04628)

### Sparse Images

- **RoGe**, "RoGe: Novel View Synthesis via End-to-End Implicit Reconstruction and Generation". [![arXiv](https://img.shields.io/badge/arXiv-2609.02847-b31b1b.svg)](https://arxiv.org/abs/2609.02847) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://roge.github.io/)
- **FrameCrafter**, "Novel View Synthesis as Video Completion". [![ECCV 2026](https://img.shields.io/badge/ECCV-2026-6f42c1.svg)](https://arxiv.org/abs/2604.08500) [![arXiv](https://img.shields.io/badge/arXiv-2604.08500-b31b1b.svg)](https://arxiv.org/abs/2604.08500) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://frame-crafter.github.io/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/szqwu/FrameCrafter)
- **CineScene**, "CineScene: Implicit 3D as Effective Scene Representation for Cinematic Video Generation". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://karine-huang.github.io/CineScene/) [![arXiv](https://img.shields.io/badge/arXiv-2602.06959-b31b1b.svg)](https://arxiv.org/abs/2602.06959) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://karine-huang.github.io/CineScene/)
- **CausNVS**, "CausNVS: Autoregressive Multi-view Diffusion for Flexible 3D Novel View Synthesis". [![arXiv](https://img.shields.io/badge/arXiv-2509.06579-b31b1b.svg)](https://arxiv.org/abs/2509.06579) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://kxhit.github.io/CausNVS.html)
- **SEVA**, "Stable Virtual Camera: Generative View Synthesis with Diffusion Models". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://arxiv.org/abs/2503.14489) [![arXiv](https://img.shields.io/badge/arXiv-2503.14489-b31b1b.svg)](https://arxiv.org/abs/2503.14489) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://stable-virtual-camera.github.io/)
- **GEN3C**, "GEN3C: 3D-Informed World-Consistent Video Generation with Precise Camera Control". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Ren_GEN3C_3D-Informed_World-Consistent_Video_Generation_with_Precise_Camera_Control_CVPR_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2503.03751-b31b1b.svg)](https://arxiv.org/abs/2503.03751) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/nv-tlabs/GEN3C)
- **MVGD**, "Zero-Shot Novel View and Depth Synthesis with Multi-View Geometric Diffusion". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Guizilini_Zero-Shot_Novel_View_and_Depth_Synthesis_with_Multi-View_Geometric_Diffusion_CVPR_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2501.18804-b31b1b.svg)](https://arxiv.org/abs/2501.18804) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://mvgd.github.io/)
- [⭐️] **ViewCrafter**, "ViewCrafter: Taming Video Diffusion Models for High-fidelity Novel View Synthesis". [![TPAMI 2025](https://img.shields.io/badge/TPAMI-2025-6f42c1.svg)](https://github.com/Drexubery/ViewCrafter) [![arXiv](https://img.shields.io/badge/arXiv-2409.02048-b31b1b.svg)](https://arxiv.org/abs/2409.02048) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://drexubery.github.io/ViewCrafter/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Drexubery/ViewCrafter)

### Video

- **PE-Field 4D**, "PE-Field 4D: Video Generation Models as Canvas". [![SIGGRAPH Asia 2026](https://img.shields.io/badge/SIGGRAPH_Asia-2026-6f42c1.svg)](https://arxiv.org/abs/2607.15667) [![arXiv](https://img.shields.io/badge/arXiv-2607.15667-b31b1b.svg)](https://arxiv.org/abs/2607.15667) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/MTLab/PE-Field)
- **MV-Forcing**, "MV-Forcing: Long Multi-View Video Generation via 4D-Grounded Spatio-Temporal Self-Forcing". [![ECCV 2026](https://img.shields.io/badge/ECCV-2026-6f42c1.svg)](https://arxiv.org/abs/2607.05376) [![arXiv](https://img.shields.io/badge/arXiv-2607.05376-b31b1b.svg)](https://arxiv.org/abs/2607.05376) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://galfiebelman.github.io/mv-forcing/)

## 🏗️ Generation-Guided 3D Reconstruction

These methods reverse the information flow: a pretrained image or video generator supplies unobserved views, appearance priors, optimization guidance, or a learned decoder for reconstruction. Their central output is a reusable explicit or queryable 3D/4D representation, typically 3D Gaussians, a NeRF, a mesh, a point cloud, or a geometry field.

### Single Image

- **Scene Splatter**, "Scene Splatter: Momentum 3D Scene Generation from Single Image with Video Diffusion Model". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Zhang_Scene_Splatter_Momentum_3D_Scene_Generation_from_Single_Image_with_CVPR_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2504.02764-b31b1b.svg)](https://arxiv.org/abs/2504.02764)
- **WonderWorld**, "WonderWorld: Interactive 3D Scene Generation from a Single Image". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Yu_WonderWorld_Interactive_3D_Scene_Generation_from_a_Single_Image_CVPR_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2406.09394-b31b1b.svg)](https://arxiv.org/abs/2406.09394)
- **SGAM**, "Building a Virtual 3D World through Simultaneous Generation and Mapping". [![NeurIPS 2022](https://img.shields.io/badge/NeurIPS-2022-6f42c1.svg)](https://proceedings.neurips.cc/paper_files/paper/2022/hash/8ae9cf363ea625161f885b798c1f1f78-Abstract-Conference.html)

### Sparse Images

- **SPAR3S**, "Sparse Auto-Regressive Modeling for Scene Generation from Multi-View Images". [![arXiv](https://img.shields.io/badge/arXiv-2609.03931-b31b1b.svg)](https://arxiv.org/abs/2609.03931)
- **PixWorld**, "PixWorld: Unifying 3D Scene Generation and Reconstruction in Pixel Space". [![arXiv](https://img.shields.io/badge/arXiv-2607.05373-b31b1b.svg)](https://arxiv.org/abs/2607.05373) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://sensengao.github.io/PixWorld/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/SensenGao/PixWorld)
- **VidSplat**, "VidSplat: Gaussian Splatting Reconstruction with Geometry-Guided Video Diffusion Priors". [![SIGGRAPH 2026](https://img.shields.io/badge/SIGGRAPH-2026-6f42c1.svg)](https://arxiv.org/abs/2605.11424) [![arXiv](https://img.shields.io/badge/arXiv-2605.11424-b31b1b.svg)](https://arxiv.org/abs/2605.11424)
- **S2C-3D**, "Sparse-to-Complete: From Sparse Image Captures to Complete 3D Scenes". [![SIGGRAPH 2026](https://img.shields.io/badge/SIGGRAPH-2026-6f42c1.svg)](https://arxiv.org/abs/2605.05664) [![arXiv](https://img.shields.io/badge/arXiv-2605.05664-b31b1b.svg)](https://arxiv.org/abs/2605.05664) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://gapszju.github.io/S2C-3D/)
- **Free-Range Gaussians**, "Free-Range Gaussians: Non-Grid-Aligned Generative 3D Gaussian Reconstruction". [![ECCV 2026](https://img.shields.io/badge/ECCV-2026-6f42c1.svg)](https://arxiv.org/abs/2604.04874) [![arXiv](https://img.shields.io/badge/arXiv-2604.04874-b31b1b.svg)](https://arxiv.org/abs/2604.04874) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://free-range-gaussians.github.io/)
- **Gen3R**, "Gen3R: 3D Scene Generation Meets Feed-Forward Reconstruction". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://arxiv.org/abs/2601.04090) [![arXiv](https://img.shields.io/badge/arXiv-2601.04090-b31b1b.svg)](https://arxiv.org/abs/2601.04090) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://xdimlab.github.io/Gen3R/)
- **FaithFusion**, "FaithFusion: Harmonizing Reconstruction and Generation via Pixel-wise Information Gain". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://arxiv.org/abs/2511.21113) [![arXiv](https://img.shields.io/badge/arXiv-2511.21113-b31b1b.svg)](https://arxiv.org/abs/2511.21113) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/wangyuanbiubiubiu/FaithFusion)
- **Few-Glimpse NVS**, "Novel View Synthesis from A Few Glimpses via Test-Time Natural Video Completion". [![NeurIPS 2025](https://img.shields.io/badge/NeurIPS-2025-6f42c1.svg)](https://arxiv.org/abs/2511.17932) [![arXiv](https://img.shields.io/badge/arXiv-2511.17932-b31b1b.svg)](https://arxiv.org/abs/2511.17932)
- **LangScene-X**, "LangScene-X: Reconstruct Generalizable 3D Language-Embedded Scenes with TriMap Video Diffusion". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/ICCV2025/html/Liu_LangScene-X_Reconstruct_Generalizable_3D_Language-Embedded_Scenes_with_TriMap_Video_Diffusion_ICCV_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2507.02813-b31b1b.svg)](https://arxiv.org/abs/2507.02813) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://liuff19.github.io/LangScene-X/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/THU-SI/LangScene-X)
- **GS-GS**, "Generative Sparse-View Gaussian Splatting". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Kong_Generative_Sparse-View_Gaussian_Splatting_CVPR_2025_paper.html)
- **GenFusion**, "GenFusion: Closing the Loop between Reconstruction and Generation via Videos". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2503.21219) [![arXiv](https://img.shields.io/badge/arXiv-2503.21219-b31b1b.svg)](https://arxiv.org/abs/2503.21219) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Inception3D/GenFusion)
- **Scene-Grounding Guidance**, "Taming Video Diffusion Prior with Scene-Grounding Guidance for 3D Gaussian Splatting from Sparse Inputs". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2503.05082) [![arXiv](https://img.shields.io/badge/arXiv-2503.05082-b31b1b.svg)](https://arxiv.org/abs/2503.05082)
- **ReconX**, "ReconX: Reconstruct Any Scene from Sparse Views with Video Diffusion Model". [![arXiv](https://img.shields.io/badge/arXiv-2408.16767-b31b1b.svg)](https://arxiv.org/abs/2408.16767)
- **CAT3D**, "CAT3D: Create Anything in 3D with Multi-View Diffusion Models". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://arxiv.org/abs/2405.10314) [![arXiv](https://img.shields.io/badge/arXiv-2405.10314-b31b1b.svg)](https://arxiv.org/abs/2405.10314) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://cat3d.github.io/)
- **ReconFusion**, "ReconFusion: 3D Reconstruction with Diffusion Priors". [![CVPR 2024](https://img.shields.io/badge/CVPR-2024-6f42c1.svg)](https://arxiv.org/abs/2312.02981) [![arXiv](https://img.shields.io/badge/arXiv-2312.02981-b31b1b.svg)](https://arxiv.org/abs/2312.02981) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://reconfusion.github.io/)

### Video

- **ViDAR**, "ViDAR: Video Diffusion-Aware 4D Reconstruction From Monocular Inputs". [![NeurIPS 2025](https://img.shields.io/badge/NeurIPS-2025-6f42c1.svg)](https://arxiv.org/abs/2506.18792) [![arXiv](https://img.shields.io/badge/arXiv-2506.18792-b31b1b.svg)](https://arxiv.org/abs/2506.18792) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://vidar-4d.github.io/)
- **Geo4D**, "Geo4D: Leveraging Video Generators for Geometric 4D Scene Reconstruction". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://arxiv.org/abs/2504.07961) [![arXiv](https://img.shields.io/badge/arXiv-2504.07961-b31b1b.svg)](https://arxiv.org/abs/2504.07961)
- **DreamDrive**, "DreamDrive: Generative 4D Scene Modeling from Street View Images". [![ICRA 2025](https://img.shields.io/badge/ICRA-2025-6f42c1.svg)](https://arxiv.org/abs/2501.00601) [![arXiv](https://img.shields.io/badge/arXiv-2501.00601-b31b1b.svg)](https://arxiv.org/abs/2501.00601) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/NVlabs/DreamDrive)
- **CAT4D**, "CAT4D: Create Anything in 4D with Multi-View Video Diffusion Models". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2411.18613) [![arXiv](https://img.shields.io/badge/arXiv-2411.18613-b31b1b.svg)](https://arxiv.org/abs/2411.18613) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://cat-4d.github.io/)
- **DriveDreamer4D**, "DriveDreamer4D: World Models Are Effective Data Machines for 4D Driving Scene Representation". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2410.13571) [![arXiv](https://img.shields.io/badge/arXiv-2410.13571-b31b1b.svg)](https://arxiv.org/abs/2410.13571)

### Text / Multimodal

- **Latent-to-4D**, "Beyond Pixels: From Video Priors to 4D Worlds". [![arXiv](https://img.shields.io/badge/arXiv-2608.10744-b31b1b.svg)](https://arxiv.org/abs/2608.10744)
- [⭐️] **HY-World 2.0**, "HY-World 2.0: A Multi-Modal World Model for Reconstructing, Generating, and Simulating 3D Worlds". [![arXiv](https://img.shields.io/badge/arXiv-2604.14268-b31b1b.svg)](https://arxiv.org/abs/2604.14268) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Tencent-Hunyuan/HY-World-2.0)
- **WorldGen**, "WorldGen: From Text to Traversable and Interactive 3D Worlds". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Wang_WorldGen_From_Text_to_Traversable_and_Interactive_3D_Worlds_CVPR_2026_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2511.16825-b31b1b.svg)](https://arxiv.org/abs/2511.16825)
- **FlashWorld**, "FlashWorld: High-quality 3D Scene Generation within Seconds". [![ICLR 2026](https://img.shields.io/badge/ICLR-2026-6f42c1.svg)](https://arxiv.org/abs/2510.13678) [![arXiv](https://img.shields.io/badge/arXiv-2510.13678-b31b1b.svg)](https://arxiv.org/abs/2510.13678) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/imlixinyang/FlashWorld)
- [⭐️] **Lyra**, "Lyra: Generative 3D Scene Reconstruction via Video Diffusion Model Self-Distillation". [![ICLR 2026](https://img.shields.io/badge/ICLR-2026-6f42c1.svg)](https://research.nvidia.com/labs/toronto-ai/lyra/) [![arXiv](https://img.shields.io/badge/arXiv-2509.19296-b31b1b.svg)](https://arxiv.org/abs/2509.19296) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/toronto-ai/lyra/)
- **Matrix-3D**, "Matrix-3D: Omnidirectional Explorable 3D World Generation". [![arXiv](https://img.shields.io/badge/arXiv-2508.08086-b31b1b.svg)](https://arxiv.org/abs/2508.08086) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://matrix-3d.github.io/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/SkyworkAI/Matrix-3D)
- **WorldExplorer**, "WorldExplorer: Towards Generating Fully Navigable 3D Scenes". [![SIGGRAPH Asia 2025](https://img.shields.io/badge/SIGGRAPH_Asia-2025-6f42c1.svg)](https://arxiv.org/abs/2506.01799) [![arXiv](https://img.shields.io/badge/arXiv-2506.01799-b31b1b.svg)](https://arxiv.org/abs/2506.01799) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://mschneider456.github.io/world-explorer/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/mschneider456/WorldExplorer)
- **GGS**, "Generative Gaussian Splatting: Generating 3D Scenes with Video Diffusion Priors". [![ICCV 2025](https://img.shields.io/badge/ICCV-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/ICCV2025/html/Schwarz_Generative_Gaussian_Splatting_Generating_3D_Scenes_with_Video_Diffusion_Priors_ICCV_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2503.13272-b31b1b.svg)](https://arxiv.org/abs/2503.13272) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://katjaschwarz.github.io/ggs/)
- **Director3D**, "Director3D: Real-World Camera Trajectory and 3D Scene Generation from Text". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://proceedings.neurips.cc/paper_files/paper/2024/hash/89566c18d5b3e9836e8e16fde010b41d-Abstract-Conference.html) [![arXiv](https://img.shields.io/badge/arXiv-2406.17601-b31b1b.svg)](https://arxiv.org/abs/2406.17601)
- **DreamScene360**, "DreamScene360: Unconstrained Text-to-3D Scene Generation with Panoramic Gaussian Splatting". [![ECCV 2024](https://img.shields.io/badge/ECCV-2024-6f42c1.svg)](https://dreamscene360.github.io/) [![arXiv](https://img.shields.io/badge/arXiv-2404.06903-b31b1b.svg)](https://arxiv.org/abs/2404.06903) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://dreamscene360.github.io/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/ShijieZhou-UCLA/DreamScene360)
- **LucidDreamer**, "LucidDreamer: Domain-Free Generation of 3D Gaussian Splatting Scenes". [![TVCG 2025](https://img.shields.io/badge/TVCG-2025-6f42c1.svg)](https://luciddreamer-cvlab.github.io/) [![arXiv](https://img.shields.io/badge/arXiv-2311.13384-b31b1b.svg)](https://arxiv.org/abs/2311.13384) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/luciddreamer-cvlab/LucidDreamer)
- **DMV3D**, "DMV3D: Denoising Multi-View Diffusion using 3D Large Reconstruction Model". [![ICLR 2024](https://img.shields.io/badge/ICLR-2024-6f42c1.svg)](https://arxiv.org/abs/2311.09217) [![arXiv](https://img.shields.io/badge/arXiv-2311.09217-b31b1b.svg)](https://arxiv.org/abs/2311.09217) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://justimyhxu.github.io/projects/dmv3d/)
- **Text2Room**, "Text2Room: Extracting Textured 3D Meshes from 2D Text-to-Image Models". [![ICCV 2023](https://img.shields.io/badge/ICCV-2023-6f42c1.svg)](https://arxiv.org/abs/2303.11989) [![arXiv](https://img.shields.io/badge/arXiv-2303.11989-b31b1b.svg)](https://arxiv.org/abs/2303.11989) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://lukas-hoellein.github.io/text2room/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/lukasHoel/text2room)
- **DreamFusion**, "DreamFusion: Text-to-3D using 2D Diffusion". [![ICLR 2023](https://img.shields.io/badge/ICLR-2023-6f42c1.svg)](https://arxiv.org/abs/2209.14988) [![arXiv](https://img.shields.io/badge/arXiv-2209.14988-b31b1b.svg)](https://arxiv.org/abs/2209.14988) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://dreamfusion3d.github.io/)

## 🩹 Generative Refinement of 3D Reconstructions

These methods begin with an existing 3D reconstruction or its rendered buffers and then use an image or video generator to repair artifacts, restore detail, or synthesize under-observed content. Unlike the previous category, the generative model is introduced primarily **after** an initial scene has been reconstructed.

### Reconstructed Renderings

- **FixAnything**, "FixAnything: 3D-Consistent Rendering Refinement via Video Generative Priors". [![ECCV 2026](https://img.shields.io/badge/ECCV-2026-6f42c1.svg)](https://arxiv.org/abs/2608.23549) [![arXiv](https://img.shields.io/badge/arXiv-2608.23549-b31b1b.svg)](https://arxiv.org/abs/2608.23549) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://fix-anything.github.io/)
- **GaussVid**, "GaussVid: Sparse-View Gaussian Splatting with 3D-Aware Video Diffusion Priors". [![arXiv](https://img.shields.io/badge/arXiv-2608.21849-b31b1b.svg)](https://arxiv.org/abs/2608.21849) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Xinhui-99/GaussVid)
- **GaussFusion**, "GaussFusion: Improving 3D Reconstruction in the Wild with A Geometry-Informed Video Generator". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Zhu_GaussFusion_Improving_3D_Reconstruction_in_the_Wild_with_A_Geometry-Informed_CVPR_2026_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2603.25053-b31b1b.svg)](https://arxiv.org/abs/2603.25053) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.zhuliyuan.net/projects/GaussFusion/)
- **ArtiFixer**, "ArtiFixer: Enhancing and Extending 3D Reconstruction with Auto-Regressive Diffusion Models". [![arXiv](https://img.shields.io/badge/arXiv-2603.00492-b31b1b.svg)](https://arxiv.org/abs/2603.00492) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/sil/projects/artifixer)
- **GSFixer**, "GSFixer: Improving 3D Gaussian Splatting with Reference-Guided Video Diffusion Priors". [![arXiv](https://img.shields.io/badge/arXiv-2508.09667-b31b1b.svg)](https://arxiv.org/abs/2508.09667) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/GVCLab/GSFixer)
- [⭐️] **Difix3D+**, "Difix3D+: Improving 3D Reconstructions with Single-Step Diffusion Models". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://arxiv.org/abs/2503.01774) [![arXiv](https://img.shields.io/badge/arXiv-2503.01774-b31b1b.svg)](https://arxiv.org/abs/2503.01774) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/toronto-ai/difix3d/)
- **MVSplat360**, "MVSplat360: Feed-Forward 360 Scene Synthesis from Sparse Views". [![NeurIPS 2024](https://img.shields.io/badge/NeurIPS-2024-6f42c1.svg)](https://arxiv.org/abs/2411.04924) [![arXiv](https://img.shields.io/badge/arXiv-2411.04924-b31b1b.svg)](https://arxiv.org/abs/2411.04924) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://donydchen.github.io/mvsplat360/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/donydchen/mvsplat)

## 🧱 Foundation Models

These pretrained backbones and broadly reusable models provide video priors or geometric representations that can be adapted by generative-reconstruction systems. General-purpose frontier systems may also reappear here when their released model spans multiple downstream tasks. They are enabling foundations rather than core methods in the three task categories above.

### World / Video

- **World Labs — Atlas**, "Atlas: A World Model for Spatial Intelligence". [![Website](https://img.shields.io/badge/Website-Link-blue)](https://www.worldlabs.ai/blog/atlas) [![Access](https://img.shields.io/badge/Access-Early_Access-orange)](https://www.worldlabs.ai/blog/atlas)
- **JoyAI-Echo-1.5**, "Long-Horizon Audio-Visual Generation for Persistent Stories and Interactive Worlds". [![arXiv](https://img.shields.io/badge/arXiv-2608.23383-b31b1b.svg)](https://arxiv.org/abs/2608.23383) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://echo-team-joy-future-academy-jd.github.io/Echo-1.5-Page/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/jd-opensource/JoyAI-Echo)
- **MiniMax H3**, "MiniMax H3: An Open Model Breaking the Boundaries Between Tasks and Modalities". [![Website](https://img.shields.io/badge/Website-Link-blue)](https://www.minimax.io/blog/minimax-h3) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/MiniMax-AI/MiniMax-H3) [![Demo](https://img.shields.io/badge/Demo-Hailuo-orange)](https://hailuoai.video/)
- **LingBot-World 2.0**, "Infinite Worlds with Versatile Interactions". [![arXiv](https://img.shields.io/badge/arXiv-2607.07534-b31b1b.svg)](https://arxiv.org/abs/2607.07534) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Robbyant/lingbot-world-v2)
- **BiWM**, "BiWM: Advancing Open-Source Interactive Video World Models with Bidirectional Autoregression". [![arXiv](https://img.shields.io/badge/arXiv-2606.10135-b31b1b.svg)](https://arxiv.org/abs/2606.10135)
- **Cosmos 3**, "Cosmos 3: Omnimodal World Models for Physical AI". [![arXiv](https://img.shields.io/badge/arXiv-2606.02800-b31b1b.svg)](https://arxiv.org/abs/2606.02800) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://research.nvidia.com/labs/cosmos-lab/cosmos3) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/nvidia/cosmos)
- **SANA-WM**, "SANA-WM: Efficient Minute-Scale World Modeling with Hybrid Linear Diffusion Transformer". [![arXiv](https://img.shields.io/badge/arXiv-2605.15178-b31b1b.svg)](https://arxiv.org/abs/2605.15178) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://nvlabs.github.io/Sana/WM/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/NVlabs/Sana)
- **HY-World 2.0**, "HY-World 2.0: A Multi-Modal World Model for Reconstructing, Generating, and Simulating 3D Worlds". [![arXiv](https://img.shields.io/badge/arXiv-2604.14268-b31b1b.svg)](https://arxiv.org/abs/2604.14268) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Tencent-Hunyuan/HY-World-2.0)
- [⭐️] **LingBot-World**, "Advancing Open-source World Models". [![arXiv](https://img.shields.io/badge/arXiv-2601.20540-b31b1b.svg)](https://arxiv.org/abs/2601.20540) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Robbyant/lingbot-world)
- **LTX-2**, "LTX-2: Efficient Joint Audio-Visual Foundation Model". [![arXiv](https://img.shields.io/badge/arXiv-2601.03233-b31b1b.svg)](https://arxiv.org/abs/2601.03233) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://ltx.io/model/ltx-2) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Lightricks/LTX-2)
- [⭐️] **Yume-1.5**, "Yume-1.5: A Text-Controlled Interactive World Generation Model". [![arXiv](https://img.shields.io/badge/arXiv-2512.22096-b31b1b.svg)](https://arxiv.org/abs/2512.22096) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://stdstu12.github.io/YUME-Project/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/stdstu12/YUME)
- **Cosmos-Predict2.5**, "World Simulation with Video Foundation Models for Physical AI". [![arXiv](https://img.shields.io/badge/arXiv-2511.00062-b31b1b.svg)](https://arxiv.org/abs/2511.00062) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/nvidia-cosmos/cosmos-predict2.5)
- **Google DeepMind — Genie 3**, "Genie 3: A new frontier for world models". [![Website](https://img.shields.io/badge/Website-Link-blue)](https://deepmind.google/blog/genie-3-a-new-frontier-for-world-models/) [![Demo](https://img.shields.io/badge/Demo-Project_Genie-orange)](https://deepmind.google/models/genie/)
- **Wan**, "Wan: Open and Advanced Large-Scale Video Generative Models". [![arXiv](https://img.shields.io/badge/arXiv-2503.20314-b31b1b.svg)](https://arxiv.org/abs/2503.20314) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Wan-Video/Wan2.1)
- **Cosmos**, "Cosmos World Foundation Model Platform for Physical AI". [![arXiv](https://img.shields.io/badge/arXiv-2501.03575-b31b1b.svg)](https://arxiv.org/abs/2501.03575) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/nvidia/cosmos)
- **HunyuanVideo**, "HunyuanVideo: A Systematic Framework For Large Video Generative Models". [![arXiv](https://img.shields.io/badge/arXiv-2412.03603-b31b1b.svg)](https://arxiv.org/abs/2412.03603) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Tencent-Hunyuan/HunyuanVideo)
- **CogVideoX**, "CogVideoX: Text-to-Video Diffusion Models with An Expert Transformer". [![arXiv](https://img.shields.io/badge/arXiv-2408.06072-b31b1b.svg)](https://arxiv.org/abs/2408.06072) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/THUDM/CogVideo)
- **Stable Video Diffusion**, "Stable Video Diffusion: Scaling Latent Video Diffusion Models to Large Datasets". [![arXiv](https://img.shields.io/badge/arXiv-2311.15127-b31b1b.svg)](https://arxiv.org/abs/2311.15127) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Stability-AI/generative-models)

### Geometry / 3D

- **MoGe-3**, "MoGe-3: Fine-Detail Monocular Geometry Estimation with Self-Guided Sparse Volumetric Refinement". [![arXiv](https://img.shields.io/badge/arXiv-2607.17967-b31b1b.svg)](https://arxiv.org/abs/2607.17967)
- **Any4D**, "Any4D: Unified Feed-Forward Metric 4D Reconstruction". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2026/html/Karhade_Any4D_Unified_Feed-Forward_Metric_4D_Reconstruction_CVPR_2026_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2512.10935-b31b1b.svg)](https://arxiv.org/abs/2512.10935) [![Website](https://img.shields.io/badge/Website-Link-blue)](https://any-4d.github.io/) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/Any-4D/Any4D)
- **Depth Anything 3**, "Depth Anything 3: Recovering the Visual Space from Any Views". [![arXiv](https://img.shields.io/badge/arXiv-2511.10647-b31b1b.svg)](https://arxiv.org/abs/2511.10647)
- **π³**, "π³: Permutation-Equivariant Visual Geometry Learning". [![arXiv](https://img.shields.io/badge/arXiv-2507.13347-b31b1b.svg)](https://arxiv.org/abs/2507.13347)
- **VGGT**, "VGGT: Visual Geometry Grounded Transformer". [![CVPR 2025](https://img.shields.io/badge/CVPR-2025-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2025/html/Wang_VGGT_Visual_Geometry_Grounded_Transformer_CVPR_2025_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2503.11651-b31b1b.svg)](https://arxiv.org/abs/2503.11651) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/facebookresearch/vggt)
- **Long-LRM**, "Long-LRM: Long-sequence Large Reconstruction Model for Wide-coverage Gaussian Splats". [![arXiv](https://img.shields.io/badge/arXiv-2410.12781-b31b1b.svg)](https://arxiv.org/abs/2410.12781)
- **MASt3R**, "Grounding Image Matching in 3D with MASt3R". [![ECCV 2024](https://img.shields.io/badge/ECCV-2024-6f42c1.svg)](https://eccv.ecva.net/virtual/2024/poster/523) [![arXiv](https://img.shields.io/badge/arXiv-2406.09756-b31b1b.svg)](https://arxiv.org/abs/2406.09756) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/naver/mast3r)
- **Depth Anything V2**, "Depth Anything V2". [![arXiv](https://img.shields.io/badge/arXiv-2406.09414-b31b1b.svg)](https://arxiv.org/abs/2406.09414) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/DepthAnything/Depth-Anything-V2)
- **DUSt3R**, "DUSt3R: Geometric 3D Vision Made Easy". [![CVPR 2024](https://img.shields.io/badge/CVPR-2024-6f42c1.svg)](https://openaccess.thecvf.com/content/CVPR2024/html/Wang_DUSt3R_Geometric_3D_Vision_Made_Easy_CVPR_2024_paper.html) [![arXiv](https://img.shields.io/badge/arXiv-2312.14132-b31b1b.svg)](https://arxiv.org/abs/2312.14132) [![Code](https://img.shields.io/badge/Code-GitHub-green)](https://github.com/naver/dust3r)

## Surveys and Related Collections

- **Generative 3D Reconstruction Survey**, "A Survey of Recent Advances in Generative 3D Reconstruction". [![JCST 2025](https://img.shields.io/badge/JCST-2025-6f42c1.svg)](https://jcst.ict.ac.cn/article/doi/10.1007/s11390-025-5462-4)
- **3D and 4D World Modeling Survey**, "3D and 4D World Modeling: A Survey". [![arXiv](https://img.shields.io/badge/arXiv-2509.07996-b31b1b.svg)](https://arxiv.org/abs/2509.07996) [![Collection](https://img.shields.io/badge/Collection-GitHub-green)](https://github.com/worldbench/survey)
- **Immersive Video Survey**, "Generative AI for Immersive Video: Recent Advances and Future Opportunities". [![IJCAI 2025](https://img.shields.io/badge/IJCAI-2025-6f42c1.svg)](https://www.ijcai.org/proceedings/2025/1162.pdf)
- **3D Scene Generation Survey**, "3D Scene Generation: A Survey". [![arXiv](https://img.shields.io/badge/arXiv-2505.05474-b31b1b.svg)](https://arxiv.org/abs/2505.05474) [![Collection](https://img.shields.io/badge/Collection-GitHub-green)](https://github.com/hzxie/Awesome-3D-Scene-Generation)
- **Multimodal Generative Models Survey**, "Simulating the Real World: A Unified Survey of Multimodal Generative Models". [![TPAMI 2026](https://img.shields.io/badge/TPAMI-2026-6f42c1.svg)](https://arxiv.org/abs/2503.04641) [![arXiv](https://img.shields.io/badge/arXiv-2503.04641-b31b1b.svg)](https://arxiv.org/abs/2503.04641) [![Collection](https://img.shields.io/badge/Collection-GitHub-green)](https://github.com/ALEEEHU/World-Simulator)

## Contributing

Contributions of papers, code releases, project pages, corrected venue information, and new categories are very welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request. Automated contributors must also follow [AGENTS.md](AGENTS.md).

## Acknowledgements

The presentation style is inspired by [Awesome World Models](https://github.com/knightnemo/Awesome-World-Models). We thank the authors and maintainers of the papers, projects, and open-source models collected here.
