# RefineAnything

**Multimodal Region-Specific Refinement for Perfect Local Details**

<a href="https://limuloo.github.io/RefineAnything/"><img src="https://img.shields.io/badge/Project-Page-blue" /></a>
<a href="https://arxiv.org/abs/2604.06870"><img src="https://img.shields.io/badge/arXiv-2604.06870-b31b1b" /></a>
<a href="https://github.com/limuloo/RefineAnything"><img src="https://img.shields.io/badge/GitHub-Code-black?logo=github" /></a>
<a href="https://huggingface.co/limuloo1999/RefineAnything"><img src="https://img.shields.io/badge/HuggingFace-Checkpoint-yellow?logo=huggingface" /></a>

RefineAnything targets **region-specific image refinement**: given an input image and a user-specified region (e.g., scribble mask or bounding box), it restores fine-grained details—text, logos, thin structures—while keeping **all non-edited pixels unchanged**. It supports both **reference-based** and **reference-free** refinement.

![Teaser](docs/static/teaser.png)
---

## News
- **2026-04-09** — Checkpoint released on Hugging Face: <https://huggingface.co/limuloo1999/RefineAnything>.
- **2026-04-09** — Release inference scripts.
- **2026-04-08** — Documentation skeleton added; **code release coming this month** (inference scripts, environment, and checkpoints will be linked here).
- **TBD** — Checkpoints and training/evaluation resources will be announced once finalized.

---

## Highlights

- **Region-accurate refinement** — Explicit region cues (scribbles or boxes) steer edits to the target area.
- **Reference-based and reference-free** — Optional reference image for guided local detail recovery.
- **Strict background preservation** — Edits stay inside the target region; training emphasizes seamless boundaries.

---

## Comparisons

![Reference-free qualitative comparisons](docs/static/qualitative_free.png)

![Reference-based qualitative comparisons](docs/static/qualitative_reference.png)

---

## Installation

```bash
pip install -r requirement.txt
```

---

## Quick Start

Only **three** things are required to run RefineAnything:

| Argument | Description |
|----------|-------------|
| `--input` | Source image |
| `--mask` | Binary mask (white = region to refine) |
| `--prompt` | What to refine |
| `--ref` | *(optional)* Reference image for guided refinement |

---

### Demo 1 — Reference-based Logo Refinement

Refine a blurry logo on a pillow using a reference image.

```bash
python scripts/fast_inference.py \
    --input  src/input1.png \
    --mask   src/mask1.png \
    --prompt "Refine the LOGO." \
    --ref    src/ref1.png \
    --output output/demo1.png
```

<table>
<tr>
<td align="center"><b>Input</b></td>
<td align="center"><b>Reference</b></td>
<td align="center"><b>Prompt</b></td>
</tr>
<tr>
<td><img src="docs/static/demo1_input_zoom.jpg" width="100%"></td>
<td><img src="src/ref1.png" width="100%"></td>
<td><i>"Refine the LOGO."</i></td>
</tr>
<tr>
<td align="center" colspan="3"><b>Output</b></td>
</tr>
<tr>
<td colspan="3"><img src="docs/static/demo1_output_zoom.jpg" width="100%"></td>
</tr>
</table>

---

### Demo 2 — Reference-free Text Refinement

Refine blurry Chinese text on a building sign — no reference image needed.

```bash
python scripts/fast_inference.py \
    --input  src/input2.png \
    --mask   src/mask2.png \
    --prompt "refine the text '鼎好商城'" \
    --output output/demo2.png
```

<table>
<tr>
<td align="center"><b>Input</b></td>
<td align="center"><b>Prompt</b></td>
</tr>
<tr>
<td><img src="docs/static/demo2_input_zoom.jpg" width="100%"></td>
<td><i>"refine the text '鼎好商城'"</i></td>
</tr>
<tr>
<td align="center" colspan="2"><b>Output</b></td>
</tr>
<tr>
<td colspan="2"><img src="docs/static/demo2_output_zoom.jpg" width="100%"></td>
</tr>
</table>

---

## Citation

If you use this repository, please cite:

```bibtex
@article{refineanything2026,
  title        = {RefineAnything: Multimodal Region-Specific Refinement for Perfect Local Details},
  author       = {TBD},
  year         = {2026},
  eprint       = {2604.06870},
  archivePrefix= {arXiv},
  primaryClass = {cs.CV},
  url          = {https://arxiv.org/abs/2604.06870},
}
```

---

## Acknowledgements and License

RefineAnything builds on ideas and components from the broader diffusion and multimodal ecosystem (including **Qwen2.5-VL**, **Qwen-Image**, and latent diffusion with **VAE** + **MMDiT**). Base model weights and API terms are subject to their respective licenses—**verify compliance before redistributing checkpoints or derived weights**.

Repository **code license**: *TBD* (e.g., Apache-2.0 or MIT)—set `LICENSE` when you open-source the implementation.
