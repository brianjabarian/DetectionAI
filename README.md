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
