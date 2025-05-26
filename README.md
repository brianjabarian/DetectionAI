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
1. **AI-Use Disclosure** – We evaluate several detectors:
   - **Pengram**
   - **GPTZero**
   - **Originality**
   - **roberta-base-detector**
2. **Model Choice**—Closed–source APIs were chosen as primary models because the open-source model, Roberta-base-detector, performs extremely poorly and appears only as a secondary check.
3. **Reproducibility Package** – All notebooks, prompts, and parameter settings live in this repository under `notebooks/` and `results/`. The environment can be recreated with `requirements.txt`.
4. **Training-Data Separation** – We do not upload any confidential data to third-party services.
5. **Chain-of-Thought Transparency** – Reasoning traces saved by the notebooks include one quantitative quality metric.
6. **Hallucination & Robustness Diagnostics** – Results tables report sensitivity to multiple sampling settings.
7. **Citation and Attribution** – Any verbatim AI-generated text will cite the model snapshot and date.
8. **Reviewer Checklist** – The repository contains, to the best of our knowledge, sufficient material to satisfy the policy's reproducibility checklist.


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

Feel free to contact the author for clarification or collaboration requests.

## References

Brian Jabarian, 2025, Scientific Policy on AI Use & Reproducibility in Economics, work-in-progress

