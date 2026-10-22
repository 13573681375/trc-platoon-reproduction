# Minimal reproducibility package

This author-prepared artifact reproduces the frozen core C1/C2 experiments of **Physical Information Budgets and Recursive Feasibility in Distributed Platoon Control**. Python3.12.14 and the pinned packages match the recorded environment. MATLAB is not required by this particular archived Python implementation. The code and data archive is publicly available at https://github.com/13573681375/trc-platoon-reproduction. No data DOI has been assigned or verified.

## Install and run

```text
python -m venv .venv
# Activate .venv for your operating system, then:
python -m pip install -r requirements.txt
python reproduce.py verify-data
python reproduce.py analyze
python reproduce.py check-c2
python reproduce.py simulate --case C1_A_all_links
python reproduce.py simulate --case C1_A_active_only
python reproduce.py simulate --case C2_first
# Optional: --case all runs all eight core cases.
# Optional directed certificate recheck, without redesign:
python reproduce.py certificate --period 3
```

All commands resolve paths from this repository. New outputs go to outputs/ by default; --output accepts a separate writable directory. Inputs under recorded_core/, archived_data/ and simulation/period_models/ are not overwritten. Failures produce an error/traceback record. The solver and exact initial/packet history stay fixed. CPU timing columns vary with hardware and are not bitwise-reproduction targets.

## Contents and scope

- Eight cases: three C1 A/B/C maneuver pairs and both C2 physical-history witnesses. cases.json fixes seed20261014, horizon10,180 samples, initial states and profile/service choices.
- Original period-specific NPZ terminal models/design records for P2–5. No gain, budget, objective, physical row or matrix is retuned. Original source and portable-source hashes are recorded; portability edits remove only old machine-specific dependency search paths.
- Eight complete compact step/event/cache/command records, configuration and initialization records. Original trajectory CSVs retain their hashes. The two large redundant per-case constraint NPZ arrays are not shipped: the unchanged engine regenerates full_constraint_rows.npz on a fresh run. The original complete arrays remain in the author archive.
-86 compact CSV files spanning the archived controller/communication comparisons, plus frozen reported summaries (including unfavorable results). provenance/csv_index.json lists all94 source CSV hashes; eight very large partial Ge-original-scene histories are expressly omitted from this minimal artifact.
- check-c2 rebuilds conditional and product-current initial programs and verifies the archived complete correction shifts/physical rows for both histories. analyze recomputes C1/C2 numerical metrics and actual billed frame/data resources directly from CSV/event logs.

This is **not** a complete recovery of Ge's original source algorithm or its23.14% sending rate. Those source gains/timing/energy limitations remain as reported. The minimal runner does not regenerate every optional ablation, five-follower redesign, desktop runtime benchmark or Ge synthesis search; their compact archived data/summaries are supplied for inspection, with no claim of fresh independent full-paper reproduction. Read the accompanying paper/supplement for the exact claim scope. Plotting scripts can derive new displays from the included data, but no new schematic is used as experimental evidence.

## Numerical comparison

verify-data uses only the Python standard library and compares every packaged input hash. analyze compares recomputed RMS/effort to stored values at1e-10 absolute tolerance. Fresh simulations compare deterministic metrics at1e-8 tolerance and bills exactly; complete row feasibility and tail checks remain in the unchanged engine. Floating timing and file timestamps are excluded. Stored certificates are inherited until the optional certificate command is actually executed. Verification logs identify which actions were run in preparing this delivery.
