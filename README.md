# Detecting Suspicious Reviews on Amazon Fine Food Data

An unsupervised data mining project that detects fake or low-quality product reviews on the Amazon Fine Food corpus (~394k reviews, 1999–2012) by combining three independent signals — text-rating sentiment mismatch, network authority, and topic modeling. Showing that the signals converge on the same kind of review.

## Quick links

- **Start here:** [`main_notebook.ipynb`](main_notebook.ipynb) — the curated story of the project.
- **Project video (investor pitch):** [Watch on YouTube](https://www.youtube.com/watch?v=nge9tk2TOzk)
- **Dataset:** Amazon Fine Food Reviews ([Kaggle](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews/data)).
- **Checkpoints:** [`checkpoints/checkpoint_1.ipynb`](checkpoints/checkpoint_1.ipynb) · [`checkpoints/checkpoint_2.ipynb`](checkpoints/checkpoint_2.ipynb)

## Research questions

The project is organized around three connected questions, each attacking a different dimension of review authenticity:

1. **RQ1 Semantic alignment.** Can sentiment-rating mismatch flag fake reviews? Authentic reviews align text tone with the star rating; fake reviews tend to contradict themselves.
2. **RQ2 Social position.** Does a reviewer's place in the user-product network predict helpfulness better than how much they write? In other words, does network authority beat raw volume?
3. **RQ3 Latent themes.** What topics do reviews fall into, do those topics differ across user types, and do certain topics correlate with helpfulness?

The hypothesis tying them together: a fake review might be able to fake one of these dimensions, but faking all three consistently is much harder.

## Data

- **Source:** [Amazon Fine Food Reviews](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews/data) on Kaggle.
- **Placement:** download `Reviews.csv.zip` from Kaggle and place it either at the repo root or in a `data/` folder — the notebook handles either location.
- **Preprocessing:** deduplication on (UserId, ProfileName, Text), user segmentation by review count (Amateur / Active / Expert), sentence-level VADER sentiment scoring, and lemmatization plus domain-stopword removal for LDA. Full details in the notebook.

## How to reproduce

The project was developed locally with Python 3.13 in a virtual environment.

```bash
git clone <this repo URL>
cd dma-project
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Then download the dataset and open [`main_notebook.ipynb`](main_notebook.ipynb) in VS Code or Jupyter. Run the cells top to bottom.

The notebook also runs in Google Colab — upload the notebook, install the requirements with `!pip install -r requirements.txt`, and either upload `Reviews.csv.zip` to the working directory or mount Google Drive.

## Key dependencies

| Package | Version |
|---|---|
| Python | 3.13.3 |
| pandas | 3.0.2 |
| numpy | 2.4.4 |
| scikit-learn | 1.8.0 |
| networkx | 3.6.1 |
| nltk | 3.9.4 |
| matplotlib | 3.10.8 |
| seaborn | 0.13.2 |

Full pinned list in [`requirements.txt`](requirements.txt).

## Repo structure

```
.
├── main_notebook.ipynb
├── README.md
├── requirements.txt
├── .gitignore
├── checkpoints/
│   ├── checkpoint_1.ipynb
│   └── checkpoint_2.ipynb
└── data/
    └── README.md            # download instructions for Reviews.csv.zip
```

## Results summary

- **RQ1.** A three-signal consensus filter (Isolation Forest residual outlier + word-direction mismatch + not legitimately mixed) flagged **11,232 reviews (2.85%)** as anomalous — a rate that lines up with external estimates of fake-review prevalence.
- **RQ2.** Reviewer Hub Score correlated with helpfulness at **−0.08**, about **2× the magnitude** of Word Count's **+0.04**, but in the opposite direction from the naive expectation: the most central reviewers write *less* helpful reviews on average.
- **RQ3.** LDA produced **5 interpretable topics** (shopping, pet food, cooking, generic usage, coffee/tea). Topic distribution is strongly associated with helpfulness (chi-square statistic 468, p ≈ 4e-100).
- **Cross-method convergence.** The "generic usage" topic from LDA is **+10.1 percentage points more common** among RQ1 anomalies than normal reviews, and **−3.1 percentage points less common** among reviews that received helpful votes. Two independent methods, built from different data — sentiment-rating alignment and word co-occurrence — landed on the same kind of review as suspicious. That convergence is the project's strongest internal-validation finding.

Full analysis, plots, and discussion live in [`main_notebook.ipynb`](main_notebook.ipynb).
