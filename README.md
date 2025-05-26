# DetectionAI

This repository contains notebooks and summary tables for evaluating the performance of several AI text detection tools. The experiments measure how well different detectors identify AI-generated content across a variety of text genres and lengths.

## Repository contents

- **`Code_detection.ipynb`** – Runs multiple detectors (Pangram, Originality.ai, GPTZero, ZeroGPT, and a RoBERTa-based model) on a corpus of human and AI-generated texts.
- **`Code_new_detection_withStealthgpt.ipynb`** – Evaluates detection accuracy when the AI text is rewritten using StealthGPT and computes detection thresholds.
- **`Code_shorter_text_analysis.ipynb`** – Analyses detector performance on short texts and generates summary tables.
- **`Code_statistics_part.ipynb`** – Produces the statistics used in Tables 1 and 2, including AUROC and type‑I/type‑II error rates.
- **CSV tables** – `Table1_*.csv`, `Table2_*.csv`, and their `ShortText_` variants store the aggregated results reported by the notebooks.

## Setup

These notebooks were designed for execution in Google Colab. They require Python packages such as `pandas`, `numpy`, `scikit-learn`, `torch`, `transformers`, and `requests`. Install the dependencies in your Colab environment or local Jupyter setup before running the notebooks.

Some notebooks call external detection APIs. Provide your own API keys by editing the corresponding notebook cells before execution.

The input data referenced in the notebooks is stored in a Google Drive folder named `pre2020_human_text_by_genre`. Update the paths if your data is stored elsewhere.

## Running the notebooks

1. Open the desired notebook in Google Colab.
2. Mount your Google Drive so the notebooks can access the dataset and store results.
3. Install any required Python packages using `pip install`.
4. Replace the placeholder API keys with your own values.
5. Execute the cells sequentially to reproduce the detection results.

The summary CSV files included in this repository contain the metrics produced by the notebooks and may be used directly without rerunning the detection.

## Results overview

- **Table 1** files report overall AUROC and Δ‑Mean values for each detector, both overall and by genre.
- **Table 2** files contain precision and recall statistics at various detection thresholds.
- **ShortText** tables capture the same metrics for short-form text experiments.

## License

No license information is provided. If you plan to reuse the code or results, please contact the repository owner.

