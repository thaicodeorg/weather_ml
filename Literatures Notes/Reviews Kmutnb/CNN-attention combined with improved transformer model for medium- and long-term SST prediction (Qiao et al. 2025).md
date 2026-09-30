---
type: review
created: '2026-09-30'
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi]]"
---

## CNN-attention combined with improved transformer model for medium- and long-term SST prediction

## Source Information

Qiao, B., Y. Yang, Z. Tang, D. Han, G. Wu, 2025: CNN-attention combined with
improved transformer model for medium- and long-term SST prediction. *Ocean
Engineering*, 340, 122315. Immutable copy:
[[Sources/Markdown/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi]].
PDF: 20 sheets, printed folios equal sheet numbers (folio = sheet).

## Research Objective

To build a sea-surface-temperature forecasting model that keeps the Transformer's
long-range dependency modelling while fixing two known defects: boundary artefacts
from image-patch prediction, and poor extraction of local features. The
CNN-AT Transformer does this with a CNN-attention module for shallow-feature
extraction and fusion, convolutional layers embedded inside the Transformer
sub-layers, and progressively shrinking patch sizes
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=1|1. Introduction, p.1]]).

The target is medium- and long-range *monthly mean* SST â€” 6, 12 and 24 months
ahead â€” plus the derived El NiÃ±o index
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=7|4. Experiments, p.7]]).

## Problem

The paper positions itself against a specific architectural weakness rather than
against SST forecasting generally. A plain Transformer applied to gridded SST as
image patches produces boundary artefacts, does not constrain the spatial
continuity of the predicted SST field, and its error does not behave monotonically
with depth
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=4|3.3. Shallow feature extraction and fusion module, p.4]]).

More broadly, the framing is that existing data-driven SST predictors underperform
because they cannot capture the cross-ocean long-range correlations characteristic of
ENSO
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=13|4.4. Performance comparison, p.13]]).

## Gap Addressed in paper

Three claimed contributions, stated on page 1: the CNN-AT Transformer itself, the
shallow feature extraction and fusion module, and the improved Transformer with
convolutional layers embedded in its sub-layers â€” validated against a broad
baseline set spanning CNN, LSTM, ConvLSTM, PredRNN, MIM, TemproNet and
TransDtSt-Part
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=1|1. Introduction, p.1]]).

The ablation programme is the most substantial part of the paper: it isolates the
loss function, input length, pre-training, the shallow-feature module, the
convolutional FNN, patch size, and encoder depth
independently
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=9|4.3. Ablation study, p.9]]).

## Findings and conclusion

Against the strongest baselines in Table 6, CNN-AT Transformer records RMSE 0.5995
/ 0.6039 / 0.6225 at 6 / 12 / 24-month steps, beating TemproNet (0.6292 / 0.6423 /
0.7063), TransDtSt-Part (0.6402 / 0.6610 / 0.7115) and plain CNN (0.6315 / 0.6253 /
0.6444), with the best SSIM at every horizon
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=13|4.4.1. Medium- and long-term SST prediction, p.13]]).

Architecture findings are cleanly separated: RMSE and MAE fall by about 10% versus
the original Transformer, the original Transformer's error does *not* decrease
monotonically with depth whereas CNN-AT's does, and eight encoder layers is the
better choice
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=12|4.4. Performance comparison, p.12]]).

On ENSO, the paper is markedly more cautious than its own SST table implies. At
12 months the predicted Nino3.4 index tracks the observed variation but
"prediction ability for the peak values is insufficient"; at 24 months the
prediction effect is "relatively poor", and index correlation across models is
described as "relatively weak"
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=13|4.4.2. Medium- and long-term prediction of El NiÃ±o index, p.13]]).

The conclusion concedes the mechanism: accuracy declines at long lead times because
of error accumulation in multi-step prediction and the absence of explicit
constraints on ocean physics such as currents and thermohaline circulation
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=19|5. Conclusions, p.19]]).

## Limitations or Weakness

**The headline metric is nearly blind to lead time, and the paper does not notice.**
This is the central problem. Extending the forecast horizon from 6 to 24 months
changes CNN-AT Transformer's RMSE by 3.8% (0.5995 â†’ 0.6225). Plain CNN and
TemproNet behave the same way, and LSTM's RMSE *improves* with lead time
(0.9423 â†’ 0.9144 â†’ 0.9085)
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=13|4.4.1. Medium- and long-term SST prediction, p.13]]).
For any genuine forecast problem, error must grow with lead time. A field RMSE flat
to within a few percent across an 18-month extension, and non-monotone for some
baselines, indicates the metric is dominated by a component the model can predict
without any forecast skill â€” the mean state plus the seasonal cycle of monthly mean
SST. On that reading, a good chunk of the 0.5995 is climatological fidelity, not
prediction.

