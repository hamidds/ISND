# Iranian Social Norm Dataset (ISN)

[![Paper](https://img.shields.io/badge/Paper-NAACL%202025-blue)](https://aclanthology.org/2025.findings-naacl.337/)
[![License](https://img.shields.io/badge/License-CC--BY--4.0-green)](LICENSE)
[![Dataset](https://img.shields.io/badge/Dataset-1%2C699%20samples-orange)]()
[![Language](https://img.shields.io/badge/Language-Farsi%20%7C%20English-red)]()

> **Can I Introduce My Boyfriend to My Grandmother? Evaluating Large Language Models Capabilities on Iranian Social Norm Classification**

Welcome to the **Iranian Social Norm (ISN) Dataset** repository! This is the first comprehensive dataset designed to capture social norms and cultural expectations in Iranian society, featuring 1,699 carefully annotated samples in both Farsi and English.

## 🌟 Overview

Social norms are the unwritten rules that govern behavior within societies. The ISN dataset addresses a critical gap in AI research by providing culturally-specific data for Iranian society, enabling the development of more inclusive and culturally-aware AI systems.

### Why ISN Matters
- **First of its kind**: The only dataset exclusively focused on Iranian social norms
- **Bilingual**: Available in both Farsi and English to support diverse research communities
- **Culturally nuanced**: Distinguishes between Iran-specific norms and general ones
- **Comprehensive**: Includes environmental context and demographic features
- **Research-validated**: Peer-reviewed and accepted at NAACL 2025

## 📊 Quick Stats

| Metric | Value |
|--------|-------|
| **Total Samples** | 1,699 |
| **Languages** | Farsi + English |
| **Unique Environments** | 197 |
| **Iran-Specific Norms** | 44.1% |
| **Annotator Agreement** | 56% (Fleiss' Kappa) |

## 🎯 Dataset Structure

### Core Components

| Component | Description | Example |
|-----------|-------------|---------|
| **Norm** | Specific social norm or cultural expectation | "Showing respect for elders" |
| **Environment** | Setting where the norm applies | "family gatherings", "workplace", "mosque" |
| **Demographic Features** | Characteristics of the person (age, gender, religion, etc.) | "female; muslim; unmarried" |
| **Label** | Acceptability classification | Expected, Normal, Taboo |
| **Scope** | Cultural specificity | Specific (Iran-only), General (universal) |

### Label Definitions

- **Expected** (44.9%): Widely accepted, aligned with cultural norms in Iran
- **Normal** (31.1%): Tolerated, permissible but not necessarily common or preferred  
- **Taboo** (24.0%): Uncommon, atypical, contradicts prevalent cultural norms in Iran

### 👥 Demographic Features

The dataset includes detailed demographic characteristics (522 out of 1,699 entries have demographic features):

**English**: Age (child, adult, elderly, young) | Gender (woman, man) | Religion (Muslim, Christian, Jewish, Zoroastrian, Not Muslim) | Family Status (single, married, engaged, divorced, widowed) | Family Role (father, mother, son, daughter, etc.) | Educational Role (student, teacher, professor) | Social Status (poor, middle class, wealthy) | Ethnicity (Fars, Turk, Kurd, Arab, Baluch, Turkmen, Qashqai)

**Farsi**: سن (کودک، بالغ، مسن، جوان) | جنسیت (زن، مرد) | دین (مسلمان، مسیحی، یهودی، زرتشتی، نامسلمان) | وضعیت خانوادگی | نقش خانوادگی | نقش آموزشی | وضعیت اجتماعی | قومیت

### 📝 Sample Data

| Environment | Demographic Features | Norm | Label |
|-------------|---------------------|------|-------|
| Wedding ceremony | female; muslim; unmarried | Obtaining father's consent | Expected |
| Mosque | muslim | Distributing votive food offerings | Normal |
| Street | female | Lacking hijab completely in public | Taboo |

*Note: All entries above are marked as "Specific" scope, meaning they are closely linked to Iranian culture.*

## 🔧 Usage

### Quick Start

```bash
# Clone the repository
git clone https://github.com/hamidds/ISN
cd ISN

# Install required dependencies (optional, for analysis)
pip install pandas numpy matplotlib seaborn
```

### Loading the Dataset

```python
import pandas as pd

# Load dataset with separate demographic columns
df_with_demo = pd.read_csv('[ISN] FINAL - w_demographiccols-updated.csv')

# Load dataset with joint demographic features
df_without_demo = pd.read_csv('[ISN] FINAL - wo_demographiccols-updated.csv')

print(f"Dataset shape: {df_with_demo.shape}")
print(f"Columns: {list(df_with_demo.columns)}")
```

### Example Analysis

```python
# Analyze label distribution
label_dist = df_with_demo['Label'].value_counts(normalize=True)
print("Label Distribution:")
print(label_dist)

# Filter Iran-specific norms
iran_specific = df_with_demo[df_with_demo['Scope - EN'] == 'Specific']
print(f"Iran-specific norms: {len(iran_specific)} ({len(iran_specific)/len(df_with_demo)*100:.1f}%)")

# Examine demographic patterns
demo_counts = df_with_demo['Demographic features - EN'].value_counts()
print("Top demographic patterns:")
print(demo_counts.head())
```

## 📁 Files

| File | Description | Size |
|------|-------------|------|
| **`[ISN] FINAL - w_demographiccols-updated.csv`** | Complete dataset with separate demographic columns | ~1,699 rows |
| **`[ISN] FINAL - wo_demographiccols-updated.csv`** | Dataset with joint demographic features only | ~1,699 rows |
| **`README.md`** | This documentation file | - |
| **`LICENSE`** | CC-BY-4.0 license file | - |

### Data Format

Both CSV files contain the following key columns:
- `Norm - EN/FA`: Social norm description in English/Farsi
- `Environment - EN/FA`: Setting/context in English/Farsi  
- `Demographic features - EN/FA`: Relevant demographic information
- `Label`: Classification (Expected/Normal/Taboo)
- `Scope - EN`: Cultural specificity (Specific/General)

## 🎯 Applications

The ISN dataset can be used for:

### Research Applications
- **Social Norm Classification**: Train and evaluate models on culturally-specific norms
- **Cross-Cultural Studies**: Compare Iranian norms with other cultural contexts
- **Bias Detection**: Identify cultural biases in language models
- **Cultural AI**: Develop culturally-aware AI systems

### NLP Tasks
- **Fine-tuning LLMs**: Improve cultural understanding of language models
- **Evaluation Benchmarks**: Test model performance on cultural knowledge
- **Prompt Engineering**: Design culturally-sensitive prompts
- **Multilingual NLP**: Study norm classification across languages

## 📈 Benchmark Results

Our evaluation of 6 Large Language Models revealed significant challenges in understanding Iranian social norms:

| Model | English (Iran Context) | Farsi | Best F1-Score |
|-------|----------------------|-------|---------------|
| GPT-4o | **0.609** | **0.581** | 0.609 |
| Mixtral-8x7B | **0.611** | 0.531 | 0.611 |
| Aya-23-8B | 0.578 | 0.532 | 0.578 |

**Key Findings:**
- All models showed suboptimal performance (best: 61% F1)
- Performance significantly worse on Iran-specific norms vs. general norms
- Adding geographic context ("in Iran") improved English performance but not Farsi
- Models particularly struggled with "Normal" category norms

## 🏗️ Methodology

### Data Construction
1. **Generation**: Used Claude (Anthropic) with carefully designed prompts
2. **Validation**: Three native Farsi speakers reviewed and edited all samples
3. **Annotation**: Independent labeling with majority vote (Fleiss' κ = 0.56)
4. **Translation**: Professional translation to English with manual validation

### Quality Assurance
- Native Iranian annotators with deep cultural knowledge
- Multiple rounds of validation and editing
- Removal of irrelevant, repetitive, or nonsensical samples
- Cross-linguistic consistency checks

## 👥 Team

**Authors:**
- Hamidreza Saffari (Politecnico di Milano)
- Mohammadamin Shafiei (University of Milan)  
- Donya Rooein (Bocconi University)
- Francesco Pierri (Politecnico di Milano)
- Debora Nozza (Bocconi University)


## 📚 Citation

If you use the ISN dataset in your research, please cite our NAACL 2025 paper:

```bibtex
@inproceedings{saffari-etal-2025-introduce,
    title = "Can {I} Introduce My Boyfriend to My Grandmother? Evaluating Large Language Models Capabilities on {I}ranian Social Norm Classification",
    author = "Saffari, Hamidreza  and
      Shafiei, Mohammadamin  and
      Rooein, Donya  and
      Pierri, Francesco  and
      Nozza, Debora",
    editor = "Chiruzzo, Luis  and
      Ritter, Alan  and
      Wang, Lu",
    booktitle = "Findings of the Association for Computational Linguistics: NAACL 2025",
    month = apr,
    year = "2025",
    address = "Albuquerque, New Mexico",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2025.findings-naacl.337/",
    doi = "10.18653/v1/2025.findings-naacl.337",
    pages = "6060--6074",
    ISBN = "979-8-89176-195-7",
}
```

## ⚖️ License

This dataset is licensed under the [CC-BY-4.0 License](LICENSE), allowing for broad usage with attribution.

## ⚠️ Ethical Considerations & Limitations

### Important Notes
- This dataset represents norms as observed, not as behavioral prescriptions
- Annotations reflect perspectives of Iranian university students studying abroad (limited demographic)
- Social norms are dynamic and may change over time
- The dataset may not capture all nuances of Iran's diverse cultural landscape
- Generated using LLMs, which may introduce certain biases
- Differences in annotator agreement highlight the subjective nature of cultural norms

### Responsible Usage
- Use for research and educational purposes
- Acknowledge cultural context and avoid stereotyping
- Consider the limitations when drawing conclusions
- Respect the cultural sensitivity of the data

## 🤝 Contributing

We welcome contributions to improve the dataset! Please feel free to:
- Report issues or inconsistencies
- Suggest additional norms or environments
- Propose improvements to annotations
- Share your research results using ISN


## 🙏 Acknowledgments

We thank our dedicated annotators and reviewers for their valuable contributions to this dataset. This work represents a significant step toward building AI systems that better understand and respect cultural nuances in human society.

---

