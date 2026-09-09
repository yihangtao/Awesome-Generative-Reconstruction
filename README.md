<div align="center">

# Awesome Generative Reconstruction

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Last Update](https://img.shields.io/badge/updated-September%202026-6c5ce7.svg)](#news--updates)
[![GitHub stars](https://img.shields.io/github/stars/yihangtao/Awesome-Generative-Reconstruction?style=social)](https://github.com/yihangtao/Awesome-Generative-Reconstruction)

<img src="assets/hero.png" alt="Sparse observations becoming a generated and reconstructed 3D world" width="100%">

**A curated map of methods that generate what is missing and reconstruct what is observed.**

</div>

Generative reconstruction studies how learned generative priors and 3D/4D reconstruction can be designed as one system. The goal is not merely to synthesize a plausible video, nor merely to fit visible measurements, but to recover a persistent, renderable world that remains faithful to observations while plausibly completing unseen geometry and appearance.

This list is **scene- and world-centric**. A work belongs to the core collection when a learned generator and a geometry-producing reconstruction path interact through conditioning, denoising, supervision, distillation, a shared representation, or an explicit feedback loop. Pure video generation, pure feed-forward geometry, and generic text-to-3D asset methods are not included in the core list; important ingredients are tracked separately under [Adjacent Enablers](#adjacent-enablers).

> **Status.** This is a living research index rather than a leaderboard. Paper summaries are deliberately short, and links to project pages or code are included only when publicly available. Atlas is covered as an industry system because no paper, code, weights, or unrestricted public demo had been released as of September 2026.

## News & Updates

- **2026-09-09** — Repository launched with a pipeline-centered taxonomy, orthogonal capability maps, and a screened local Zotero collection.
- **2026-09** — Added the newest unified and sparse-completion systems, including **Atlas**, **RoGe**, **SPAR3S**, **FixAnything**, and **Rethinking 3D Noise**.
- **2026-08** — Added **Beyond Pixels**, **GaussVid**, and other video-prior approaches for 3D/4D reconstruction.
- **2026-07** — Added **PixWorld**, **PE-Field 4D**, **MV-Forcing**, and **VGGRPO**.

## Overview

- [Definition and Scope](#definition-and-scope)
- [Pipeline Taxonomy](#pipeline-taxonomy)
  - [Generate, then Reconstruct](#1-generate--reconstruct)
  - [Reconstruct, then Generate](#2-reconstruct--generate)
  - [Closed-loop Generation and Reconstruction](#3-closed-loop-generation--reconstruction)
  - [Native or Unified 3D/4D Models](#4-native-or-unified-3d4d-models)
  - [Generative Repair and Distillation](#5-generative-repair-and-distillation)
- [Industry Systems](#industry-systems)
- [Orthogonal Views of the Field](#orthogonal-views-of-the-field)
- [Adjacent Enablers](#adjacent-enablers)
- [Datasets and Evaluation](#datasets-and-evaluation)
- [Contributing](#contributing)

## Definition and Scope

Let the evidence be a text prompt, one or more images, a video, or a partial 3D reconstruction. **Reconstruction** asks for a 3D/4D scene that explains the observed evidence. **Generation** models the conditional distribution of content that the evidence does not determine. **Generative reconstruction** combines both:

1. **Observation fidelity** — rendered views should agree with real input evidence where it is visible.
2. **Plausible completion** — unobserved or weakly constrained regions should be completed rather than left empty or corrupted.
3. **Persistent spatial output** — the result should be queryable beyond a fixed video, through a 3D/4D representation or a reconstruction-aware scene state.
4. **Algorithmic coupling** — generation and reconstruction must affect one another inside the method, rather than appearing as unrelated pre- and post-processing tools.

We use three curation labels:

- **Core** — satisfies the coupling criterion and reconstructs, maintains, or explicitly reasons through a persistent geometric scene.
- **System** — demonstrates the same scope, but lacks sufficient public technical detail for reproducibility.
- **Adjacent** — provides a key geometry, camera-control, memory, video, or evaluation component, but does not itself complete the full generative-reconstruction loop.

The collection prioritizes general scenes and explorable worlds. Object-centric work is included only when it establishes a broadly reused coupling pattern, such as score distillation or reconstruction-in-the-denoiser.

## Pipeline Taxonomy

The primary taxonomy assigns each method to the place where its main generation–reconstruction interaction occurs. The same papers are then compared along independent axes—input, representation, dynamics, training regime, and efficiency—in [Orthogonal Views of the Field](#orthogonal-views-of-the-field).

```text
observations ──► generation ──► reconstruction        Generate → Reconstruct
observations ──► reconstruction ──► generation        Reconstruct → Generate
                    ▲                  │
                    └──── feedback ────┘              Closed Loop
observations ──► shared 3D/4D generative model        Native / Unified
partial 3D ──► generative repair ──► improved 3D      Repair / Distillation
```

### 1. Generate → Reconstruct

These methods first synthesize missing views or camera-controlled videos, then lift the generated evidence into an explicit 3D/4D representation.

- **2026 — [Lyra 2.0: Explorable Generative 3D Worlds](https://arxiv.org/abs/2604.13036)** — Generates arbitrarily long, camera-controlled, 3D-consistent videos from one image using a geometry-indexed 3D cache and self-augmented history, then converts the video into 3DGS or a mesh with a feed-forward reconstructor. [Project](https://research.nvidia.com/labs/sil/lyra2/)
- **2026 — [HY-World 2.0: A Multi-Modal World Model for Reconstructing, Generating, and Simulating 3D Worlds](https://arxiv.org/abs/2604.14268)** — Supports text, single image, multi-view image, and video inputs; world generation expands a panorama along planned trajectories before WorldMirror 2.0 and 3DGS composition. [Code](https://github.com/Tencent-Hunyuan/HY-World-2.0)
- **2025 — [Matrix-3D: Omnidirectional Explorable 3D World Generation](https://arxiv.org/abs/2508.08086)** — Generates trajectory-guided panoramic videos and lifts them with either a feed-forward panorama reconstructor or 3DGS optimization. [Project](https://matrix-3d.github.io/) · [Code](https://github.com/SkyworkAI/Matrix-3D)
- **2025 — [WorldExplorer: Towards Generating Fully Navigable 3D Scenes](https://arxiv.org/abs/2506.01799)** — Starts from a text-generated 360° scaffold, autoregressively explores camera trajectories with video diffusion and scene memory, and fuses the generated views into 3DGS. [Project](https://mschneider456.github.io/world-explorer/) · [Code](https://github.com/mschneider456/WorldExplorer)
- **2025 — [Scene Splatter: Momentum 3D Scene Generation from Single Image with Video Diffusion Model](https://arxiv.org/abs/2504.02764)** — Alternates latent- and pixel-level momentum generation with Gaussian refinement to extend a single image into a consistent 3D scene. [Paper](https://openaccess.thecvf.com/content/CVPR2025/html/Zhang_Scene_Splatter_Momentum_3D_Scene_Generation_from_Single_Image_with_CVPR_2025_paper.html)
- **2025 — [DreamDrive: Generative 4D Scene Modeling from Street View Images](https://arxiv.org/abs/2501.00601)** — Uses video diffusion to create visual references from street-view imagery, then lifts them into a hybrid Gaussian 4D representation. [Code](https://github.com/NVlabs/DreamDrive)
- **2024/2025 — [DimensionX: Create Any 3D and 4D Scenes from a Single Image with Decoupled Video Diffusion](https://arxiv.org/abs/2411.04928)** — Decouples camera and motion control, generates multi-view videos, and reconstructs static 3DGS or deformable 4DGS. [Project](https://chenshuo20.github.io/DimensionX/) · [Code](https://github.com/wenqsun/DimensionX)
- **2024/2025 — [CAT4D: Create Anything in 4D with Multi-View Video Diffusion Models](https://arxiv.org/abs/2411.18613)** — Turns one monocular video into a camera–time grid of generated views and optimizes a deformable 3D Gaussian representation. [Project](https://cat-4d.github.io/)
- **2024 — [ReconX: Reconstruct Any Scene from Sparse Views with Video Diffusion Model](https://arxiv.org/abs/2408.16767)** — Conditions video diffusion on a global point cloud, then reconstructs a 3DGS with confidence-aware optimization.
- **2024 — [ViewCrafter: Taming Video Diffusion Models for High-fidelity Novel View Synthesis](https://arxiv.org/abs/2409.02048)** — Uses point-based 3D clues and iterative trajectory planning to generate novel-view videos; generated views can supervise a real-time-renderable 3DGS. [Project](https://drexubery.github.io/ViewCrafter/) · [Code](https://github.com/Drexubery/ViewCrafter)
- **2024 — [CAT3D: Create Anything in 3D with Multi-View Diffusion Models](https://arxiv.org/abs/2405.10314)** — Generates many pose-specified views from any number of real or generated images and feeds them to a robust Zip-NeRF or 3DGS reconstruction pipeline. [Project](https://cat3d.github.io/)
- **2023 — [Text2Room: Extracting Textured 3D Meshes from 2D Text-to-Image Models](https://arxiv.org/abs/2303.11989)** — Repeatedly inpaints RGB-D views and fuses them into a textured room-scale mesh, establishing an early generate-then-consolidate scene pipeline. [Project](https://lukas-hoellein.github.io/text2room/) · [Code](https://github.com/lukasHoel/text2room)

### 2. Reconstruct → Generate

These methods build or query geometry before generation, using reconstructed scene state as the condition, canvas, or bridge for a video model.

- **2026 — [RoGe: Novel View Synthesis via End-to-End Implicit Reconstruction and Generation](https://arxiv.org/abs/2609.02847)** — Ray-queries an implicit VGGT scene representation along a target trajectory and injects the resulting geometric features into a video diffusion model; reconstruction and generation are trained jointly. [Project](https://roge.github.io/)
- **2026 — [PE-Field 4D: Video Generation Models as Canvas](https://arxiv.org/abs/2607.15667)** — Reconstructs source geometry, projects reference content into target coordinates, and uses position-aligned context tokens to control a video DiT.
- **2026 — [MV-Forcing: Long Multi-View Video Generation via 4D-Grounded Spatio-Temporal Self-Forcing](https://arxiv.org/abs/2607.05376)** — Reconstructs each completed source view into a geometric bridge for the next view, then distills temporal and view-wise autoregression into a few-step student. [Project](https://galfiebelman.github.io/mv-forcing/)
- **2026 — [CineScene: Implicit 3D as Effective Scene Representation for Cinematic Video Generation](https://arxiv.org/abs/2602.06959)** — Encodes multiple static scene images with VGGT and concatenates implicit 3D context into a pretrained text-to-video model for large camera moves and dynamic subjects. [Project](https://karine-huang.github.io/CineScene/)
- **2024 — [MVSplat360: Feed-Forward 360 Scene Synthesis from Sparse Views](https://arxiv.org/abs/2411.04924)** — Renders feed-forward 3DGS features directly into Stable Video Diffusion's latent space, coupling geometric reconstruction with wide-baseline video synthesis. [Project](https://donydchen.github.io/mvsplat360/) · [Code](https://github.com/donydchen/mvsplat)

### 3. Closed-loop Generation ↔ Reconstruction

These methods explicitly alternate or back-propagate between a generative prior and a scene representation.

- **2026 — [VidSplat: Gaussian Splatting Reconstruction with Geometry-Guided Video Diffusion Priors](https://arxiv.org/abs/2605.11424)** — A training-free loop samples unexplored trajectories, guides denoising with current 3D renders, and refines 3DGS with confidence-weighted generated views.
- **2026 — [Sparse-to-Complete: From Sparse Image Captures to Complete 3D Scenes](https://arxiv.org/abs/2605.05664)** — Combines scene-adapted restoration, view-consistency-conditioned diffusion sampling, and coverage-aware trajectory planning for six-to-eight-view 3DGS. [Project](https://gapszju.github.io/S2C-3D/)
- **2025 — [Novel View Synthesis from A Few Glimpses via Test-Time Natural Video Completion](https://arxiv.org/abs/2511.17932)** — Alternates uncertainty-aware video completion and 3DGS reconstruction so generated views and geometry progressively correct each other.
- **2025 — [FaithFusion: Harmonizing Reconstruction and Generation via Pixel-wise Information Gain](https://arxiv.org/abs/2511.21113)** — Uses expected information gain to decide where diffusion should repair uncertain 3DGS renders and how strongly edits should be distilled back into the scene. [Code](https://github.com/wangyuanbiubiubiu/FaithFusion)
- **2025 — [GenFusion: Closing the Loop between Reconstruction and Generation via Videos](https://arxiv.org/abs/2503.21219)** — Trains video diffusion on artifact-prone RGB-D renders and cyclically adds restored frames back into scene optimization. [Code](https://github.com/Inception3D/GenFusion)
- **2025 — [Taming Video Diffusion Prior with Scene-Grounding Guidance for 3D Gaussian Splatting from Sparse Inputs](https://arxiv.org/abs/2503.05082)** — Uses reliable RGB and masks rendered from the current 3DGS to guide every denoising step, then optimizes the 3D scene with generated sequences. [Paper](https://openaccess.thecvf.com/content/CVPR2025/html/Zhong_Taming_Video_Diffusion_Prior_with_Scene-Grounding_Guidance_for_3D_Gaussian_CVPR_2025_paper.html)
- **2025 — [Generative Sparse-View Gaussian Splatting](https://openaccess.thecvf.com/content/CVPR2025/html/Kong_Generative_Sparse-View_Gaussian_Splatting_CVPR_2025_paper.html)** — Iteratively generates pseudo views with a geometry-aware image diffusion model and uses semantic correspondences to refine static or dynamic Gaussian scenes.
- **2023/2024 — [ReconFusion: 3D Reconstruction with Diffusion Priors](https://arxiv.org/abs/2312.02981)** — Regularizes per-scene NeRF reconstruction with samples from a pose-conditioned novel-view diffusion prior. [Project](https://reconfusion.github.io/)

### 4. Native or Unified 3D/4D Models

Here, geometry is generated inside the model, decoded during denoising, or learned in a shared generative representation rather than reconstructed only after RGB synthesis.

- **2026 — [SPAR3S: Sparse Auto-Regressive Modeling for Scene Generation from Multi-View Images](https://arxiv.org/abs/2609.03931)** — Learns a sparse voxel-aligned 3D latent from image supervision through differentiable Gaussian rendering, then autoregressively completes both voxel support and latent content.
- **2026 — [PixWorld: Unifying 3D Scene Generation and Reconstruction in Pixel Space](https://arxiv.org/abs/2607.05373)** — Uses one pixel-space diffusion transformer for reconstruction and generation, decoding pixel-aligned 3D Gaussians under differentiable rendering and geometry-feature supervision. [Project](https://sensengao.github.io/PixWorld/) · [Code](https://github.com/SensenGao/PixWorld)
- **2026 — [Beyond Pixels: From Video Priors to 4D Worlds](https://arxiv.org/abs/2608.10744)** — Learns a reusable decoder from video-diffusion latents to dynamic 4D geometry and transfers it across multiple video DiTs sharing a VAE family.
- **2026 — [Free-Range Gaussians: Non-Grid-Aligned Generative 3D Gaussian Reconstruction](https://arxiv.org/abs/2604.04874)** — Performs flow matching directly over unordered Gaussian parameters, treating sparse-view reconstruction itself as conditional 3D generation. [Project](https://free-range-gaussians.github.io/)
- **2026 — [Gen3R: 3D Scene Generation Meets Feed-Forward Reconstruction](https://arxiv.org/abs/2601.04090)** — Aligns VGGT-derived geometry latents with video appearance latents and jointly generates RGB, cameras, depth, and global point maps. [Project](https://xdimlab.github.io/Gen3R/)
- **2025/2026 — [FlashWorld: High-quality 3D Scene Generation within Seconds](https://arxiv.org/abs/2510.13678)** — Jointly pretrains multi-view-oriented RGB generation and 3D-oriented Gaussian prediction, then distills appearance quality from the former into the latter. [Code](https://github.com/imlixinyang/FlashWorld)
- **2025 — [Lyra: Generative 3D Scene Reconstruction via Video Diffusion Model Self-Distillation](https://arxiv.org/abs/2509.19296)** — Adds a 3DGS decoder beside a video diffusion RGB decoder and self-distills synthetic multi-view supervision, enabling feed-forward text/image-to-3D and video-to-4D. [Project](https://research.nvidia.com/labs/toronto-ai/lyra)
- **2023 — [DMV3D: Denoising Multi-View Diffusion using 3D Large Reconstruction Model](https://arxiv.org/abs/2311.09217)** — Places a triplane-NeRF reconstructor inside the multi-view denoising loop, using rendered reconstructions as the next denoising state and returning a clean 3D representation. [Project](https://justimyhxu.github.io/projects/dmv3d/)
- **2022 — [DreamFusion: Text-to-3D using 2D Diffusion](https://arxiv.org/abs/2209.14988)** — Introduces score distillation to optimize a NeRF from a frozen text-to-image diffusion prior, a foundational pattern for generative 3D optimization. [Project](https://dreamfusion3d.github.io/)

### 5. Generative Repair and Distillation

These methods begin with an incomplete or artifact-prone reconstruction and use generative models to enhance renderings, expand coverage, or provide pseudo-supervision back to 3D.

- **2026 — [FixAnything: 3D-Consistent Rendering Refinement via Video Generative Priors](https://arxiv.org/abs/2608.23549)** — Adapts a pretrained video generator with lightweight fine-tuning to refine novel-view render sequences from 3DGS, NeRF, meshes, or point clouds.
- **2026 — [GaussVid: Sparse-View Gaussian Splatting with 3D-Aware Video Diffusion Priors](https://arxiv.org/abs/2608.21849)** — Fine-tunes a camera-aware video restoration model with boundary anchors to repair sparse-view 3DGS renderings coherently across viewpoints. [Code](https://github.com/Xinhui-99/GaussVid)
- **2026 — [ArtiFixer: Enhancing and Extending 3D Reconstruction with Auto-Regressive Diffusion Models](https://arxiv.org/abs/2603.00492)** — Distills a bidirectional repair model into a causal generator that can produce hundreds of consistent views in one pass or supervise the underlying reconstruction. [Project](https://research.nvidia.com/labs/sil/projects/artifixer)
- **2025 — [GSFixer: Improving 3D Gaussian Splatting with Reference-Guided Video Diffusion Priors](https://arxiv.org/abs/2508.09667)** — Conditions video restoration on 2D semantics and VGGT geometry from the original sparse references, then uses repaired views to improve 3DGS. [Code](https://github.com/GVCLab/GSFixer)
- **2025 — [ViDAR: Video Diffusion-Aware 4D Reconstruction From Monocular Inputs](https://arxiv.org/abs/2506.18792)** — Personalizes a diffusion model to create pseudo multi-view supervision for dynamic Gaussians and uses diffusion-aware weighting plus camera optimization to suppress inconsistent edits. [Project](https://vidar-4d.github.io/)
- **2025 — [Difix3D+: Improving 3D Reconstructions with Single-Step Diffusion Models](https://arxiv.org/abs/2503.01774)** — Repairs novel-view artifacts with a one-step image diffusion model, distills corrected pseudo-views into NeRF/3DGS, and can also act as a neural enhancer at render time. [Project](https://research.nvidia.com/labs/toronto-ai/difix3d)

## Industry Systems

### Atlas — World Labs

**[Atlas: A World Model for Spatial Intelligence](https://www.worldlabs.ai/blog/atlas)** is a multimodal autoregressive diffusion transformer that organizes text, images, camera poses, and depth in a shared spatial context. World Labs demonstrates camera-controlled image/video generation, depth and point prediction, point clouds, and 3D Gaussian Splatting from one to many observations. Its most direct connection to generative reconstruction is the continuous transition between evidence-constrained reconstruction and generative completion: more observations reduce the amount the model must imagine.

As of **September 2026**, World Labs has not disclosed model size, training data scale, accelerator count, detailed 3DGS architecture, code, weights, or a public evaluation API. Access requires an early-access application, so Atlas should be treated as an influential system demonstration rather than a reproducible baseline.

## Orthogonal Views of the Field

The tables below intentionally cut across the pipeline taxonomy. They answer different questions without redefining overlapping categories.

### By input evidence

| Input regime | Representative core methods |
|---|---|
| Text only | DreamFusion, Text2Room, DMV3D, WorldExplorer, Matrix-3D, FlashWorld, PixWorld, HY-World 2.0 |
| Single image | CAT3D, ViewCrafter, DimensionX, Scene Splatter, DreamDrive, Lyra, Lyra 2.0, FlashWorld, Gen3R, VidSplat, HY-World 2.0 |
| Sparse multi-view images | ReconFusion, CAT3D, ReconX, MVSplat360, GuidedVD, GenFusion, GS-GS, GSFixer, Few Glimpses, RoGe, Free-Range Gaussians, PixWorld, SPAR3S |
| Monocular video | CAT4D, ViDAR, Geo-aware Lyra 4D mode, Beyond Pixels, HY-World 2.0 |
| Partial reconstruction / degraded renders | GenFusion, Difix3D+, GSFixer, FaithFusion, ArtiFixer, S2C-3D, GaussVid, FixAnything |
| Multimodal | CineScene, Matrix-3D, HY-World 2.0, PixWorld, Atlas |

### By persistent representation

| Representation | Representative core methods |
|---|---|
| 3D Gaussian Splatting | ViewCrafter, ReconX, MVSplat360, GenFusion, GuidedVD, GS-GS, Lyra, Lyra 2.0, Matrix-3D, FlashWorld, Free-Range Gaussians, PixWorld, HY-World 2.0 |
| Dynamic / deformable Gaussians | DreamDrive, DimensionX, CAT4D, ViDAR, Lyra, Beyond Pixels |
| NeRF / radiance field | DreamFusion, DMV3D, ReconFusion, CAT3D |
| Mesh | Text2Room, Lyra 2.0, HY-World 2.0, Atlas |
| Point, depth, ray, or implicit scene state | ViewCrafter, RoGe, CineScene, Gen3R, PE-Field 4D, MV-Forcing |
| Sparse voxel-aligned latent | SPAR3S |

### By coupling and optimization regime

| Regime | What is updated? | Representative methods |
|---|---|---|
| Per-scene optimization with frozen prior | Scene representation; generator stays frozen | DreamFusion, ReconFusion, GuidedVD, Few Glimpses, VidSplat |
| Scene-adapted generative repair | Lightweight or personalized generator plus scene | ViDAR, S2C-3D, GSFixer, GaussVid, FixAnything |
| Iterative alternating loop | Generated views and 3D supervision expand each other | Scene Splatter, GenFusion, GS-GS, FaithFusion, VidSplat |
| Feed-forward two-stage | Generator first, amortized reconstructor second | ReconX, Matrix-3D, Lyra 2.0, HY-World 2.0 |
| Joint / end-to-end | Reconstruction and generation learn together | MVSplat360, RoGe, Gen3R, PixWorld, DMV3D |
| Native 3D generative modeling | Distribution is defined over 3D latents or primitives | Free-Range Gaussians, FlashWorld, PixWorld, SPAR3S |

### By dynamics and scale

| Target | Representative methods |
|---|---|
| Static object or compact scene | DreamFusion, DMV3D, CAT3D, Free-Range Gaussians, SPAR3S |
| Static room / outdoor world | Text2Room, ViewCrafter, ReconX, Scene Splatter, Matrix-3D, WorldExplorer, Lyra 2.0, HY-World 2.0 |
| Dynamic 4D scene | DreamDrive, DimensionX, CAT4D, ViDAR, Lyra, Beyond Pixels |
| Long or open-ended exploration | WorldExplorer, Matrix-3D, Lyra 2.0, ArtiFixer, HY-World 2.0 |
| Driving-centric | DreamDrive, FaithFusion, Difix3D+, GS-GS |

### By efficiency strategy

| Strategy | Representative methods | Practical implication |
|---|---|---|
| Single-step / few-step diffusion | Difix3D+, FlashWorld, MV-Forcing, PixWorld | Reduces repeated denoising; may require distillation or dedicated training. |
| Feed-forward reconstruction | ReconX, MVSplat360, Lyra, Lyra 2.0, Matrix-3D, Gen3R, HY-World 2.0 | Avoids long per-scene 3D optimization after evidence is generated. |
| Training-free guidance | GuidedVD, Few Glimpses, VidSplat | Avoids model fine-tuning but usually retains per-scene reconstruction and repeated denoising. |
| Causal / autoregressive expansion | WorldExplorer, MV-Forcing, ArtiFixer, Lyra 2.0 | Extends spatial or temporal horizon while managing accumulated drift. |
| Sparse native representation | Free-Range Gaussians, SPAR3S | Spends model capacity on occupied 3D support rather than a dense grid. |

Reported headline speeds are not directly comparable: DMV3D reports roughly 30 seconds on one A100, CAT3D reports as little as one minute end to end, FlashWorld reports seconds and a 10–100× speed-up over prior pipelines, and the PixWorld project reports a distilled four-step model at about 0.6 seconds. Always check resolution, hardware, reconstruction backend, and whether preprocessing or per-scene optimization is included.

## Adjacent Enablers

These works are intentionally **not mixed into the core list**. They help build generative-reconstruction systems but do not by themselves provide the full coupling defined above.

### Geometry-aware video generation

- [Geometry Forcing: Marrying Video Diffusion and 3D Representation for Consistent World Modeling](https://arxiv.org/abs/2507.07982) — aligns Video DiT representations with a frozen geometry foundation model.
- [VGGRPO: Towards World-Consistent Video Generation with 4D Latent Reward](https://arxiv.org/abs/2603.26599) — post-trains video models with latent 4D geometry rewards without repeatedly decoding RGB.
- [Towards Realistic and Consistent Orbital Video Generation via 3D Foundation Priors](https://arxiv.org/abs/2604.12309) — uses 3D priors for camera-orbit video consistency.
- [ZeroNVS: Zero-Shot 360-Degree View Synthesis from a Single Image](https://arxiv.org/abs/2310.17994) — a 3D-aware single-image NVS diffusion prior and important predecessor to later scene reconstruction pipelines.

### Spatial memory and long-horizon video

- [Context as Memory: Scene-Consistent Interactive Long Video Generation with Memory Retrieval](https://arxiv.org/abs/2506.03141) — retrieves pose-overlapping historical frames as video-native memory. [Project](https://context-as-memory.github.io/)
- [VMem: Consistent Interactive Video Scene Generation with Surfel-Indexed View Memory](https://arxiv.org/abs/2506.18903) — indexes view memory with surfels for efficient revisitation. [Project](https://v-mem.github.io/)
- [Video World Models with Long-term Spatial Memory](https://arxiv.org/abs/2506.05284) — combines point-map spatial memory with sparse episodic frames. [Project](https://spmem.github.io/)
- [Frame Context Packing and Drift Prevention in Next-Frame-Prediction Video Diffusion Models](https://arxiv.org/abs/2504.12626) — packs long visual context and mitigates autoregressive drift.

### Geometry foundations and reconstructors

- [VGGT: Visual Geometry Grounded Transformer](https://arxiv.org/abs/2503.11651), [π³: Permutation-Equivariant Visual Geometry Learning](https://arxiv.org/abs/2507.13347), [Depth Anything 3](https://arxiv.org/abs/2511.10647), [MoGe-3](https://arxiv.org/abs/2607.17967), and [Long-LRM](https://arxiv.org/abs/2410.12781) provide geometry encoders, metrics, pseudo-labels, or scalable reconstruction backends.

### Video backbones, camera control, and evaluation

- Video foundations: [Wan](https://arxiv.org/abs/2503.20314), [CogVideoX](https://arxiv.org/abs/2408.06072), [LTX-2](https://arxiv.org/abs/2601.03233), [Cosmos 3](https://arxiv.org/abs/2606.02800), and [SANA-WM](https://arxiv.org/abs/2605.15178).
- Camera control: [CameraCtrl](https://arxiv.org/abs/2404.02101), [Unified Camera Positional Encoding](https://arxiv.org/abs/2512.07237), [Stable Virtual Camera](https://arxiv.org/abs/2503.14489), and [Video Pose Engine](https://research.nvidia.com/labs/toronto-ai/vipe/).
- Evaluation: [VBench](https://arxiv.org/abs/2311.17982) and [VBench-2.0](https://arxiv.org/abs/2503.21755).

## Datasets and Evaluation

### Common data regimes

- **Scene capture:** DL3DV-10K, RealEstate10K, ACID, ScanNet++, Tanks and Temples, Mip-NeRF 360, LLFF, and DTU.
- **Dynamic scenes:** DyCheck, Neural 3D Video, HyperNeRF, and synthetic multi-view video.
- **Driving:** Waymo Open, KITTI, nuScenes, and PandaSet.
- **Object-centric pretraining:** Objaverse, CO3D, GSO, and synthetic multi-view renders.

### What should be measured

| Axis | Typical evidence |
|---|---|
| Observed-view fidelity | held-out PSNR / SSIM / LPIPS; reference-view reprojection; identity and texture preservation |
| Novel-view realism | FID / FVD / KID; perceptual preference; artifact rate in extrapolated regions |
| Geometry | depth and point-map error; camera error; multi-view correspondence; rendered optical-flow consistency |
| Temporal / trajectory control | FVD, motion smoothness, pose adherence, loop-closure consistency, long-horizon drift |
| Completion quality | coverage, unseen-region plausibility, uncertainty calibration, and diversity under identical evidence |
| System efficiency | end-to-end wall time, denoising steps, preprocessing, per-scene optimization, peak VRAM, and render FPS |

A fair comparison should report the **full pipeline cost**, not only the video sampler or final renderer. It should also distinguish faithful reconstruction of observed regions from plausible—but unverified—completion of unobserved regions.

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request. A proposed core paper should make the generation–reconstruction coupling explicit in one sentence and link to a primary source.

The original Zotero screening, including retained, adjacent, duplicate, and excluded records, is documented in [docs/zotero-screening.md](docs/zotero-screening.md).

## Acknowledgements

The organization is inspired by [Awesome World Models](https://github.com/knightnemo/Awesome-World-Models), while using a narrower definition centered on the coupling between learned generation and reconstructive geometry.
