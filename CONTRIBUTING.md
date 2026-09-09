# Contributing

Thank you for helping improve Awesome Generative Reconstruction.

## Inclusion checklist

A core submission should satisfy all of the following:

- It is a research paper, technical report, or clearly documented research system.
- It combines a learned generative model or prior with a 3D/4D reconstruction process or persistent geometric scene state.
- Generation and reconstruction interact through conditioning, denoising, loss, distillation, shared latent space, or feedback.
- A primary source is publicly accessible.
- The proposed description is factual, concise, and does not copy the abstract verbatim.

Pure video generation, pure reconstruction, generic camera control, geometry estimation, and benchmark papers belong under **Adjacent Enablers** unless the submission explains a stronger coupling.

## Pull request format

Please add one entry in chronological order within the best-fitting primary pipeline category:

```markdown
- **YEAR — [Paper title](paper URL)** — One sentence explaining where generation and reconstruction interact. [Project](URL) · [Code](URL)
```

Also update an orthogonal table when the paper introduces a genuinely new input regime, representation, coupling strategy, dynamic setting, or efficiency mechanism. Do not duplicate the full bibliography entry across multiple primary categories.

## Link and status policy

- Prefer arXiv, conference proceedings, official project pages, and author repositories.
- Do not link to AI-generated summaries when a primary source is available.
- Mark code as public only when a usable repository is visible.
- Mark closed systems separately and state which technical details or access routes are unavailable.
- For efficiency claims, include hardware and end-to-end scope when known.

## Curation notes

Maintainers may move a submission between **Core**, **System**, and **Adjacent** as public information changes. Borderline cases should explain both the geometry path and the generator path in the pull request description.
