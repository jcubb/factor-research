# Factor Research Wiki

A distilled, cross-linked knowledge base on **equity, currency, and bond factor
models** — spanning the academic research and the practitioner risk-model
machinery: Fama–French, Betting Against Beta, the momentum family, the Barra
risk models, covariance estimation, factor-portfolio construction, and manager
evaluation.

**📖 Read it as a site:** https://jcubb.github.io/factor-research/

## What this is

25 research papers and practitioner notes, each distilled into a structured
article — an overview, key results (with tables and equations), practical
implications, and cross-links to related work. Three on-ramp pages make it
learnable from scratch rather than just a reference:

- **[Start Here](wiki/start-here.md)** — a staged reading path, from mathematical
  intuition to advanced methods.
- **[Glossary](wiki/glossary.md)** — plain-language definitions of the terms used
  throughout.
- **[Index](wiki/index.md)** — the full topic map and cross-cutting themes.

## How it was built

This is a *Karpathy-style* LLM knowledge base: source papers are read and
distilled by a large language model into the wiki articles, which are then
maintained and cross-linked as the corpus grows. The published site is built
from the Markdown in [`wiki/`](wiki/) with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/)
and deployed to GitHub Pages automatically on every push.

## Important notes

- **Source PDFs are not included.** The articles are original summaries; the
  underlying papers are third-party copyrighted works (some are vendor research
  marked "not for distribution"). Only the distilled wiki is published here —
  consult the cited originals for authoritative detail.
- **Not investment advice.** This is a research reference compiled for
  educational use. Summaries may contain errors or simplifications; verify
  against the primary sources before relying on any result.

## License

The wiki content (everything in [`wiki/`](wiki/)) is licensed under
[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE) — you may
share and adapt it with attribution. This covers the original summaries only,
not the underlying copyrighted papers they describe.

## Local preview

```bash
pip install -r requirements.txt
mkdocs serve      # live-reload preview at http://127.0.0.1:8000
mkdocs build      # static site into ./site
```
