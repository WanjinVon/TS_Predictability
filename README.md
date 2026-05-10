# Beyond Model Ranking: Predictability-Aligned Evaluation for Time Series Forecasting

This repository contains the official source code and experiments for the paper "Beyond Model Ranking: Predictability-Aligned Evaluation for Time Series Forecasting (ICML 2026)".


## Abstract
In the era of increasingly complex AI models for time series forecasting, progress is often measured by marginal improvements on benchmark leaderboards.
However, this approach suffers from a fundamental flaw: standard evaluation metrics conflate a model's performance with the data's intrinsic unpredictability.
To address this pressing challenge, we introduce a novel, predictability-aligned diagnostic framework grounded in spectral coherence.
Our framework makes two primary contributions: 
the **Spectral Coherence Predictability (SCP)**, a computationally efficient ($O(N\log N)$)  and task-aligned score that quantifies the inherent difficulty of a given forecasting instance, and the **Linear Utilization Ratio (LUR)**, a frequency-resolved diagnostic tool that precisely measures how effectively a model exploits the linearly predictable information within the data.
We validate our framework's effectiveness and leverage it to reveal two core insights. First, we provide the first systematic evidence of ``predictability drift'', demonstrating that a task's forecasting difficulty varies sharply over time. 
Second, our evaluation reveals a key architectural trade-off: complex models are superior for low-predictability data, whereas linear models are highly effective on more predictable tasks.
We advocate for a paradigm shift, moving beyond simplistic aggregate scores toward a more insightful, predictability-aware evaluation that fosters fairer model comparisons and a deeper understanding of model behavior.


## 🚀 Getting Started


1. Download Datasets
Download the benchmark datasets from [Google Drive](https://drive.google.com/file/d/1l51QsKvQPcqILT3DwfjCgx8Dsg2rpjot/view?pli=1). After downloading, unzip and place them into the ./datasets directory.

2. Install Dependencies
Install the required Python packages by running the following command:
```Bash
pip install -r requirements.txt
```

3. Run Experiments
To run the experiments, navigate to the desired model directory and execute the corresponding script. For example, to run the experiments for the ETTh1 dataset with the DLinear model, use the following command:
```Bash
cd DLinear
bash ./scripts/ETTh1.sh 0
```

4. Evaluate Predictability 
To evaluate the predictability of the models, run the following command:
```Bash
bash ./scripts/eval_ETTh1.sh
```
Pay attention to the parameters to ensure that the function can load the correct weights.

4. Advanced Diagnostic Analysis

Linear Utilization Ratio (LUR)
To compute the Linear Utilization Ratio (LUR) for a trained model and analyze its frequency-band performance, run the ``run_LUR_bands.py`` script. You may need to configure the script to point to the correct model checkpoint.

Predictability Drift
To reproduce the predictability drift analysis, execute the ``run_predictability_drift.py`` script. This will generate the results showing how forecasting difficulty varies over time for a given dataset.



## 🏛️ Code Structure

The core logic of our framework is implemented in the following functions:

- evaluate_predictability(): Computes the Spectral Coherence Predictability (SCP) score. 
- evaluate_band_LUR(): Calculates the Linear Utilization Ratio (LUR) across frequency bands.
- evaluate_band_predictability_dualaxis(): Implements the analysis for predictability drift.

Located in ./[model_name]/exp/exp_main.py.


## 🙏  Acknowledgements

We appreciate the following GitHub repos a lot for their valuable code and efforts.

- PSloss: https://github.com/Dilfiraa/PS_Loss
- iTransformer: https://github.com/thuml/iTransformer
- PatchTST: https://github.com/yuqinie98/PatchTST
- TimeMixer: https://github.com/kwuking/TimeMixer
- DLinear: https://github.com/cure-lab/LTSF-Linear
- TimesNet: https://github.com/thuml/Time-Series-Library
