# 🎬 YouTube Thumbnail A/B Testing

<div align="center">

![Project Thumbnail](https://github.com/akisavujel/Youtube-thumbnail-A-B-testing-PYTHON/blob/2e91a95b30c3af39b773281ed7dbfb63699d3bb6/Youtube-thumbnail.webp)

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

*A data-driven experiment to find out which YouTube thumbnail drives more clicks — using statistics, not guesswork.*

</div>

---

## 📋 Table of Contents

- [📌 Introduction](#-introduction)
- [🛠️ Tools Used](#️-tools-used)
- [📌 Dataset](#-dataset)
- [🧐 Explore the Dataset](#-explore-the-dataset)
- [✨ Clean the Dataset](#-clean-the-dataset)
- [📊 Visualize the Data](#-visualize-the-data)
- [⚖️ Hypothesis Testing](#️-hypothesis-testing-ctr)
- [📝 Conclusion](#-conclusion)
- [👤 Author](#-author)

---

## 📌 Introduction

In the digital age, content creators on YouTube constantly compete for viewer attention. One of the most powerful yet often overlooked factors in a video's success is its **thumbnail** — the first visual impression a potential viewer gets before deciding to click.

This project simulates a real-world **A/B test** conducted by a YouTuber who wants to find out whether a redesigned thumbnail performs better than the original. By running a controlled experiment over **30 days**, we can use data and statistics to make a confident, evidence-based decision — rather than relying on guesswork.

> 💡 **Key Question:** Does the redesigned thumbnail (Variant B) perform significantly better than the original (Variant A)?

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| 🐍 **Python** | Core programming language |
| 🐼 **Pandas** | Data manipulation & analysis |
| 🔢 **NumPy** | Numerical computations |
| 📊 **Matplotlib** | Data visualization |
| 🎨 **Seaborn** | Statistical data visualization |
| 🔬 **SciPy / Statsmodels** | Hypothesis testing (Z-test) |
| 📓 **Jupyter Notebook** | Interactive development environment |
| 🌐 **HTML** | Notebook cell styling & structure |
| 🎨 **CSS** | Custom styling & formatting |

---

## 📌 Dataset

📥 You can download the dataset [here](https://github.com/akisavujel/Youtube-thumbnail-A-B-testing-PYTHON/blob/main/Thumbnail_A_B_testing.csv).

**Features include:**

| Column | Type | Description |
|---|---|---|
| `Day` | int | Day of the experiment (1–30) |
| `Variant` | str | A (original) or B (redesigned) thumbnail |
| `Impressions` | int | Number of times the thumbnail was shown |
| `Clicks` | int | Number of clicks on the thumbnail |
| `CTR` | float | Click-Through Rate (Clicks / Impressions) |
| `Avg_watch_time_sec` | float | Average watch time in seconds |

---

## 🧐 Explore the Dataset

Check the first few rows, data info, and summary statistics to understand the dataset. Identify missing values and data types before proceeding with analysis.

**📈 Average metrics per Variant:**

| Metric | Variant A | Variant B |
|---|---|---|
| Daily Impressions | 2,000 – 4,000 | 8,000 – 10,000 |
| CTR Range | 0.2 – 0.4 | 0.6 – 0.9 |
| CTR Median | ~0.3 | ~0.75 |

---

## ✨ Clean the Dataset

- ✅ Remove duplicates.
- ✅ Rename columns for clarity, e.g., `"Avg_watch_time"` → `"Avg_watch_time_sec"`.

---

## 📊 Visualize the Data

### 📈 Daily Impressions — Variant A vs Variant B
- Variant B consistently receives **~3x more impressions** than Variant A every single day.
- There is **not a single day** where Variant A matched or beat Variant B.

### 🖱️ Total Clicks — Variant A vs Variant B

| Variant | Total Clicks |
|---|---|
| 🟣 Variant A | ~26,000 |
| 🟢 Variant B | ~185,000 |

> Variant B generated **7x more total clicks** over the entire 30-day experiment.

### 📉 CTR Distribution — Variant A vs Variant B
- **Variant A CTR:** 0.2 – 0.4 (median ≈ 0.3) — half the days performed below 30% CTR
- **Variant B CTR:** 0.6 – 0.9 (median ≈ 0.75) — consistently above 60% CTR every day

---

## ⚖️ Hypothesis Testing (CTR)

**Null Hypothesis (H₀):** There is no significant difference in CTR between Variant A and Variant B.  
**Alternative Hypothesis (H₁):** Variant B has a significantly higher CTR than Variant A.

A **Z-test for proportions** was conducted using total clicks and impressions across both variants.

```python
from statsmodels.stats.proportion import proportions_ztest

clicks      = [A_data['Clicks'].sum(),      B_data['Clicks'].sum()]
impressions = [A_data['Impressions'].sum(),  B_data['Impressions'].sum()]

stat, pval = proportions_ztest(count=clicks, nobs=impressions, alternative='two-sided')
```

**Results:**

| Metric | Result |
|---|---|
| Z-Test Statistic | Significant |
| p-value | < 0.05 ✅ |
| Decision | **Reject H₀** |

> ✅ **Reject H₀:** Variant B has a significantly higher CTR than Variant A. The difference is **real** and not due to random chance.

---

## 📝 Conclusion

Based on the 30-day A/B test, **Variant B significantly outperforms Variant A** across all key metrics.

**📊 Visualization Findings:**
- Variant B received nearly **3x** more impressions than Variant A every single day
- Variant B generated **7x** more total clicks over the entire experiment
- Variant B maintained a consistently higher CTR of **0.6 – 0.9** vs Variant A's **0.2 – 0.4**
- Variant B watch time was significantly higher throughout all 30 days
- There was **not a single day** where Variant A matched or beat Variant B

**🔬 Hypothesis Testing Findings:**
- Z-Test: CTR difference is statistically significant **(p < 0.05)**
- We **reject H₀** — the difference is real and not due to random chance

### ✅ Recommendation

> 🚀 The YouTuber should **immediately switch to Variant B** as the default thumbnail. The redesigned thumbnail — with bold visuals and the creator's face visible — is far more effective at attracting viewer attention, driving clicks, and keeping viewers engaged longer.

---

## 👤 Author

<div align="center">

**Akisha Bhujel**

[![Kaggle](https://img.shields.io/badge/Kaggle-20BEFF?style=for-the-badge&logo=Kaggle&logoColor=white)](https://www.kaggle.com/akisavujel)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/akishabhujel/)
[![Blog](https://img.shields.io/badge/Blog-FF5722?style=for-the-badge&logo=blogger&logoColor=white)](https://akisavujel.blogspot.com/)

*If you found this project helpful, please consider giving it a ⭐ on GitHub!*

---

<img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExazJyaHJtcXViamE2OGZibmZnYmlpZnBrcW9hb3c0aDhrcmo2dDRxcSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/UcFddPv7emtgOYWwMe/giphy.gif" width="300">

</div>
