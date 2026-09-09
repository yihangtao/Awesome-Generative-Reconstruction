# Contributing

Thank you for helping improve **Awesome Generative Reconstruction**. Papers, code releases, project pages, corrected venue information, and constructive taxonomy suggestions are welcome.

## Inclusion checklist

A submission should satisfy the following:

- It is a research paper, technical report, or clearly documented research system.
- It couples generation with implicit or explicit 3D/4D reasoning.
- Geometry affects generation, or a generative prior affects reconstruction, through conditioning, memory, denoising, supervision, optimization, repair, or a shared representation.
- A primary source is publicly accessible.
- The description and metadata are factual and concise.

Pure video generation, conventional dense-view reconstruction, standalone camera control, geometry estimation, and benchmark papers are normally out of scope unless the pull request explains their direct relevance.

## Choose one primary category

Please classify a work by its **primary output** and add it only once:

- **Camera-Controlled Generation (Implicit 3D Modeling):** outputs novel-view images or videos along a requested camera path; geometry acts as a condition, memory, latent scene state, or training signal.
- **Spatial Reconstruction:** performs reference-conditioned generative novel-view synthesis or outputs a persistent point cloud, NeRF, mesh, 3D Gaussian scene, or another explicit 3D asset.
- **Space-Time Simulation (Dynamic 4D Modeling):** outputs a controllable dynamic world, 4D representation, or real-to-sim environment.
- **Image Generation (Text-to-Image and Text-to-Panorama):** generates images or globally coherent 360° panoramas from text; reference-conditioned NVS belongs under Spatial Reconstruction.

When a method spans multiple capabilities, choose the category that best matches the headline deliverable and explain the other capabilities in the pull request.

## Entry format

Follow the badge-based style used throughout the README:

```markdown
- **Method**, "Full Paper Title". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](official venue URL) [![arXiv](https://img.shields.io/badge/arXiv-YYMM.NNNNN-b31b1b.svg)](arXiv URL) [![Website](https://img.shields.io/badge/Website-Link-blue)](project URL) [![Code](https://img.shields.io/badge/Code-GitHub-green)](code URL)
```

- Add a venue badge only after acceptance or publication can be verified through an official conference, proceedings, project, or author page.
- Omit badges for resources that do not exist.
- Prefer arXiv, official proceedings, official project pages, and author repositories.
- Do not link to generated summaries when a primary source is available.
- Reserve ⭐️ for established, high-impact work with strong evidence of community adoption, such as substantial GitHub activity, broad downstream reuse, or field-shaping influence. Do not star a paper merely because it is recent or technically representative.

## Pull request checklist

- [ ] The paper is in scope.
- [ ] It appears in exactly one primary category.
- [ ] The title, arXiv identifier, venue, and links have been checked.
- [ ] The venue badge links to a source that verifies the venue.
- [ ] The pull request briefly explains how generation and 3D/4D reasoning interact.
- [ ] Existing Markdown layout and badge order are preserved.
