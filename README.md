# Nuclear Recoil vs. Electronic Recoil Classification

A small applied-ML project that turns a signal-in-noise discrimination problem from dark matter
physics into an actual classification pipeline — and uses it to think concretely about the same
statistical reasoning as it shows up in AI alignment evaluation design.

## Background

This project follows on from my earlier paper, [*"Detecting Dark Matter: Exploring WIMP
Interactions and Background Noise Mitigation in the LUX-ZEPLIN Experiment"*](https://doi.org/10.58445/rars.1963), which analyzed
how the LUX-ZEPLIN (LZ) dark matter detector distinguishes candidate WIMP interactions (**nuclear
recoils**) from background events (**electronic recoils**) using two correlated signals:
scintillation light (S1) and ionization (S2).

That paper was a literature review and conceptual analysis — it did not involve building a
classifier. This notebook closes that gap: it builds a synthetic dataset that mimics the
real S1/S2 discrimination problem, trains two classifiers on it (logistic regression and a
gradient-boosted decision tree, the model family real dark matter collaborations actually use),
and evaluates them the way a physics search would — via ROC curves, precision-recall tradeoffs,
and purity-driven threshold selection.

## What's in this repo

- `nuclear_vs_electronic_recoil_classifier.ipynb` — the full analysis, with explanatory markdown
  throughout
- `requirements.txt` — dependencies to reproduce the notebook

## Why this is relevant beyond physics

The core problem here — extracting a rare, weak signal from a much larger background population,
under a decision threshold chosen by asymmetric error costs — is not unique to dark matter. It's
the same structural problem that shows up in:

- Interpretability work looking for rare anomalous behaviors (e.g., deception, reward hacking) in
  model outputs
- Choosing an operating point for a safety classifier, where false negatives and false positives
  have very different costs depending on what's being detected
- Interpreting null results: a well-characterized non-detection still meaningfully constrains a
  hypothesis space, as discussed in the physics paper with respect to how LZ's results rule out
  regions of supersymmetric parameter space

The notebook's final section discusses these parallels explicitly.

## Honesty about scope

The synthetic dataset is constructed to be *qualitatively representative* of real S1/S2
distributions (based on published physical intuition — nuclear recoils yield less ionization per
unit scintillation than electronic recoils) — it is not real LZ data, which isn't publicly
available at this granularity. This is a first, self-taught project in applying an ML classifier
to a problem structurally like the one in my physics research, not a claim of novel contribution
to either dark matter physics or machine learning.

## Running it

```bash
pip install -r requirements.txt
jupyter notebook nuclear_vs_electronic_recoil_classifier.ipynb
```

## Author

Seshivardhini Dulam
