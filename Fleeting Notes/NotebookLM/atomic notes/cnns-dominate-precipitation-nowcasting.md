---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [cnn, nowcasting, convgru, dgmr]
---

# CNNs dominate short-term precipitation nowcasting

## Claim

For nowcasting under about six hours from radar and satellite imagery, the
convolutional family is the standard choice: ConvLSTM, ConvGRU as in DGMR, and
3D-UNet as in NowcastNet. The data arrives as an image sequence, which is
exactly what convolutions expect.

## Evidence

The parent note's selection guidance is stated as a rule of thumb: choose CNN
when the input is radar imagery, satellite photos, or a uniform 2D grid and the
task is local short-term rain movement; choose GNN for global or irregular-grid
problems. It attributes the success to pixel-level detail in rain motion
direction and intensity.

## Related

- [[gnn-represents-the-atmosphere-as-nodes-and-edges]]
- [[dgmr-fuses-radar-history-with-gaussian-noise]]
- [[cnn-expects-a-regular-lat-lon-grid]]
- [[channel-concatenation-fuses-satellite-and-radar]]
