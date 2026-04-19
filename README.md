# DSS5104assignment_2-8
Course project repository containing code, experiments, and report results.
---

## Quickstart

### 1. Clone the repository

```bash
git clone https://github.com/[your-username]/[your-repo-name].git
cd [your-repo-name]
```

### 2. Set up the environment

**Option A — Conda (recommended)**
```bash
conda env create -f environment.yml
conda activate dss5104
```

**Option B — pip**
```bash
pip install -r requirements.txt
```

### 3. Run the notebooks

Run notebooks in this order for each dataset:
clean_agnews.ipynb  →  Tier1_agnews.ipynb  →  agnews_fasttext.ipynb  →  Tier3.ipynb
clean_imdb.ipynb    →  Tier1_imdb.ipynb    →  imdb_fasttext.ipynb    →  Tier3.ipynb


> **Note**: Tier 3 notebooks require a GPU. We ran all experiments on Google Colab (T4 GPU). Tier 1 and Tier 2 notebooks run on CPU.

---

## Reproducing Results

All experiments use three fixed random seeds: `42`, `123`, `456`.  
Results are averaged across seeds; standard deviations are reported in the paper.

The test set was used **only once**, after all hyperparameter decisions were finalised on the validation set.

**Hyperparameter search ranges:**

| Model | Parameter | Range |
|---|---|---|
| LR / SVM | `C` | {0.1, 1, 10} |
| FastText | `learning_rate` | {0.1, 0.5, 1.0} |
| FastText | `epoch` | {5, 10, 25} |
| DistilBERT / BERT | `learning_rate` | {1e-5, 2e-5, 5e-5} |
| DistilBERT / BERT | `num_epochs` | {3, 4, 5} |

---

## Key Results

> Results will be updated upon completion of all experiments.

| Model | AG News F1 | IMDB F1 | Train Time |
|---|---|---|---|
| TF-IDF + LR | — | — | — |
| TF-IDF + SVM | — | — | — |
| FastText | — | — | — |
| DistilBERT | — | — | — |
| BERT-base | — | — | — |

---

## Requirements


Full dependency list: see `requirements.txt` and `environment.yml`.

---

## Report

The full report (PDF) is available at: `[链接，完成后补上]`

---

## License

This project is for academic purposes only as part of DSS5104 coursework at NUS.