**The conclusion's central claim is contradicted by the paper's own Table 6.** The
authors state that accuracy "declines with increasing prediction steps"
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=19|5. Conclusions, p.19]]).
Table 6 shows no such decline for RMSE. The decline they observe is real but lives
in the *El NiÃ±o index correlation* (Table 7), not in the SST field error. These two
results sit in tension and the paper never reconciles them. The reconciliation is
diagnostic rather than damning: the field metric is insensitive while the index
metric is sensitive, which is exactly what one expects when the model reproduces the
climatological field while missing the evolution that drives the index.

**No climatological or persistence baseline.** Every row of Table 6 is a deep
learning model. With 24 months of monthly-mean SST as input and monthly means as
the target, "repeat the monthly climatology" and "persist the last 24 months" are
the two references that matter most, and neither is present
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=12|4.4. Performance comparison, p.12]]).
Without them there is no way to know whether any of these models â€” including the
proposed one â€” beats a trivial forecast. The flat-RMSE pattern above makes their
absence decisive rather than merely tidy.

**SSIM is a poor metric for this task.** SSIM of 0.9556 measures structural
similarity, which is intrinsically high for smooth, slowly varying gridded fields
and is maximised by a climatologically correct field. Reporting SSIM as a headline
result alongside RMSE invites the reader to read smoothness as skill.

**The metric scale is never stated.** Inputs are min-max standardized to [0, 1]
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=8|4.1.1. Data preprocessing, p.8]]),
yet reported RMSE values run 0.60â€“0.94. The paper never states whether metrics are
computed on inverse-transformed physical values (Â°C) or in normalized units. The
absolute numbers are therefore uninterpretable and cannot be compared against other
SST forecasting studies.

**Pre-training on CMIP creates a distributional bridge the test design leans on.**
The model pre-trains on CMIP5/CMIP6 historical output, with systematic bias against
observations removed by quantile mapping, then trains and tests on ERSST V5
(1850â€“1970 / 1971â€“1980 / 1981â€“2020)
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=8|4.1.1. Data preprocessing, p.8]]).
Quantile mapping forces CMIP output into the observational distribution before
training, which is a strong and appropriate correction, but it also means the
pre-training stage cannot be credited with learning forecast skill from CMIP's
longer record â€” much of what it learns is the observed climatology by construction.

**Spatial continuity is diagnosed but never enforced.** The paper correctly
identifies that a plain Transformer "does not design a constraint mechanism
specifically for the spatial continuity of SST field", and its answer is
architectural â€” convolutional layers to capture local structure
([[Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf#page=13|4.4. Performance comparison, p.13]]).
This is a proxy for the constraint, not the constraint. No smoothness penalty,
conservation check or spectral diagnostic is reported.

## Implication or suggestions on future research

This paper is a clean instance of the trap this seminar keeps meeting: a large
margin over ML baselines, obtained on a metric that barely responds to lead time, in
a setting where the trivial forecast is competitive. The decisive experiment is
cheap. Add two rows to Table 6 â€” monthly climatology, and persistence of the input
24 months â€” scored identically. If CNN-AT Transformer does not clear both by a
margin that grows with lead time, the model is a good climatology reproducer and
should be described as one. This is the same test that was missing in the
PÃ©rez-Aracila and Jung reviews, and the corpus is accumulating enough cases to make
it a standing requirement.

Note also the SNR problem in the ENSO result. If the field is largely climatological
and the index correlation at 24 months is weak, then any operational claim built on
this model should be about the *anomalous* field, not the total field. Reporting
RMSE on deseasonalized anomalies against a persistence-of-anomaly baseline would
separate the two effects cleanly, and the authors already have the index machinery
to do it.

The broader methodological point is that "medium- and long-term" is doing heavy
lifting. A 24-month-ahead forecast of monthly mean SST is a weak test of a
spatiotemporal model precisely because the answer is close to known. Sharpening the
evaluation â€” anomalies, extremes, regional boxes, event timing â€” is what would make
this class of architecture contest meaningful.

## How your search can fill gap

Re-run the lead-time sensitivity argument against the corpus's other
long-horizon papers. Several reviews already flag climatological-behaviour
concerns, and this paper gives a third, independent instance with a quantitative
signature: near-flat RMSE across a tripling of lead time, with some baselines
improving. That pattern is specific enough to be worth stating as a permanent note
and testing across the remaining batch.

For the ENSO side, the corpus contains the seasonal-to-subseasonal and
teleconnection material (the Li et al. circulation-classification review, the
Blunn et al. heatwave downscaling review) but no dedicated ENSO prediction paper.
Adding one would let the seminar ask whether the same architecture gains survive
once the target is genuinely unpredictable rather than climatologically dominated.

