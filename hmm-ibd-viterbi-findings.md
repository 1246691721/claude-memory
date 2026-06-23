---
name: hmm-ibd-viterbi-findings
description: Core findings from HMM-IBD Viterbi vs max.col decoding comparison across Cubic and GAIN populations
metadata: 
  node_type: memory
  type: project
  originSessionId: a4a9d2cd-2a27-43a5-a441-3268d170fffb
---

## max.col vs Viterbi across 3 populations (100 pseudolines each)

| Population | max.col raw | Viterbi | Gain |
|---|---|---|---|
| Cubic 24-parent G=9 | 87.5% (BP=21) | 95.3% (BP=15) | +7.8% |
| GAIN Maternal 30-parent G=3 | 76.7% (BP=94) | 82.7% (BP=5) | +6.0% |
| GAIN Paternal 30-parent G=3 | 89.9% (BP=61) | 93.9% (BP=6) | +4.0% |

- max.col+cM_merge reduces BP but accuracy barely changes (direction-blind merge)
- 14% lines show Viterbi gain <1% — emission ambiguity bottleneck when many parents share same alleles
- Real GAIN data confirms: maternal Viterbi 65.7 BP/offspring, paternal 44.2 BP/offspring

## Key technical points
- Viterbi does NOT use Z matrix (Forward-Backward output) — it runs its own DP on emission + transition directly
- max.col uses Z (which already includes neighbor info) but picks argmax per-marker independently
- The difference: Viterbi enforces transition cost at decision time; max.col sees transition info via Z but decides per-row
- cM merge is blind to parent identity — merges short segments into longer neighbor, can hurt accuracy if direction wrong

## Data locations
- `/Users/apple/Downloads/ibd5.29/evaluation/boxplots/gain_100lines_cache.rds` — GAIN maternal
- `/Users/apple/Downloads/ibd5.29/evaluation/boxplots/gain_fuben_100lines_cache.rds` — GAIN paternal
- `/Users/apple/Downloads/ibd5.29/cubic复现/cubic_100lines_cache.rds` — Cubic
- Parent labels: G1-G30 maternal, G31-G60 paternal from `副本亲本标签.xlsx`

## Plotting
- Use pal30 for color consistency across Heatmap/Ribbons/Contribution
- Contribution: 12×9 (4:3), title 22pt bold, axis labels 15pt bold, coord_flip()
- See [[gain-contribution-plot-style]] for detailed ggplot2 settings

## Literature
- Forney (1973) 10.1109/PROC.1973.9030
- Rabiner (1989) 10.1109/5.18626
- Mott et al. (2000) 10.1073/pnas.230304397
- Zheng et al. (2015) 10.1534/genetics.115.177873
- Li et al. (2021) 10.1007/s00122-021-03919-7
