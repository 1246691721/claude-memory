---
name: gain-contribution-plot-style
description: "ggplot2 style settings for GAIN parent contribution bar plots — large bold fonts, 4:3 ratio, consistent color palette"
metadata: 
  node_type: memory
  type: project
  originSessionId: a4a9d2cd-2a27-43a5-a441-3268d170fffb
---

GAIN parent contribution plots use these settings:

- **Dimensions**: 12×9 inches (4:3), `ggsave(width=12, height=9)`
- **Title**: `size=22, face="bold"`
- **Subtitle**: `size=14, color="grey40"`
- **Axis labels (y)**: `size=15, face="bold"` (parent names in horizontal bar chart)
- **Axis text (x)**: `size=15`
- **Axis title (x)**: `size=17`
- **Base theme**: `theme_bw(base_size=18)`
- **Bar width**: `width=0.6`, no legend
- **Color**: `pal30` 30 distinct colors, same palette used across Heatmap, Ribbons, and Contribution for consistent parent-color mapping
- **Parent labels**: `G1_CT1669` ~ `G30_EY764` (maternal) or `G31_CML171` ~ `G60_L719` (paternal), from `/Users/apple/Downloads/ibd5.29/副本亲本标签.xlsx`
- **Horizontal layout**: `coord_flip()` for vertical parent list

Color palette (30 colors):
```
c("#E41A1C","#377EB8","#4DAF4A","#984EA3","#FF7F00","#FFFF33","#A65628","#F781BF","#999999","#66C2A5","#FC8D62","#8DA0CB","#E78AC3","#A6D854","#FFD92F","#E5C494","#B3B3B3","#1B9E77","#D95F02","#7570B3","#E7298A","#66A61E","#E6AB02","#A6761D","#666666","#8DD3C7","#BEBADA","#FB8072","#80B1D3","#FDB462")
```

**Why:** User found default fonts too small; these settings give clear legibility in presentations. The uniform palette across Heatmap/Ribbons/Contribution lets viewers cross-reference parent identity by color.

**How to apply:** Use this style for all GAIN parent contribution bar charts. Keep the same pal30 for heatmaps and ribbon plots to maintain color consistency across figures.
