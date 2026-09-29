---
type: index
created: 2026-09-29
status: seed
tags: [atomic-notes, weather-ml]
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
---

# Atomic notes: AI weather forecasting models

One claim per note, decomposed from the NotebookLM synthesis
`09282026 - weather forecase models machine learning english`.

Every note is `status: seed` and `confidence: low`: the parent note is a
NotebookLM summary of papers, not a source read directly. Each note needs its
claim checked against the original paper before it becomes permanent.

## Data and reanalysis

- [[reanalysis-fuses-observations-with-numerical-models]]
- [[era5-covers-1940-to-present]]
- [[era5-is-the-base-training-set-of-global-weather-ai]]
- [[reanalysis-fills-gaps-over-oceans-and-poles]]
- [[anemoi-repackages-era5-as-zarr]]
- [[anemoi-serves-a-one-degree-half-terabyte-era5-subset]]
- [[anemoi-curates-65000-era5-variable-files]]

## The leading models

- [[fourcastnet-3-uses-spherical-neural-operators-with-wavelets]]
- [[fourcastnet-3-forecasts-60-days-in-under-four-minutes]]
- [[aifs-became-operational-in-february-2025]]
- [[aifs-uses-gnn-on-the-anemoi-framework]]
- [[graphcast-predicts-227-variables-on-a-multiscale-mesh]]
- [[weathernext-3-forecasts-from-live-satellite-observations]]

## Ensembles and stochasticity

- [[ensemble-forecasting-perturbs-initial-conditions-across-many-members]]
- [[atmospheric-chaos-bounds-deterministic-forecast-horizon]]
- [[ensembles-quantify-uncertainty-through-spread-skill-ratio]]
- [[latent-noise-injection-creates-ensemble-diversity]]
- [[gem-3-modulates-adaln-sequentially-with-delta-t-then-z]]
- [[fourcastnet-3-generates-ensembles-in-a-single-step]]

## Loss functions

- [[mse-training-drives-forecasts-toward-the-blurred-mean]]
- [[generative-models-preserve-storm-detail-better-than-regression]]
- [[fair-crps-rewards-accuracy-and-ensemble-spread]]
- [[crps-loss-weights-points-by-latitude]]
- [[spectral-crps-loss-preserves-the-energy-spectrum]]
- [[spectral-crps-tapers-high-wavenumbers-and-compresses-with-log]]
- [[the-composite-loss-adds-spatial-and-spectral-crps]]

## Physics and error accumulation

- [[autoregressive-rollout-accumulates-error]]
- [[physical-constraints-suppress-cumulative-error]]
- [[anomaly-space-modeling-reduces-long-range-drift]]
- [[conservation-laws-constrain-predicted-states]]
- [[physics-informed-architectures-align-with-earths-geometry]]

## Time-step management

- [[hierarchical-temporal-aggregation-reduces-iteration-count]]
- [[pangu-sub-models-cover-1h-3h-6h-and-24h]]
- [[gem-3-conditions-a-single-model-on-delta-t]]
- [[shared-time-step-weights-accumulate-spectral-noise]]

## GNN, CNN and the spatial representation

- [[cnn-expects-a-regular-lat-lon-grid]]
- [[gnn-represents-the-atmosphere-as-nodes-and-edges]]
- [[cnns-dominate-precipitation-nowcasting]]
- [[gnn-message-passing-covers-long-range-dependencies]]
- [[graph-construction-costs-more-than-convolution]]
- [[gated-gcn-with-performer-models-greenland-surface-melt]]
- [[gnn-surrogates-replace-expensive-climate-simulations]]

## Other architectures

- [[pangu-forecast-24-hours-in-1-4-seconds]]
- [[3dest-processes-non-uniform-3d-atmospheric-data]]
- [[pangu-forecast-typhoon-mawar-course-change-five-days-ahead]]
- [[dgmr-fuses-radar-history-with-gaussian-noise]]
- [[latent-diffusion-nowcasting-conditions-on-the-current-state]]

## Radar and satellite preprocessing

- [[radar-reflectivity-converts-to-rain-rate-by-z-r]]
- [[precipitation-pixels-are-mostly-zero]]
- [[clipping-sets-a-ceiling-on-extreme-precipitation]]
- [[low-correlation-pixels-get-filtered-out]]
- [[percentile-scaling-handles-heavy-tails-better-than-min-max]]
- [[sliding-window-sets-the-temporal-context]]
- [[channel-concatenation-fuses-satellite-and-radar]]
- [[rainy-period-oversampling-balances-the-dataset]]
