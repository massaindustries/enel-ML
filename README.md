# LACHESI: Results-only Research Record
<img width="550" height="337" alt="image" src="https://github.com/user-attachments/assets/39f0a511-c926-4eb8-ac1e-9709a5a71f85" />

This repository is a public, results-only record of an independent research
proof of concept on self-supervised bearing anomaly detection. It contains the
final report and the figures required to read it; operational code, training
pipelines, model implementation, configurations, and checkpoints are kept in a
private repository.

## LACHESI at a glance

LACHESI is the name of the evaluated V3 DualTower design. It separates two time scales:

- A fast, channel-independent transformer processes raw vibration windows to
  model fine temporal structure.
- A compact slow encoder processes snapshot features such as RMS, peak and
  temperature.
- A fusion layer combines the two representations, while a consecutive-window
  burst rule is used to reduce isolated alarms.

The work uses normal-operation data for training and treats reconstruction error
as an anomaly signal. It is not a production deployment or a validated
maintenance product.

## Benchmark results

| Public benchmark | Result reported in the final report |
| --- | --- |
| CWRU | Under a cross-load split, PatchTST V1 retained FPR 9.4% versus 41.5% for the FNN baseline; its separation gap was 8.30 versus 1.43. |
| KAIST | LACHESI detected degradation 77 hours before failure (62% of the measured lifetime) with a two-snapshot burst rule and zero validation FPR. |
| PRONOSTIA | From-scratch V3 achieved a one-hour early-warning margin on Bearing1_3; KAIST warm-start was transfer-neutral and zero-shot did not provide early warning. |
| XJTU-SY | A shared model alarmed before failure on 14 of 15 bearings (median AUROC 0.908); intra-condition leave-one-out calibration reached 15 of 15, with CV(EW%) = 0.442. |

See [the final report](results/final_report.pdf) for experimental protocols,
metrics, limitations and the corresponding figures.

## Scope and limitations

All results use public benchmark datasets. They are proof-of-concept evidence,
not a claim of production reliability or validation on Enel turbine data. In
particular, the study notes a remaining shared-threshold failure case in XJTU-SY
and limitations for spectral-band and narrow cyclostationary anomalies.

The Enel context and the cases discussed in the report were studied in part from
material presented during a masterclass by Ing. Lelli. This is independent
personal research by Francesco Massa; it is not an Enel deliverable and does not
constitute an endorsement by Enel.

## Rights

Copyright (c) 2026 Francesco Massa. All rights reserved.

No license is granted for the LACHESI operational code or implementation. The public
materials in this repository are provided for reading and citation of the
research results only. Referenced third-party datasets and libraries remain
subject to their respective licenses.
