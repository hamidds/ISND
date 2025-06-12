# Iranian Social Norm Dataset

Welcome to the Iranian Social Norm Dataset repository! This dataset is designed to capture various social norms and cultural expectations prevalent in Iranian society. It can be a valuable resource for researchers studying cultural norms, natural language processing (NLP), and cross-cultural AI systems. This dataset is prestened in the paper "Can I Introduce My Boyfriend to My Grandmother? Evaluating Large Language Models Capabilities on Iranian Social Norm Classification" by Saffari et al., accepted at NAACL 2025.

## Dataset Description

| Column Name                       | Description                                                                                                                                                                                                                  | Possible Values                                                                                                                                                             |
|-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Norm - EN                         | The specific social norm or cultural expectation being represented, stated clearly and concisely in English.                                                                                                             | e.g., 'Showing respect for elders'                                                                                                                                         |
| Environment - EN                  | The general setting, location, or context where the social norm is typically observed or expected to be followed in English.                                                                                             | e.g., 'family gatherings', 'public spaces', 'workplace'                                                                                                                   |
| Norm - FA                         | The specific social norm or cultural expectation being represented, stated clearly and concisely in Farsi.                                                                                                                | e.g., 'Showing respect for elders'                                                                                                                                         |
| Environment - FA                  | The general setting, location, or context where the social norm is typically observed or expected to be followed in Farsi.                                                                                               | e.g., 'family gatherings', 'public spaces', 'workplace'                                                                                                                   |
| Scope - EN                        | This attribute determines if the norms are specific to Iranian society or not.                                                                                                                                           | Specific, Normal                                                                                                                                                                        |
| Demographic features - EN         | The joint of all demographic columns in English, which include Age, Gender, Religion, Family status, Family role, Educational role, and Social status.                                                                      | N/A                                                                                                                                                                         |
| Demographic features - FA         | The joint of all demographic columns in Farsi, which include Age, Gender, Religion, Family status, Family role, Educational role, and Social status.                                                                        | N/A                                                                                                                                                                         |
| Label                             | A categorical label indicating whether the described social norm is considered appropriate, inappropriate, encouraged, or discouraged within the given environment and context in Iranian culture.                          | Expected, Normal, Taboo                                                                                                                                                   |

### Demographic Features

#### English

- **Age**: The age of the person that the norm is associated with. Possible values: child, adult, elderly, young.
- **Gender**: The gender of the person that the norm is associated with. Possible values: woman, man.
- **Religion**: The religion of the person that the norm is associated with. Possible values: Muslim, Christian, Jewish, Zoroastrian, Not Muslim.
- **Ethnicity**: The ethnicity of the person that the norm is associated with. Possible values: Fars, Turk, Kurd, Arab, Baluch, Turkmen, Qashqai.
- **Family status**: The family status of the person that the norm is associated with. Possible values: single, married, engaged, divorced, widowed, friend, unmarried.
- **Family role**: The family role of the person with whom the norm is associated. Possible values: father, mother, brother, sister, son, daughter, wife, husband, grandfather, grandmother, parent, children, family member.
- **Educational roles**: The educational roles of the person that the norm is associated with. Possible values: student, teacher, professor, university student.
- **Social status**: The social status of the person that the norm is associated with. Possible values: poor, middle class, wealthy.

#### Farsi

- **Age**: The age of the person that the norm is associated with. Possible values: کودک, بالغ, مسن, جوان.
- **Gender**: The gender of the person that the norm is associated with. Possible values: زن, مرد.
- **Religion**: The religion of the person that the norm is associated with. Possible values: مسلمان, مسیحی, یهودی, زرتشتی, نامسلمان.
- **Ethnicity**: The ethnicity of the person that the norm is associated with. Possible values: فارس, ترک, کردی, عرب, بلوچ, ترکمن, قشقایی.
- **Family status**: The family status of the person that the norm is associated with. Possible values: مجرد, متاهل, نامزد , جدا شده, بیوه, دوست, ازدواج نکرده.
- **Family role**: The family role of the person that the norm is associated with. Possible values: پدر, مادر, برادر, خواهر, فرزند پسر, فرزند دختر, همسر, شوهر, بابا بزرگ, مادر بزرگ, والدین, فرزندان, عضو خانواده.
- **Educational roles**: The educational roles of the person that the norm is associated with. Possible values: دانش آموز, معلم, استاد, دانشجو.
- **Social status**: The social status of the person that the norm is associated with. Possible values: فقیر, طبقه متوسط, ثروتمند.

- The description of the labels is as follows:
  - **Expected:** Widely accepted, aligned with cultural norms in Iran.
  - **Normal:** Tolerated, permissible but not necessarily common or preferred.
  - **Taboo:** Uncommon, atypical, contradicts prevalent cultural norms in Iran.

## Data Statistics

The dataset contains 1,699 samples. The distribution of labels is as follows:
- **Expected:** 44.9%
- **Normal:** 31.1%
- **Taboo:** 24%

## Data Construction

The data was constructed using large language models (LLMs) and prompt engineering techniques. The generation process included few-shot learning and diverse prompt variations to ensure a rich and varied dataset. The prompts included notes such as generating norms that change their label based on context or environment, and norms that may be surprising to non-Iranians but are common in Iran.

Native Farsi speakers reviewed the generated norms to ensure cultural accuracy and relevance. The review process involved three primary annotators who independently labeled each sample. 

## Translation to English

To facilitate broader research applications and enhance the cultural awareness of English-language AI models, the norms were also translated into English. This translation enables cross-cultural comparisons and helps develop more inclusive AI systems. 

## Usage

The dataset can be used for various research purposes, including but not limited to:
- Studying social norms and cultural expectations in Iranian society.
- Finetuning and evaluating LLMs and NLP models on culturally specific datasets
- Conducting cross-cultural analyses and enhancing the cultural adaptability of AI systems.

## Files
- [ISN] FINAL - w_demographiccols-updated.csv: contains the dataset along with the demographic columns separately.
- [ISN] FINAL - wo_demographiccols-updated.csv: contains only the joint demographic features.


## 📝 Citation

If you use these datasets in your research, please cite:

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

## License

This dataset is licensed under the [CC-BY-4.0 License](LICENSE).

## Acknowledgements

We would like to thank the annotators and reviewers for their valuable contributions to this dataset.

---

Feel free to reach out if you have any questions or need further assistance.

Happy researching!

