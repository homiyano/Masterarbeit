# Speech-based detection of Alzheimer's disease: reproduction and transfer of NeuroXVocal

Code for the master's thesis *Benchmarking the NeuroXVocal Architecture on ADReSSo for Cross-Lingual and Cross-Task Transferability*. The model is NeuroXVocal ([paper](https://arxiv.org/abs/2502.10108), [original code](https://github.com/NNtamp/NeuroXVocal)): Whisper transcripts with DeBERTa, a Wav2Vec2 speech embedding and hand-crafted acoustic features, fused by a transformer.

## Notebooks

| Notebook | Thesis part |
|---|---|
| `01_reproduction_baseline_whisper_base` | Reproduction with the corrected pipeline (Whisper base) |
| `02_ablation_whisper_medium` | Ablation: Whisper medium |
| `03_ablation_whisper_prompt` | Ablation: Whisper with an initial prompt |
| `04_ablation_participant_only_with_overlap` | Ablation: participant speech only, overlap kept |
| `05_ablation_participant_only_without_overlap` | Ablation: participant speech only, overlap removed |
| `06_rq1_train_english_test_german` | RQ1: English → German |
| `07_rq1_train_german_test_english` | RQ1: German → English |
| `08_rq2_normalised_0_1` | RQ2: picture descriptions → verbal fluency, audio normalised to [0, 1] |
| `09_rq3_classical_denoising` | RQ3: classical noise reduction |
| `10_rq3_denoiser` | RQ3: Denoiser (Demucs) |

Run each notebook from the `notebooks/` folder. Its first cell creates `runs/<notebook name>/` and writes all outputs there.

## Setup

```
pip install -r requirements.txt
git clone https://github.com/thuml/LogME.git LogME                          # LEEP and NCE (06–08)
git clone https://github.com/facebookresearch/denoiser.git facebook-denoiser  # Denoiser (10)
```

`scalers/` holds the two feature scalers of the original NeuroXVocal release, which notebooks 01–05, 09 and 10 load.

## Data

No audio, transcripts or labels are included. Place the data under `data/` in the repository root. ADReSSo is available from DementiaBank (https://dementia.talkbank.org) under its data-use agreement; the German PROSPECT-AD recordings are not public.

## Licence

AGPL-3.0, as the original NeuroXVocal code (see `LICENSE`). LogME is MIT-licensed; the Denoiser is CC BY-NC 4.0.
