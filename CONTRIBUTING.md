# Contributing

Thank you for helping improve **Awesome Generative Reconstruction**. Papers, code releases, project pages, corrected venue information, and constructive taxonomy suggestions are welcome.

## Inclusion checklist

A submission should satisfy the following:

- It is a research paper, technical report, or clearly documented research system.
- It couples generation with implicit or explicit 3D/4D reasoning.
- Geometry affects generation, or a generative prior affects reconstruction, through conditioning, memory, denoising, supervision, optimization, repair, or a shared representation.
- A primary source is publicly accessible.
- The description and metadata are factual and concise.

Pure video generation, image-only novel-view synthesis, conventional dense-view reconstruction, standalone camera control, geometry estimation, rendering-only repair, and benchmark papers are normally out of the core taxonomy. Exceptionally relevant NVS or rendering-repair methods may be proposed for the adjacent-baselines section.

## Choose one primary category

Please classify a work by its **primary output** and add it only once:

- **Camera-Controlled Video Generation:** the headline output is a spatially consistent roaming video along a requested camera path. Any 3D representation is an internal condition, latent, cache, memory, reward, or denoising constraint; a reusable 3D asset is not required.
- **Spatial Reconstruction:** the headline output is a persistent point cloud, NeRF, mesh, 3D Gaussian scene, or another explicit 3D asset that is directly predicted, generated, completed, or optimized.
- **Interactive & Dynamic Worlds:** the headline output is an action-responsive or real-time stream, a persistent interactive environment, an explicit 4D scene, or a real-to-sim world whose state evolves over time.

When a method spans multiple capabilities, choose the category that best matches the headline deliverable and explain the other capabilities in the pull request.

Within that category, use an existing, shortest applicable input heading: **Single Image**, **Sparse Images**, **Video**, **Text**, **Text / Multimodal**, or **Multimodal**. Use **Generalist** only when a method is explicitly designed for a variable number of distinct input regimes and no one regime is representative. Classify by the inputs available at inference time, not by training data or internally generated frames. Do not duplicate a paper across input headings.

## Entry format

Follow the badge-based style used throughout the README:

```markdown
- **Method**, "Full Paper Title". [![CVPR 2026](https://img.shields.io/badge/CVPR-2026-6f42c1.svg)](official venue URL) [![arXiv](https://img.shields.io/badge/arXiv-YYMM.NNNNN-b31b1b.svg)](arXiv URL) [![Website](https://img.shields.io/badge/Website-Link-blue)](project URL) [![Code](https://img.shields.io/badge/Code-GitHub-green)](code URL)
```

- Add a venue badge only after acceptance or publication can be verified through an official conference, proceedings, project, or author page.
- Omit badges for resources that do not exist.
- Prefer arXiv, official proceedings, official project pages, and author repositories.
- Do not link to generated summaries when a primary source is available.
- Use the authors' official method name and capitalization. Check the paper title first, then the abstract, project page, code repository, and BibTeX. If no method name exists, use a concise descriptive label without inventing an acronym.
- Keep the quoted paper title exact, including any method-name prefix used in the title.
- Order entries within every subsection by first public release date, newest first. Use the arXiv v1 date when available, otherwise the official release or publication date. Do not sort by revision date.
- Reserve ⭐️ for established, high-impact work with strong evidence of community adoption, such as substantial GitHub activity, broad downstream reuse, or field-shaping influence. Do not star a paper merely because it is recent or technically representative.

## Pull request checklist

- [ ] The paper is in scope.
- [ ] It appears in exactly one primary category.
- [ ] Its subsection reflects the method's inference-time input regime.
- [ ] The official method name, exact title, arXiv identifier, first-release date, venue, and links have been checked against primary sources.
- [ ] The venue badge links to a source that verifies the venue.
- [ ] The entry is positioned in reverse chronological order within its subsection.
- [ ] The pull request briefly explains how generation and 3D/4D reasoning interact.
- [ ] Existing Markdown layout and badge order are preserved.

Automated contributors must also follow [AGENTS.md](AGENTS.md).
