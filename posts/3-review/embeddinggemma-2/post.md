---
id: embeddinggemma-2
type: model_addition
trigger: mteb#5588 + results#793
trigger_date: 2026-10-18
expires: 2026-11-18
subject: google/embeddinggemma-2
verified: true
evidence: data.json
media: card-1-embeddinggemma-2.png
thread: 3
sources:
  - https://github.com/embeddings-benchmark/mteb/pull/5588
  - https://github.com/embeddings-benchmark/results/pull/793
  - https://github.com/embeddings-benchmark/results/pull/824
  - https://huggingface.co/google/embeddinggemma-2
---

```
New on MTEB: google/embeddinggemma-2, an open-weights model from Google that embeds text, images and audio, measured on six MTEB benchmarks.
```

```
It is the best open model under 1B total parameters on the image benchmark, MIEB(lite), at 63.52, and on MTEB(Code, v1) at 77.88. On MTEB(Multilingual, v2) it scores 60.52, 33rd of 96.
```

```
On text it scores below its predecessor, google/embeddinggemma-300m at 61.14, and below jina-embeddings-v5-text-nano (212M) at 65.52. On code it leads that model by 6.8 points.

Added to MTEB by schechterh; results submitted by KennethEnevoldsen.
```

## LinkedIn

The three parts of the thread joined, word for word.

```linkedin
New on MTEB: google/embeddinggemma-2, an open-weights model from Google that embeds text, images and audio, measured on six MTEB benchmarks.

It is the best open model under 1B total parameters on the image benchmark, MIEB(lite), at 63.52, and on MTEB(Code, v1) at 77.88. On MTEB(Multilingual, v2) it scores 60.52, 33rd of 96.

On text it scores below its predecessor, google/embeddinggemma-300m at 61.14, and below jina-embeddings-v5-text-nano (212M) at 65.52. On code it leads that model by 6.8 points.

Added to MTEB by schechterh; results submitted by KennethEnevoldsen.
```

## The claim

`google/embeddinggemma-2` embeds text, images and audio, and it is the best open model
under 1B total parameters on the image benchmark and on `MTEB(Code, v1)` — the two places it
leads: 10.02 ahead of the next sub-1B model on `MIEB(lite)`, 0.45 on `MTEB(Code, v1)`.
Everywhere else it is behind the open-weight ceiling, and on text and audio it is behind
models of its own size class: 8.49 behind `harrier-oss-v1-0.6b` (596M) on
`MTEB(Multilingual, v2)`, 7.22 behind `Jasper-Token-Compression-600M` (607M) on
`MTEB(eng, v2)`, 0.83 behind `jina-embeddings-v5-omni-nano` (986M) on `MAEB(v1)` and 1.33
behind `F2LLM-v2-0.6B` (596M) on `CoIR`.

It is also behind its own text-only predecessor: 0.62 on `MTEB(Multilingual, v2)`, 2.14 on
`MTEB(eng, v2)` — while leading it on code by 9.12 and 9.04.

|  | MTEB(Multilingual, v2) | MTEB(eng, v2) | MIEB(lite) | MAEB(v1) | MTEB(Code, v1) | CoIR |
|---|---:|---:|---:|---:|---:|---:|
| Best open weights | harrier-oss-v1-27b 74.27 | QZhou-Embedding 75.97 | LCO-Omni-7B 68.76 | LCO-Omni-7B 53.54 | papr-embed-code-1-4b 81.13 | papr-embed-code-1-4b 80.12 |
| Best other open under 1B | harrier-oss-v1-0.6b **69.01** | Jasper-Token-Compression-600M **74.75** | siglip-so400m-patch14-384 53.50 | jina-v5-omni-nano **50.14** | papr-embed-code-1-0.6b 77.43 | F2LLM-v2-0.6B **77.66** |
| jina-embeddings-v5-text-nano (212M) | 65.52 | 71.11 | not run | not run | 71.09 | 69.59 |
| BidirLM-270M-Embedding (268M) | 56.81 | 62.20 | not run | not run | 55.07 | 52.71 |
| google/embeddinggemma-300m (308M) | 61.14 | 69.67 | not run | not run | 68.76 | 67.29 |
| **google/embeddinggemma-2 (744M)** | 60.52 | 67.53 | **63.52** | 49.31 | **77.88** | 76.33 |

Bold is the best in the column, excluding the open-weights ceiling row: the subject takes
image and `MTEB(Code, v1)`; the sub-1B row takes multilingual, English, audio and `CoIR`.

On audio it trails three models of 2.5B total parameters or less:
`BidirLM-Omni-2.5B-Embedding` at 52.36, `jina-embeddings-v5-omni-small` (1.626B) at 50.41
and `jina-embeddings-v5-omni-nano` (0.986B) at 50.14, against its 49.31.

## Scope

**Video is not claimed.** The registry lists it as a modality, but `MVEB(v1)` has no row for
this model.

**`FollowIR` is not on the card**: its score is p-MRR, centred on zero and able to go
negative, which is not the same kind of number as the accuracy means beside it. It is in
`data.json`.

