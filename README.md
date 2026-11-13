# Reward Shaping

This repository is an ongoing project on the topic of reward shaping, with the goal of crafting educational resources to initiate people to the subject. Completed as part of the Reinforcement Learning course (INF8250AE) at Polytechnique Montréal, Fall 2026.

## Collaborators

- Benjamin Piché
- Vincent Lachapelle
- Laurence Corbeil
- Thibaud Chasteauneuf

## Repository structure

```
code/
  notebooks/   Jupyter notebooks (experiments, figures, explanations)
  utils/       Reusable Python code imported by the notebooks
reports/
  proposal/    Project proposal (NeurIPS template)
  final/       Final report (NeurIPS template)
```

## Setup

Requires Python 3.12.

```bash
git clone https://github.com/benjaminpiche8/reward-shaping.git
cd reward-shaping

python3.12 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt

# One-time, per clone: strip notebook outputs automatically on commit
nbstripout --install
```

> **Don't skip `nbstripout --install`.** Without it, notebook outputs and execution counts get committed and cause merge conflicts.

## Running the notebooks

```bash
source .venv/bin/activate
jupyter lab
```

Then open `code/notebooks/reward_shaping.ipynb` and select the `.venv` kernel.

**Convention:** put shared logic (environments, agents, shaping functions, plotting helpers) in `code/utils/` as `.py` files, and keep notebooks for calling that code and presenting results. Python files merge cleanly; notebooks don't.

When adding a dependency, pin its version in `requirements.txt`.

## Building the reports

Requires a LaTeX distribution (TeX Live, MacTeX or MiKTeX) with `latexmk`.

```bash
cd reports/final        # or reports/proposal
latexmk -pdf neurips_2026.tex
```

Clean build files with `latexmk -c`. Build artifacts and the compiled PDF are git-ignored.
