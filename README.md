# Optuna_Tiral_Timeout
When a trial starts and hangs without producing any intermediate values, it neither gets pruned nor times out. As a result, this hangs the whole process, eventually consuming all available CPU cores, leading to 100% CPU usage.
