# E1 — persistent spatial memory on a physical robot: trial logs, protocol, analysis

Artifact for the paper **"Remembering Where Things Are: Measuring What Persistent Spatial Memory Is Worth — and What It Costs — on a Physical Robot"** (Chi Feng Chang, Calabi Inc.), on OpenReview at <https://openreview.net/forum?id=duDYrWhXmw>.

The system under test is RTSM, an open-source persistent spatial-memory layer: <https://github.com/calabi-inc/rtsm>. The agent that drove the robot (planner / navigator / monitor, the trial logger, the ESP32 firmware) is <https://github.com/Vipipi/rtsm-rc-car-agent>.

## What is here

| path | what |
|---|---|
| `E1_PROTOCOL.md` | the operator protocol the campaign ran under, with its amendment history (v2, adversarially reviewed 2026-08-06; three mid-campaign amendments dated in the text) |
| `CAMPAIGN_RUNBOOK.md` | the step-by-step operator guide used on trial evenings |
| `E1_DATA_SHEET.html` | the campaign data sheet |
| `demo2_data/t*.jsonl` | 78 campaign trial logs: the 60 pre-registered trials plus the voided runs and their redos, exactly as recorded. Each file is one trial: the plan record (candidates, chosen id, the model's stated reason, coordinate age), one record per control tick, and the final verdict. Voids are marked in the session manifests, never deleted. |
| `demo2_data/session_*/MANIFEST.md` | one per session (five layouts): the sheet-to-file mapping, tape readings, voids with causes, operator interventions and deviations |
| `demo2_data/results_frozen.json` | the frozen headline numbers (completion, time-to-arrival, the statistics) |
| `demo2_data/paper_analyses.json` | the pre-registered secondary analyses (per-object gradient, repeated pairs, decomposition, cost ledger) |
| `demo2_data/precampaign/`, `demo2_data/shakedown/` | the 32 + 12 runs before the pre-registered campaign; they informed the protocol and are not part of any reported number |
| `analyze_paper.py` | recomputes `paper_analyses.json` from the trial logs (standard library only): `python analyze_paper.py` |
| `make_figures.py` | regenerates the two results figures from the trial logs (needs matplotlib): `python make_figures.py` |

**Photos.** The evidentiary photograph of every trial stop (60 files, 131 MB) is in the release asset `photos.zip`, one folder per session, EXIF and other metadata removed losslessly (the image data is byte-identical to the originals). They are not in the repository because of their size.

## Provenance

The data trees were sealed when the campaign closed on 2026-09-04 and have not been edited since; this repository holds them byte for byte. The one-time scan, the memory arm's retrieval and the memoryless arm's masked retrieval are described in the paper's Sections 3 and 4; the trial logger that wrote these files is `agent/trial_logger.py` in the harness repository.

## Licence and citation

Data, documents and figures: [CC BY 4.0](LICENSE). The two scripts may also be used under the Apache License 2.0.

```bibtex
@inproceedings{chang2026remembering,
  title     = {Remembering Where Things Are: Measuring What Persistent Spatial Memory Is Worth, and What It Costs, on a Physical Robot},
  author    = {Chang, Chi Feng},
  booktitle = {2nd Workshop on Embodied Spatial Reasoning (ESR) at NeurIPS 2026},
  year      = {2026},
  url       = {https://openreview.net/forum?id=duDYrWhXmw}
}
```
