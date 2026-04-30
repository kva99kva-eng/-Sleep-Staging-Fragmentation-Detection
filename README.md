# Sleep Staging + Fragmentation Detection

An exploratory neurotech project for automatic sleep stage classification and sleep fragmentation analysis using open polysomnography data from Sleep-EDF.

## Project goal

The goal of this project is to build an end-to-end baseline pipeline that:

- loads raw PSG and hypnogram EDF files
- converts sleep annotations into 30-second epoch labels
- extracts EEG-based spectral features
- trains a baseline sleep stage classifier
- derives sleep fragmentation metrics from true and predicted stage sequences

This project is designed as a portfolio-quality computational neuroscience / neurotech case study rather than a clinical decision system.

## Dataset

This project uses a subset of **Sleep-EDF Expanded**.

For the current mini-version, the baseline experiments were run on a small subset of subjects and epochs in order to validate the full modeling pipeline before scaling to a larger sample.

## Project structure

```text
sleep-staging-fragmentation/
├── README.md
├── requirements.txt
├── notebooks/
│   ├── 01_data_loading_and_epoching.ipynb
│   ├── 02_baseline_sleep_staging_clean.ipynb
│   └── 03_fragmentation_metrics.ipynb
├── data/
│   ├── raw/
│   │   └── sleep_edf/
│   │       └── sleep-cassette/
│   └── processed/
├── figures/
└── models/

## Notebooks
01_data_loading_and_epoching.ipynb

Loads PSG and hypnogram EDF files, maps annotations to 5 sleep stages, and creates a 30-second epoch-level dataset.

Main outputs:

epoch-level sleep stage labels
hypnogram visualization
processed epoch index table
02_baseline_sleep_staging_clean.ipynb

Builds a baseline sleep staging model using EEG spectral features extracted from each epoch.

Main steps:

EEG channel selection
bandpower feature extraction
subject-aware cross-validation
baseline Random Forest classifier
confusion matrix and classification report
03_fragmentation_metrics.ipynb

Computes fragmentation-related sleep metrics from true and predicted stage sequences.

Main outputs:

stage transition counts
wake intrusions
fragmentation index
true vs predicted fragmentation comparison plots
Current baseline result

The current mini-baseline was trained on a small subset of subjects and sampled epochs to validate the end-to-end pipeline.

Observed pattern:

best performance on Wake and N3
moderate performance on N2
weaker performance on REM
poorest performance on N1

This pattern is expected in baseline sleep staging because N1 is both rare and difficult to separate from neighboring stages.

Why this project matters

This project demonstrates several capabilities relevant to neurotech and computational neuroscience roles:

working with raw physiological data
building reproducible preprocessing pipelines
extracting interpretable signal features
training and evaluating baseline ML models
translating predictions into clinically meaningful summary metrics
Limitations
current modeling uses a mini-subset for pipeline validation
only a baseline classical ML approach is included so far
no deep learning model has been added yet
the project is exploratory and not intended for clinical use
Next steps

Planned extensions:

scale the baseline to more Sleep-EDF subjects
compare Random Forest with logistic regression and deep learning baselines
improve performance on minority stages such as N1
extend fragmentation analysis to larger subject cohorts
add subject-level error analysis and true-vs-predicted hypnogram comparisons
Tech stack
Python
pandas
numpy
matplotlib
scipy
scikit-learn
mne

Project positioning

This repository should be interpreted as an exploratory neurotech portfolio project focused on sleep signal analytics, baseline staging, and downstream sleep-quality metrics.
