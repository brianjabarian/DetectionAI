# DetectionAI

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Build](https://img.shields.io/badge/build-passing-brightgreen)](#)

DetectionAI investigates how reliably we can identify AI-generated writing. The notebooks compare multiple detectors across datasets and summarize performance metrics that inform practical detection thresholds.

## Table of Contents
- [Repository Contents](#repository-contents)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Usage](#usage)
- [License](#license)
- [Citation](#citation)

## Repository Contents
- **Code_detection.ipynb** – baseline detection notebook.
- **Code_new_detection_withStealthgpt.ipynb** – experiments using the StealthGPT dataset.
- **Code_shorter_text_analysis.ipynb** – analysis of short text samples.
- **Code_statistics_part.ipynb** – helper notebook with statistics utilities.
- **CSV files** – tables of detection results used in the notebooks.

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
Run `Code_statistics_part.ipynb` first. It loads the dataset JSON files and
produces summary tables such as [Table1_overall.csv](Table1_overall.csv).
Look for AUROC scores close to 1.0 indicating strong detection.

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

## License

This project is licensed under the [MIT License](LICENSE).

## Citation
If you build upon this work, please cite it as:

```
Alex Imas, Brian Jabarian. "DetectionAI: Evaluating AI-generated text detectors." 2025.
```

Feel free to contact the author for clarification or collaboration requests.