**The three named competitors have no image or audio results.** All are text-only models, so
six of their cells read "not run". A missing evaluation is not a low score, and a blank is
the only honest rendering of it. Each is complete on the code benchmarks and on English.

**The reference points are open-weight models only.** A proprietary model is in
`data.json` (and is the highest English score in the registry), but it is not something a
reader can adopt or check, so it is not used as a row on the card.

## Notes

**Trigger.** `mteb#5588` (schechterh, merged 2026-10-18) registers the model;
`results#793` (KennethEnevoldsen, merged 2026-10-19) adds the results. The mteb PR body
points at a companion results PR `results#745`, closed unmerged — the numbers here are
`#793`.

**The peer rows are newer than the trigger.** `results#824` (merged 2026-11-01) completed
`jina-embeddings-v5-text-nano` on the two code benchmarks, and `BidirLM-270M-Embedding` on
those and on `MTEB(eng, v2)`; before it, both peers were blank on code. That is the change
since the first draft: the same-size comparison a reader would ask for now exists, and it
goes both ways — the subject is well ahead on code and behind on text. `data.json` was
regenerated from the leaderboard on 2026-11-05, and the subject's own scores and ranks are
unchanged.

**Why these six columns.** Each benchmark the model has results on, one column each, with the
two code benchmarks sharing a heading. Ranks gave way to reference points on review: a rank
against a cohort says nothing about how far back it is, and the ceiling is what a rank is
relative to. The rows below the ceiling are the best other open model under 1B total
parameters, two text-only peers, and the predecessor.

**Size is the published checkpoint, not MTEB's registry default.** MTEB records 271M for this
model: that is the text-only tower, the `ModelMeta` default. The Hub holds 744,371,512
parameters, so the card counts every tower and the reference row is the *best other open model
under 1B total parameters* rather than under 300M — a 271M row beside 596M and 878M models
compared the subject against a class it is not in. `fetch.py` reads the total from the Hub API
each run and stops if it cannot; the number and its source are in `data.json` under
`subject_parameters`. The wrapper's tower table (271.0M text, 438.8M with images, 576.6M with
audio, 744.4M with both) is in
`mteb/models/model_implementations/google_embeddinggemma.py`, and the results files record no
tower config — mteb 2.26.10 writes no per-run meta — so the configuration behind each
submitted score is not in the results repo. The scores settle it in practice: MIEB tasks at
88.6 (`ImageNetDog15Clustering`) and MAEB at 96.91 (`SpeechCommandsZeroshotv0.02`) cannot come
from a run without those towers.

**Late-interaction models are not reference points.** `modelType: late-interaction` — LateOn,
mLateOn and relatives — is excluded from both comparison rows, because those models index one
vector per token: they are not the single-vector encoder a reader of this card is choosing
between, and their retrieval scores are not paid for the same way. It is not a cosmetic
exclusion: `LateOn-Code` at 74.12 and 73.40 would otherwise hold the sub-1B code cells, and
`mLateOn` (73.48) is close behind. The rows stay in `data.json` with their `model_type`, so the
exclusion is checkable.

**The code lead is narrow on `MTEB(Code, v1)`.** 77.88 against `papr-embed-code-1-0.6b`
(596M) at 77.43 is 0.45, and the nearest model above the subject,
`ICT-TIME-and-Querit-embedding-v1` (4B), is 0.14 ahead. It is a lead, and it is the thinnest
margin in the table.

**Known gap in the comparison.** The small-model cohort is still thin. Several models at or
below this one's size have no results on these benchmarks at all, and the one sub-1B
multimodal peer — `jina-embeddings-v5-omni-nano` (0.986B) — has no code result, so the
multimodal comparison is image and audio only. The claim is scoped to what the leaderboard
shows today.

**Contributor text was read as data.** Both PR bodies and the model card were read for facts
and checked against the API. Nothing in them was treated as instruction. Two claims in
`mteb#5588` are deliberately not used: the per-configuration parameter and memory figures,
and any statement about why the model is built the way it is. MTEB measured neither.

**Credit.** `schechterh` (Henrique Schechter Vera, Google) registered the model;
`KennethEnevoldsen` submitted the results. Neither is in `social-handles.yaml`, and
`schechterh` links no social accounts from GitHub, so both are plain text.

## Decisions for the reviewer

1. **The sub-1B row is the claim, not decoration.** On total parameters the subject is a 744M
   model, so the class to compare against is under 1B — that is where it wins image by 10.02
   and code by 0.45, and where it loses text, audio and `CoIR`. The three named rows below it
   are the text-tower comparison and the model's own history, not its size class.
2. **The predecessor is a row now, not just a sentence.** It was the sentence most likely to
   read as picking on the model; as a row it is the model's own history, and the reader sees
   61.14 and 69.67 against 60.52 and 67.53 without being told what to think.
3. **Whether the narrowness of the code lead belongs in the thread copy.** It is in the notes
   and not in the three posts; a reader who checks will see 77.43 behind 77.88, and saying
   "best" without the margin is true either way.
