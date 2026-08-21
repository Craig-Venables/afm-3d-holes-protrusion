# Data folder — how experiments work

Drop **pre-levelled** Asylum / Igor `.ibw` files here. This folder is the only input the analyser needs.

## The one rule

**One subfolder = one experiment = one comparison.**

Scans in the same folder are compared with each other. Scans in different folders are processed separately and never mixed.

```
Data/
│
├── README.md                          ← you are here
├── _template_glass_vs_ito/            ← copy this folder (starts with _ so it is ignored)
│
├── new_device/                        ← a real experiment
│   ├── Sample_0001.ibw
│   └── Sample_0002.ibw
│
└── glass_vs_glass_ito/                ← another experiment
    ├── Glass_0001.ibw
    ├── Glass_0002.ibw
    ├── Glass_ITO_0001.ibw
    └── Glass_ITO_0002.ibw
```

Folders whose names start with `_` or `.` are **templates / notes** and are skipped.

Do **not** put `.ibw` files loose in `Data/` if you can help it. If you do, they are lumped into an experiment called `unnamed`.

---

## Filename recipe

```
<Substrate>_<Layer>_<replicate>.ibw
```

| Piece | Example | Meaning |
|-------|---------|---------|
| Substrate | `Glass`, `Si`, `Quartz`, `Sample` | Bare material (before the first `_`) |
| Layer | `ITO`, `PMMA` | Optional coating. Omit for a bare baseline. |
| Replicate | `0001`, `0002` | Repeat scan of the same sample. Stripped automatically. |

| File on disk | Grouped as | Role |
|--------------|------------|------|
| `Glass_0001.ibw` | `Glass` | bare substrate (baseline) |
| `Glass_0002.ibw` | `Glass` | second replicate of the baseline |
| `Glass_ITO_0001.ibw` | `Glass_ITO` | ITO on glass |
| `Si_PMMA_0001.ibw` | `Si_PMMA` | PMMA on silicon |
| `Sample_0001.ibw` | `Sample` | single-sample experiment |

Always put a `_` before the replicate number (`Sample_0001`, not `Sample0001`). Trailing digits are treated as the replicate id.

---

## New experiment in three steps

1. **Copy** `Data/_template_glass_vs_ito/` and rename the copy (no leading `_`).
2. **Replace** the notes in that folder with your `.ibw` files, using the names above.
3. **Run** `python launch_gui.py` (or `python main.py`). The log prints one line per file: which experiment it belongs to and which sample group it was parsed as.

Optional: a one-line `baseline.txt` naming the bare sample (`Glass`) if auto-pairing is ambiguous.

---

## What you get back

```
Output/Run_<timestamp>/
  <experiment_name>/
    <sample>/<replicate>/     ← per-scan CSVs and HTML plots
    comparison/               ← bars, boxes, substrate-vs-coating, threshold review
```

`.ibw` files stay local and are gitignored. Only the folder layout and these notes are committed.
