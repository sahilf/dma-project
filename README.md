# Amazon Fine Food Reviews - Data Mining Project

## Project Overview

This project explores **Text Mining** and **Graph Mining** techniques on the Amazon Fine Food Reviews dataset. The primary objective is to investigate the depth of text mining through a purely analytical and data-driven lens, exploring what level of insight, patterns, and actionable results can be reached by relying predominantly on data mining core principles.

## Dataset Information

**Dataset Name:** Amazon Fine Food Reviews

**Source:** [Kaggle - Amazon Fine Food Reviews](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews/data)

**Description:** Collection of over 500,000 reviews covering consumer feedback on food products, ideal for studying the relationship between natural language and numerical satisfaction scores.

**Dataset Characteristics:**
- **Original Size:** 568,454 reviews
- **Cleaned Size:** 393,645 unique reviews
- **Unique Users:** 256,059
- **Unique Products:** 67,488
- **Time Span:** 1999-2012
- **Columns:** 10 (Text, Summary, Score, UserId, ProductId, Time, etc.)

## Key Features

### Data Mining Tasks
- **Text Mining:** Natural language analysis, bi-gram extraction, sentiment-score correlation
- **Graph Mining:** User-product bipartite graph construction
- **Anomaly Detection:** Identifying review manipulation and sentiment-rating disconnects
- **Frequent Itemsets:** Product relationship patterns

### Beyond-Course Techniques
- **Topic Modeling:** Latent Dirichlet Allocation (LDA) for automated theme discovery
- **Transformer-based Embeddings:** BERT/RoBERTa for semantic understanding

## Installation & Requirements

### Dependencies
```python
pandas
matplotlib
seaborn
google.colab (for Colab environment)
```

### Installation
```bash
pip install pandas matplotlib seaborn
```

## Project Structure

```
dma-project/
├── 436000918_ProjectCheckPoint1.ipynb    # Main analysis notebook
├── README.md                              # This file
└── Reviews.csv                            # Dataset (not included - download from Kaggle)
```

## Usage

### Running the Notebook

1. **Download the Dataset:**
   - Visit [Kaggle](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews/data)
   - Download `Reviews.csv`

2. **Setup Environment:**
   ```python
   # For Google Colab users:
   from google.colab import drive
   drive.mount('/content/drive')
   
   # Update file path to your Reviews.csv location
   file_path = '/path/to/Reviews.csv'
   ```

3. **Run Analysis:**
   - Execute cells sequentially
   - Data cleaning removes duplicates and HTML artifacts
   - Visualizations generate automatically

## Exploratory Data Analysis Findings

### Data Cleaning
- **Duplicate Removal:** Reduced dataset from 568K to 393K reviews
- **HTML Tag Stripping:** Removed web formatting artifacts
- **Helpfulness Validation:** Filtered invalid helpfulness ratios
- **Temporal Features:** Extracted year and month from Unix timestamps

### Key Insights

1. **Rating Distribution:**
   - Significant J-curve bias toward 5-star ratings
   - 1-star reviews are longer and more detailed than 5-star reviews

2. **Review Length vs. Helpfulness:**
   - Longer reviews (200+ words) receive higher helpfulness ratios
   - Community values detailed, information-dense content

3. **User Segmentation:**
   - **Amateur Reviewers (1-2 reviews):** Majority of user base
   - **Active Reviewers (3-5 reviews):** Moderate engagement
   - **Very Active Reviewers (5+ reviews):** Small but influential group

4. **Bi-gram Analysis:**
   - **1-Star Reviews:** "very disappointed", "waste money", "customer service"
   - **5-Star Reviews:** "highly recommend", "great price", "excellent product"

### Visualizations
- Chronological distribution of reviews (1999-2012)
- Score frequency distribution
- Average word count by review score
- Helpfulness ratio vs. review length
- User segmentation distribution

## Research Questions

1. How do specific bi-grams and vocabulary complexity evolve as reviewers gain experience on the platform?

2. Can a bipartite graph-based recommendation system improve accuracy by prioritizing product links established by very active reviewers?

## Hypotheses

- **Helpfulness as Quality Indicator:** Helpfulness Ratio predicts review honesty and depth
- **User Experience Correlation:** Very active reviewers show stronger sentiment-score alignment
- **Temporal Anomaly Detection:** Sudden spikes in 5-star reviews with decreased word counts signal potential manipulation
- **Niche Product Patterns:** Specialty food categories exhibit more complex linguistic patterns

## Data Quality Considerations

### Bias
- **Rating Distribution Bias:** Heavy skew toward 5-star ratings
- **Product Variation Duplicates:** Same reviews across product sizes/flavors

### Ethical Considerations
- Risk of automated sentiment models suppressing valid negative feedback
- Potential for unfair competitive advantage through review manipulation detection

## Future Directions

- Implement Graph Neural Networks (GNNs) for user-product relationship modeling
- Apply LDA for automated topic discovery (Taste, Shipping, Packaging)
- Develop anomaly detection for bot-driven review patterns
- Construct weighted bipartite graphs for recommendation systems

## Citations

McAuley, J., & Leskovec, J. (2013). *From amateurs to connoisseurs: modeling the evolution of user expertise through online reviews*. WWW 2013.




## License

This project uses publicly available data from Kaggle under Public Domain licensing for academic and research purposes.

## Author

Sahil Fayaz  
Texas A&M University  

## Acknowledgments

- **Dataset Provider:** Stanford Network Analysis Project (SNAP)
- **Platform:** Kaggle
- **AI Assistance:** Gemini (for technical guidance and formatting)

---

**Last Updated:** February 2026
