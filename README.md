# ATML — Assignment 0 (PA0)

This repository contains the notebooks and code for the "Advance Topics in Machine Learning" assignment (PA0). The primary notebooks are `Task1.ipynb` ... `Task5.ipynb` and supporting data / output folders are included under `data/`, `outputs/`, `gan_outputs/`, and similar.

## Quick overview
- Task1.ipynb — ResNet-152 experiments (transfer learning, disabling skip connections, feature visualization).
- Task5.ipynb — CLIP modality-gap experiments (zero-shot on STL-10, alignment and visualization).
- data/ — local datasets (some large archives may be absent; see notes below).
- outputs/, clip_outputs/, gan_outputs/, vae_outputs/ — generated images, plots, and saved results.

## Requirements
A recommended Python environment (use a venv/conda):

- Python 3.8+ (3.11 tested)
- PyTorch (matching your CUDA / CPU setup)
- torchvision
- scikit-learn
- umap-learn
- matplotlib
- numpy
- scipy
- tqdm
- clip (OpenAI CLIP) — optional for Task5

Example quick install (adjust to your env):

```powershell
python -m pip install -r requirements.txt
# or install manually
python -m pip install torch torchvision scikit-learn umap-learn matplotlib numpy scipy tqdm
python -m pip install git+https://github.com/openai/CLIP.git
```

If you don't have GPU/CUDA, CPU-only PyTorch binaries are fine but slower.

## Running the notebooks
Open the repository folder in VS Code / Jupyter and run notebooks in order.

Suggested order:
1. `Task1.ipynb` — run cells top-to-bottom to reproduce ResNet experiments.
2. `Task5.ipynb` — runs CLIP analysis. Note: the STL-10 download may fail on some networks; the notebook includes a fallback downloader and instructions.

Notes on STL-10 (Task5):
- If automatic download fails due to network/firewall, download manually and place the archive at `./data/stl10_binary.tar.gz`.
- PowerShell one-liner to download (copy to a PowerShell prompt):

```powershell
Invoke-WebRequest -Uri https://ai.stanford.edu/~acoates/stl10/stl10_binary.tar.gz -OutFile .\data\stl10_binary.tar.gz
```

Task5 includes a small downloader cell (resumable attempt) and a `USE_CIFAR_FALLBACK` flag to use CIFAR-10 for quick experiments if you want to avoid long downloads.

## Reproducing experiments
- Training runs in the notebooks are short by default (a few epochs) to keep runtime reasonable. Adjust `num_epochs` and other hyperparameters if you want full-scale runs.
- Results and example outputs are saved to `outputs/` and `clip_outputs/` by the notebooks.

## Git / repo tips
- Large dataset files should generally not be committed. This repo's `.gitignore` ignores common large files and caches.
- To commit the README and .gitignore created here:

```powershell
git add README.md .gitignore
git commit -m "Add README and .gitignore"
git push origin master
```

## Contact / notes
If you want me to:
- add a `requirements.txt` file; or
- inline sample figures into a LaTeX report; or
- automatically switch Task5 notebook to CIFAR fallback when download fails — tell me which and I'll add it.

---

_Last updated: 2025-09-08_
