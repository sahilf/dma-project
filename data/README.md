# Data

This folder is where the Amazon Fine Food Reviews dataset goes. The file itself is too large to commit to GitHub and is excluded via `.gitignore`, so you need to download it once before running the notebook.

## Download

1. Open the dataset page on Kaggle: https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews/data
2. Download `Reviews.csv.zip`.
3. Place the zip file directly in this `data/` folder, i.e. `data/Reviews.csv.zip`.

No unzipping needed — `pandas.read_csv` reads the zip directly.

## Alternate placement

The notebook also accepts `Reviews.csv.zip` at the repo root. It checks `data/Reviews.csv.zip` first and falls back to the root, so either location works.
