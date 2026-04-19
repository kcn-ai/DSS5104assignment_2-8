
# DSS5104 Assignment: Text Classification: From Classical NLP to Transformers

![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?logo=PyTorch&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?logo=googlecolab&color=525252)
![License](https://img.shields.io/badge/License-Academic-green.svg)

> Course project repository for **DSS5104** at the National University of Singapore (NUS). 
> This repository contains the source code, experimental setups, and performance benchmarks for text classification models on the AG News and IMDB datasets.

---

##  Table of Contents
- [Datasets](#-datasets)
- [Quickstart](#-quickstart)
- [Project Workflow](#-project-workflow)
- [Reproducibility](#-reproducing-results)
- [Key Results](#-key-results)
- [Report \& Documentation](#-report)

---

##  Datasets

This project evaluates the models on two standard Natural Language Processing (NLP) benchmarks. **Note that raw datasets are not included in this repository due to size limits.**

Please manually download the datasets and place them in the `data/` directory before running any notebooks.

### 1. Download the Data
* **[AG News](https://huggingface.co/datasets/fancyzhx/ag_news)**: 4-class topic classification benchmark.
* **[IMDB Reviews](https://ai.stanford.edu/~amaas/data/sentiment/)**: Binary sentiment classification benchmark.

### 2. Data Directory Setup
For convenience and exact reproducibility, we have pre-packaged the specific data splits used in our experiments. Please download them from our shared drive before running the notebooks.🔗 **[Download Datasets via Google Drive](https://drive.google.com/drive/folders/1pT62iwZx04x8XRso1KsL7fY_PKxXCb5k?usp=sharing)**

```text
├── data/
│   ├── agnews_train.csv    <-- Downloaded from Drive
│   ├── agnews_test.csv     <-- Downloaded from Drive
│   ├── IMDB_dataset.csv      <-- Downloaded from Drive
```

##  Quickstart

### 1. Clone the Repository

```bash
git clone [https://github.com/](https://github.com/)[your-username]/[your-repo-name].git
cd [your-repo-name]
````

### 2\. Environment Setup

We provide two methods for dependency management. **Conda is highly recommended** to ensure a fully isolated environment.

**Option A: Conda (Recommended)**

```bash
conda env create -f environment.yml
conda activate dss5104-group2-8
```

**Option B: pip**

```bash
pip install -r requirements.txt
```

-----

##  Project Workflow

Our pipeline is structured into two main phases: **Data Preprocessing** and **Model Training**. Please execute the Jupyter Notebooks in the following sequential order:

### Phase 1: Data Preprocessing & Cleaning 
Raw datasets are initially processed to handle noise, standardize text, and prepare the splits for model ingestion. 
* 📰 **AG News:** Run `clean_agnews.ipynb`
* 🎬 **IMDB:** Run `clean_imdb.ipynb`

### Phase 2: Model Training & Evaluation 
Once the clean datasets are generated, run the training notebooks sequentially. Our models are structured progressively from traditional machine learning baselines (Tier 1) to deep learning architectures (Tier 3).

* **AG News Pipeline:** `Tier1_agnews.ipynb` ➔ `agnews_fasttext.ipynb` ➔ `Tier3.ipynb`
* **IMDB Pipeline:** `Tier1_imdb.ipynb` ➔ `imdb_fasttext.ipynb` ➔ `Tier3.ipynb`

> ⚠️ **Hardware Note**: Tier 3 notebooks (Transformer models) require a GPU for reasonable training times. All our deep learning experiments were executed on **Google Colab (NVIDIA T4 GPU)**. Phase 1, Tier 1, and Tier 2 notebooks can be comfortably executed on a standard CPU.

-----

##  Reproducing Results

Rigorous evaluation is a core focus of this project. All experiments were conducted using three fixed random seeds (`42`, `123`, `456`) to ensure reproducibility.

  * The metrics reported below represent the **average** across these seeds. Standard deviations are documented in our final report.
  * The held-out test set was evaluated **strictly once**, only after all hyperparameter tuning was finalised via cross-validation on the validation set.

**Hyperparameter Search Space:**

| Model Algorithm | Parameter | Search Space |
|:---|:---|:---|
| **Logistic Regression / SVM** | `C` (Regularization) | `{0.1, 1, 10}` |
| **FastText** | `learning_rate` | `{0.1, 0.5, 1.0}` |
| | `epoch` | `{5, 10, 25}` |
| **DistilBERT / BERT-base** | `learning_rate` | `{1e-5, 2e-5, 5e-5}` |
| | `num_epochs` | `{3, 4, 5}` |

-----

##  Key Results


Performance comparison of traditional ML baselines versus deep learning models. Training times reflect the total duration across the full training sets.

| Model | AG News (F1) | IMDB (F1) | Train Time (AG / IMDB) |
|:---|:---:|:---:|:---:|
| **TF-IDF + LR** | 0.8992 | 0.8724 | 2.33s / 0.48s |
| **TF-IDF + SVM** | 0.9023 | 0.8659 | 0.27s / 0.54s |
| **FastText** | 0.8886 | 0.8458 | 1.12s / 15.69s |
| **DistilBERT** | 0.9278 | 0.8871 | 37.79s / 71.47s |
| **BERT-base** | **0.9311** | **0.9007** | 113.15s / 225.86s |

-----

##  Report

The comprehensive technical report, including detailed error analysis, literature review, and statistical significance testing, is available as a PDF document.

🔗 **[Read the Full Report Here](https://drive.google.com/file/d/1_XgWMZZazvc8TaqigjW10auEr-rMBcO-/view?usp=share_link)** 

-----

##  License & Disclaimer

This project was developed for academic purposes as part of the **DSS5104** module coursework. The code and models are provided as-is.

