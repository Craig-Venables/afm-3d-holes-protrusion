# Experiment: new_device

One folder = one experiment. Put every scan you want compared together in this folder.

## Files in this folder

| File | Sample group | Replicate | Notes |
|------|--------------|-----------|--------|
| `Sample20000.ibw` | `Sample` | `20000` | Trailing digits are treated as the replicate id |

Add more scans beside it:

```
Sample20000.ibw          ← already here
Sample20001.ibw          ← another replicate of the same sample
Sample_ITO_0001.ibw      ← optional coated variant
```

## After a run

Results land in:

`Output/Run_<timestamp>/new_device/`

- `sample/<replicate>/` — per-scan plots and CSVs
- `comparison/` — summary across every file in this folder
