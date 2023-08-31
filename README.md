# Optuna_Tiral_Timeout

Issue Title: Need for Trial Timeout Feature in Optuna to Handle Hanging Trials
Issue Description:
I am fairly new to coding, but I am currently captivated by Optuna's capabilities for hyperparameter tuning. I've encountered an issue related to pruners like Hyperband, which rely on intermediate values to prune trials.

The Problem:
When a trial starts and hangs without producing any intermediate values, it neither gets pruned nor times out. As a result, this hangs the whole process, eventually consuming all available CPU cores, leading to 100% CPU usage. Over time, the number of such "hanging" trials keeps increasing, bringing the optimization process to a standstill.

I noticed this issue on the Optuna dashboard's trial examiner. For instance, while the study was in the 300s trials, a trial (#13 in this case) was still running without being pruned or failed. Manually failing the trial made no difference.

Expected Behavior:
Ideally, a trial that hangs and does not produce intermediate values within a specified time frame should be automatically pruned or timed out. This would free up CPU cores for other trials and ensure smoother execution of the hyperparameter optimization process.

Current Workaround:
As I understand, Optuna doesn't currently offer a trial-specific timeout feature; it only provides a timeout option for the entire study. To work around this limitation, I created a custom pruner by extending BasePruner or MedianPruner, and used Python's multiprocessing library to allocate each trial to a separate CPU core while monitoring its execution time. Unfortunately, this solution didn't yield satisfactory results and also introduced performance degradation.

Suggested Improvement:
I believe it's crucial for the Optuna team to introduce a trial-specific timeout feature to handle such scenarios.

Code and Dataset:
Here, I have attached my code and dataset to reproduce this issue. I've only enabled SVC model usage, as trials seem to execute relatively quickly initially but slow down as time progresses.


