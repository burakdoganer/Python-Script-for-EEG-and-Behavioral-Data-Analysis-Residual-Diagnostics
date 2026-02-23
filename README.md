# Python-Script-for-EEG-and-Behavioral-Data-Analysis-Residual-Diagnostics
Python scripts for analyzing EEG (upper frontal alpha power) and behavioral (ad-watch duration) data from a Reels advertising avoidance study (N=84, 522 ad exposures). Includes mixed linear models, OLS/WLS regression, residual diagnostics, brand recall analysis, and within-subject normalization procedures. Built for iMotions-exported EEG data

# Overview
This repository contains the complete analysis pipeline for a PhD thesis investigating advertising avoidance in Instagram Reels using neurophysiological (EEG) and behavioral measures. The study examines how users cognitively and behaviorally avoid advertisements in short-form vertical video environments, measuring upper frontal alpha power as an indicator of cognitive avoidance and ad-watch duration for behavioral avoidance.

# Repository Structure
**01. initial_data_cleaning_ipynb:** Initial data cleaning pipeline: loads iMotions-exported EEG data, filters valid segments, removes excluded participants (n=6), scraps first/last segments, encodes ad indicators and recall variables, and exports the cleaned dataset for downstream analysis.

**02. data_analysis_pipeline_final.ipynb** : Main analysis pipeline: data preparation, hypothesis testing (H1–H3), and residual diagnostics. Includes mixed linear models for cognitive avoidance (EEG alpha), OLS/WLS regressions for behavioral avoidance (ad-watch duration), GEE for brand recall, LOSO sensitivity analysis, VIF checks, and publication-ready figures.

# Hypotheses Tested
**H1a:** Advertisements trigger attention inhibition (increased upper frontal alpha power)
**H1b:** Mean ad-viewing duration falls betweeen established avoidance thresholds
**H1c:** Association between cognitive and behavioral avoidance
**H2a/H2c:** Effect of ad clutter and ad position on cognitive avoidance (alpha power)
**H2b/H2d:** Effect of ad clutter and ad position on behavioral avoidance (viewing duration)
**H3a–H3e:** Predictors of brand recall (alpha power, viewing duration, clutter, position, and the interaction between clutter:position)

# Statistical Methods
**Mixed Linear Models** : Ads vs. content comparison (H1a); clutter × position effects (H2a–H2d)
**OLS & WLS Regression** : Robustness checks with cluster-robust standard errors
**GEE (Binomial)** : Brand recall prediction with exchangeable correlation structure
**LOSO Sensitivity Analysis** : Leave-one-subject-out stability check for GEE coefficients
**Residual Diagnostics** : Q-Q plots, residuals vs. fitted, scale-location plots, VIF tables
**Pseudo R²** : Marginal and conditional R² following Nakagawa & Schielzeth (2013)

# Key Variables
**ln_upper_alpha_frontal_mean** : Natural log-transformed mean upper alpha power across 7 frontal channels (F7, AF7, Fp1, Fpz, Fp2, AF8, F8)
**log_duration** : Log10-transformed segment viewing duration (ms)
**n_ads_z** : Z-scored total number of ads per participant (ad clutter)
**ad_position_c** : Within-subject centered ad position (sequential order)
**is_recall** : Binary brand recall outcome (1 = recalled, 0 = not recalled)

# DATA
Raw data was not included in this file due to an NDA. *preprocessed_eeg_data_20251209_163948.xlsx* was exported iMotions EEG processing software as input to the cleaning script, which produces eeg_segment_clean.xlsx for the main analysis pipeline.
