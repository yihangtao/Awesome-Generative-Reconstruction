# Zotero Screening Log

This log records the initial screening of every PDF found in the local Zotero `storage` directory on **2026-09-09**. It exists to make the curation boundary auditable; local file paths and personal metadata are intentionally not published.

## Decision rules

- **Core** — generation and implicit or explicit geometry interact inside one method. This includes geometry-conditioned camera-controlled generation even when the primary output is video.
- **System** — matches the scope, but the public description is insufficient for scientific reproduction.
- **Adjacent** — a directly useful geometry, video, camera, memory, or evaluation component, but not a complete generative-reconstruction method.
- **Hold** — potentially in scope, but no stable public primary source was available at screening time.
- **Exclude** — unrelated to 3D/4D generative reconstruction or an internal derivative document.
- **Duplicate** — another Zotero attachment of an already screened paper.

## All 43 PDF attachments

| Zotero key | Work | Decision | Reason |
|---|---|---|---|
| `2M5VGQPI` | Geometry Forcing | Core | Aligns video-diffusion representations with a geometry foundation model to improve spatially consistent generation. |
| `2SDWYI5N` | Towards Realistic and Consistent Orbital Video Generation via 3D Foundation Priors | Core | Uses 3D foundation priors to constrain camera-controlled orbital video generation. |
| `5Q2AZRMH` | Long-LRM | Adjacent | Feed-forward 3DGS reconstruction only; useful as a downstream reconstructor. |
| `7KRF4PWC` | DreamFusion | Core | A frozen 2D diffusion prior directly optimizes a renderable NeRF through score distillation. |
| `83ZYP8YG` | Selective Visual Guidance for Robust Retrieval-Augmented Text-to-Image Generation | Exclude | Image-generation and visual-retrieval work without 3D reconstruction. |
| `8X6LQQCV` | CameraCtrl | Adjacent | Camera-controlled video-generation component without reconstruction. |
| `9MM4Z6Y2` | Wan | Adjacent | General video-generation backbone. |
| `CYCURTSX` | Unified Camera Positional Encoding for Controlled Video Generation | Adjacent | Camera-control mechanism without a reconstructed world. |
| `DRF5STBU` | ViewCrafter | Duplicate | Duplicate attachment of `ZHXC8ZKY`. |
| `EH534W6Q` | Cosmos 3 | Adjacent | Omnimodal world-model backbone, but not a generative-reconstruction pipeline in the sense used by this list. |
| `EU9G2E9E` | ArtiFixer | Core | Generative repair can directly extend views or be distilled back into an underlying 3D reconstruction. |
| `FSHKAKDX` | CineScene | Core | Reconstructed implicit 3D context directly conditions camera-controlled video generation. |
| `H3WCS2RY` | TinyGen | Exclude | Aerial tiny-object image generation without 3D reconstruction. |
| `JDUMVLQW` | CogVideoX | Adjacent | General video diffusion backbone. |
| `JJ9TVBCD` | VMem | Core | Uses a surfel-indexed spatial memory to preserve scene identity during interactive camera-controlled video generation. |
| `JLIJMSLK` | VBench | Adjacent | Video-generation benchmark. |
| `L8ZACBDZ` | Lyra | Core | Self-distills a video diffusion model into a 3DGS decoder and supports static 3D and dynamic 4D output. |
| `LAR2P835` | SANA-WM | Adjacent | Efficient long-horizon video world model; useful backbone but no coupled 3D reconstruction. |
| `LPNX757Y` | Difix3D+ | Core | Single-step diffusion repairs renders and supplies pseudo-supervision back to NeRF or 3DGS. |
| `MI5DYUX9` | SwiftCrafter | Hold | The local anonymous manuscript appears in scope, but no stable public paper or project identifier was available. |
| `PJZHM7WX` | PE-Field 4D | Core | Reconstructed geometry projects reference content into target coordinates for video-DiT generation. |
| `PQAK7J4T` | Frame Context Packing and Drift Prevention | Adjacent | Long-video context and drift-control mechanism without reconstruction. |
| `QCUIBCBC` | Video World Models with Long-term Spatial Memory | Core | Couples point-map geometry with episodic frame memory for long-horizon world generation. |
| `RQPGNH4N` | Stable Virtual Camera | Core | Performs camera-controlled generative view synthesis with an implicit spatial scene model. |
| `RRW8BQR8` | RoGe | Core | Jointly trains an implicit reconstruction model and a video generator through ray-queried geometric features. |
| `RYF8MPTT` | Towards Realistic and Consistent Orbital Video Generation via 3D Foundation Priors | Duplicate | Duplicate attachment of `2SDWYI5N`. |
| `SAHMZW5V` | ZeroNVS | Core | Uses a 3D-aware diffusion prior for camera-conditioned, 360-degree generative novel-view synthesis. |
| `SJI9QN2I` | MoGe-3 | Adjacent | Monocular geometry foundation model. |
| `SNVUL4EV` | Taming Video Diffusion Prior with Scene-Grounding Guidance | Core | Current 3DGS renders guide diffusion sampling, and generated sequences then supervise the reconstruction. |
| `TMFPDCZU` | π³ | Adjacent | Visual-geometry foundation model used for reconstruction features and geometric supervision. |
| `U26EWBE3` | VBench-2.0 | Adjacent | Video-generation evaluation suite. |
| `U5FXYGS5` | Box2Shape-Diff | Exclude | Box-conditioned remote-sensing image generation without 3D reconstruction. |
| `UKHLFB7N` | Atlas Research Report (Chinese) | System | Internal derivative report rather than a primary paper; the underlying Atlas system is included from World Labs' official page. |
| `VHF5IUMY` | VGGRPO | Core | Uses a latent 4D geometry reward to post-train world-consistent video generation. |
| `WXU6LMYS` | MV-Forcing | Core | An autoregressive reconstruction model supplies the 4D bridge between generated views. |
| `XAZD95WJ` | Video Pose Engine | Adjacent | Camera and depth annotation engine, not a generative-reconstruction method. |
| `Y37UR25W` | ArtiFixer | Duplicate | Duplicate attachment of `EU9G2E9E`. |
| `YB9HDEZN` | Lyra 2.0 | Core | Generates long geometry-indexed video and then reconstructs an explicit 3DGS or mesh. |
| `YNYPVKI5` | Internal `overall_zh` proposal | Exclude | Internal project document, not a published research work. |
| `ZBM77J9M` | PhyGS | Exclude | Physics-grounded radio-frequency field modeling, outside visual generative reconstruction. |
| `ZHXC8ZKY` | ViewCrafter | Core | Generates trajectory-controlled novel views from sparse geometry and can optimize a 3DGS from the generated evidence. |
| `ZQBAEJ5C` | LTX-2 | Adjacent | General audio-video foundation model. |
| `ZV8NXBZP` | Depth Anything 3 | Adjacent | General visual-geometry estimator; useful as a prior or reconstruction backend. |

## Notes on public curation

1. Duplicate PDFs are counted above because the request was to inspect every local attachment, but only one public bibliography entry is retained per work.
2. Internal reports and proposal drafts are not treated as publications. Their cited primary sources were checked separately.
3. The public README adds papers found through primary-source web research, including CAT3D, ReconX, GenFusion, Free-Range Gaussians, FlashWorld, WorldExplorer, Matrix-3D, PixWorld, SPAR3S, VidSplat, GaussVid, FixAnything, and others.
4. Camera-controlled video methods are included as implicit 3D modeling when geometry, reconstruction, or spatial memory materially constrains generation; generic video backbones remain adjacent.
