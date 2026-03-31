# Sustainable-Public-Opinion-Policy-vs-Marketplace-Discourse


This project analyzes **attitudes toward sustainable policy** by comparing two fundamentally different discourse arenas:

-  **City council transcripts** (policy & governance)
-  **Amazon consumer electronics reviews** (marketplace & lived experience)

Using a **comparable keyword-centered window approach**, the project uncovers how sustainability is framed, interpreted, and evaluated differently across institutions and consumers.

---

##  Key Contributions

- **Comparable text unit design** using ±400-character keyword windows across corpora
- **Theme → subtopic framework** for sustainability discourse
- **Cross-arena comparison** of policy vs marketplace discourse
- **Attitude measurement** through:
  - stance (support / oppose / conditional / neutral)
  - sentiment (VADER)
  - optional emotion signals
- Identification of **policy–market mismatch** and **resistance drivers**

---

##  Research Questions

- **RQ1:** What themes dominate city sustainability-policy discourse?
- **RQ2:** What themes dominate sustainability-related marketplace discourse?
- **RQ3:** How do stance profiles differ across arenas and subtopics?
- **RQ4:** How does city discourse vary over time and geography?

---

##  Pipeline Overview

```text
Raw Text Data
   ↓
Keyword Dictionary (themes)
   ↓
Window Extraction (±400 chars)
   ↓
Theme Assignment
   ↓
Within-theme Topic Modeling (LDA)
   ↓
Subtopic Naming (human-in-the-loop)
   ↓
Attitude Measurement
   ↓
Comparative Analysis (City vs Amazon)
```

---

##  Project Structure

```text
.
├── data/
│   ├── city_transcripts/
│   ├── amazon_reviews/
│
├── outputs/
│   ├── sustainability_public_opinion_within_theme_and_cooc.xlsx
│   ├── Final_Results.xlsx
│   ├── figures_discovery/
│   ├── Publication_Tables_and_Appendices.xlsx
│   └── Figure1_pipeline.png
│
├── src/
│   ├── 01_window_extraction.py
│   ├── 02_theme_assignment.py
│   ├── 03_subtopic_modeling.py
│   ├── 04_stance_sentiment.py
│   ├── 05_analysis_visualization.py
│
├── paper/
│   ├── manuscript.docx / .tex
│   ├── figures/
│   ├── tables/
│
├── README.md
└── requirements.txt
```

---

##  Methods Summary

### 1. Window Extraction
- Keyword-triggered extraction
- ±400 characters around keyword hits
- Overlapping windows merged

### 2. Theme Assignment
- Dictionary-based mapping
- Assign `dominant_theme` per window

### 3. Subtopic Modeling
- **Within-theme LDA (Gensim)**
- Separate models for each theme and each source (city vs Amazon)
- Human labeling of subtopics

### 4. Attitude Measures
- **Stance classifier** (rule-based / model-based)
- **Sentiment**: VADER
- **Emotion**: lexicon-based (optional)

### 5. Validation
- 2 annotators (400–800 samples)
- Metrics:
  - Cohen’s κ
  - Accuracy
  - Macro-F1

---

##  Key Findings (Summary)

-  **City discourse** is dominated by **policy & regulation (~66%)**
-  **Amazon discourse** is dominated by **consumer tradeoffs (~82%)**

###  Core Insight
> Sustainability is framed as **institutional policy** in city discourse,  
> but as **practical tradeoffs** in consumer experience.

---

##  Outputs & Visualizations

### Main Figures
- Figure 1: Pipeline schematic
- Theme prevalence (City vs Amazon)
- Subtopic prevalence within themes
- Stance distribution (overall & subtopic-level)
- Sentiment heatmaps
- Resistance hotspots

### Supplementary
- Time trends (city)
- State variation
- Emotion heatmaps

---

##  Example: Load Results

```python
import pandas as pd

df = pd.read_excel("outputs/Final_Results.xlsx")
print(df.head())
```

---

##  Installation

```bash
git clone https://github.com/yourusername/sustainable-public-opinion.git
cd sustainable-public-opinion
pip install -r requirements.txt
```

---

##  Dependencies

- pandas
- numpy
- gensim
- nltk
- scikit-learn
- matplotlib
- seaborn
- openpyxl

---



### Focus
- Policy communication
- Consumer behavior mismatch
- Sustainability implementation challenges

---

##  Limitations

- Window-based context may truncate meaning
- Amazon reviews are subject to self-selection bias
- Emotion signals are weak and should be interpreted cautiously
- Stance validation requires final annotation metrics

---

##  Reproducibility

- Fixed keyword dictionary (Appendix A1)
- Transparent stance rules (Appendix A2)
- Documented LDA settings (Appendix A3)
- Validation protocol (Appendix A4)

---

##  Future Work

- Extend to other product categories (food, apparel, home goods)
- Improve stance classification with supervised or LLM-based models
- Link discourse patterns to behavioral outcomes
- Explore cross-country policy comparisons



##  Final Note

This project addresses a core sustainability challenge:

> Sustainable policy succeeds not only when it is written,  
> but when it aligns with how people actually experience products.
