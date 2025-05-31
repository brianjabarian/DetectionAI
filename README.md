# DetectionAI

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Build](https://img.shields.io/badge/build-passing-brightgreen)](#)

DetectionAI investigates how reliably we can identify AI-generated writing. The notebooks compare multiple detectors across datasets and summarize performance metrics that inform practical detection thresholds.

## Table of Contents
- [Repository Contents](#repository-contents)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Study Design](#study-design)
- [Usage](#usage)
- [AI Policy Compliance](#ai-policy-compliance)
- [License](#license)
- [Citation](#citation)
- [References](#references)

## Repository Contents
- `notebooks/` – Jupyter notebooks for running the detection experiments.
- `results/` – CSV tables produced by the notebooks.
- `data/` – placeholder directory for raw datasets.
- `requirements.txt` – Python dependencies for the project.

## Prerequisites
This project requires **Python 3.10+**. The main Python packages used are listed
in [requirements.txt](requirements.txt): pandas, numpy, torch, transformers,
scikit-learn, scipy, openai, requests and tqdm.

## Installation
```bash
git clone https://github.com/your-user/DetectionAI.git
cd DetectionAI
pip install -r requirements.txt
```

## Quick Start
Run `notebooks/Code_statistics_part.ipynb` first. It loads the dataset JSON files and
produces summary tables such as [results/Table1_overall.csv](results/Table1_overall.csv).
Look for AUROC scores close to 1.0 indicating strong detection.

## Study Design
Our workflow involves several steps:
1. Gather pre-2020 human-written texts spanning different genres.
2. Create AI-generated versions of these texts using the following prompt [].
3. Evaluate multiple AI detectors on the combined dataset, reporting type I and type II error rates overall and by genre.
4. Examine how performance changes when detection thresholds vary.
5. Repeat the evaluation for short passages (49 words or fewer).
6. "Humanize" the AI-generated texts with the StealthGPT tool and re-test them using the best-performing detector, Pengram.


## Data Sources

Our evaluation relies on a diverse collection of **pre-2020 human-authored texts** across multiple genres. The original human-written documents are sourced from publicly available and widely used datasets:

* **[CC-News](https://huggingface.co/datasets/cc_news)** – A collection of English-language news articles scraped from Common Crawl. Used to represent journalistic content.
* **[Bar-Ilan Blog Authorship Corpus](https://huggingface.co/datasets/barilan/blog_authorship_corpus)** – A corpus of personal blog posts written by thousands of authors. Used to evaluate performance on informal first-person writing.
* **[Resume Dataset (Kaggle)](https://www.kaggle.com/datasets/snehaanbhawal/resume-dataset)** – A compilation of resumes and CVs representing professional self-descriptions. Used to test detector accuracy on structured, formal writing.
* **[Yelp Review Full](https://huggingface.co/datasets/Yelp/yelp_review_full)** – User-generated reviews with sentiment ratings. Used to evaluate performance on consumer-facing narrative and opinionated writing.
* **[Amazon Reviews (Kaggle)](https://www.kaggle.com/datasets/kritanjalijain/amazon-reviews)** – Product reviews across a wide range of categories. Used to assess generalization across e-commerce and review genres.
* **[Pre-2000 Novel Corpus](https://github.com/computationalstylistics/100_english_novels/tree/master/corpus)** – A collection of long-form fictional texts written prior to the year 2000. Included to test how detectors perform on traditional narrative structures and literary language, distinct from modern internet discourse.

## Usage
The notebooks were developed in **Google Colab**, but they can be run locally as
well.

### Colab
1. Open the desired notebook on GitHub and choose **Open in Colab**.
2. Mount Google Drive when prompted so the notebooks can access the data files in
   `/content/drive/...`.

### Local
1. Clone the repository and install the requirements as shown above.
2. Place the data JSON/CSV files in a directory of your choice and update the
   paths at the top of each notebook.
3. Set any required API keys (e.g. `OPENAI_API_KEY`) as environment variables
   before running cells that call external services.

## AI Policy Compliance
This project follows the **Scientific Policy on AI Use & Reproducibility in Economics (Jabarian, 2025)**.
Key points include:
1. **AI-Detection Systems** – We evaluate several detectors:
   - **Pengram**
   - **GPTZero**
   - **Originality**
   - **roberta-base-detector** 
2. **AI-Detector System Choice** Closed–source APIs were chosen as primary models because the open-source model, Roberta-base-detector, performs extremely poorly and appears only as a secondary check.
3. **AI-Generating Model** We used GPT-3.5-turbo to generate the AI writings following this parametrization:
   - model="gpt-3.5-turbo",
   - temperature=0.7,
   - max_tokens=min(word_count * 2, 2048)
5. **AI Prompts** We used the following prompt to generate the AI version of the human pre-2020 texts: """You are a writing assistant. Write an original passage on the topic: '{topic}'. It should be approximately {word_count} words long. Be clear and human-like. Avoid copying or referencing specific texts. ⚠️ Do not include or repeat the topic or instructions in your output. Return only the generated passage text."""
6. **Training-Data Separation** – We do not upload any confidential data to third-party services.
7. **Hallucination & Robustness Diagnostics** – Results tables report sensitivity to multiple sampling settings.
8. **Citation and Attribution** – Any verbatim AI-generated text will cite the model snapshot and date.
9. **Reviewer Checklist** – The repository contains, to the best of our knowledge, sufficient material to satisfy the policy's reproducibility checklist.


## Contributors
1. Co-authors: Alex Imas, Brian Jabarian
2. RAs: Eda Congedez, Ziyue Fenge, Zlata Krasic

## License

This project is licensed under the [MIT License](LICENSE).

## Citation
If you build upon this work, please cite it as:

```
Alex Imas, Brian Jabarian. "DetectionAI: Evaluating AI-generated text detectors." 2025.
```

Feel free to contact the authors for clarification requests.

alex.imas@chicagobooth.edu
brian.jabarian@chicagobooth.edu

## References

Brian Jabarian, 2025, Scientific Policy on AI Use & Reproducibility in Economics, work-in-progress

