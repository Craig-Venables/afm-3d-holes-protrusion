# Template experiment — glass vs glass + ITO

This folder is a **copy-me template**. It is skipped at run time because the name starts with `_`.

## How to use it

1. Copy this whole folder up one level and rename it, for example:

   `Data/_template_glass_vs_ito`  →  `Data/glass_vs_ito`

2. Delete this README if you like, keep `baseline.txt`.

3. Put pre-levelled `.ibw` files in the new folder using these names:

```
Glass_0001.ibw          ← bare glass, replicate 1
Glass_0002.ibw          ← bare glass, replicate 2
Glass_ITO_0001.ibw      ← ITO on glass, replicate 1
Glass_ITO_0002.ibw      ← ITO on glass, replicate 2
```

4. Run the GUI or `python main.py`.

## What the analyser will do

| Filename | Sample group | Role |
|----------|--------------|------|
| `Glass_0001.ibw` | `Glass` | baseline |
| `Glass_0002.ibw` | `Glass` | baseline replicate |
| `Glass_ITO_0001.ibw` | `Glass_ITO` | coating on `Glass` |
| `Glass_ITO_0002.ibw` | `Glass_ITO` | coating replicate |

`baseline.txt` in this folder contains `Glass`, which pins the bare substrate if pairing is ever ambiguous.

Swap `Glass` / `ITO` for your own tokens (`Si`, `Quartz`, `PMMA`, …). Keep the pattern `Substrate_Layer_0001.ibw`.
