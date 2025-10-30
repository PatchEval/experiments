# Submit to PatchEval Leaderboard

If you are interested in submitting your method (model/agent) and results to the [PatchEval](https://patcheval.github.io/) leaderboard, please follow these steps:

1. Fork and clone the [PatchEval repository](https://github.com/bytedance/PatchEval). Set up the evaluation environment as described in the [README.md](https://github.com/PatchEval/experiments/blob/main/README.md) file.

2. Within the repository, you can evaluate your own data using the provided script (e.g., `patcheval/evaluation/run_evaluation.py`).

    a. Prepare your patch data in the following format:

    ```json
    [
        {
            "cve": "CVE-ID",
            "fix_patch": "YOUR_PATCH (diff)"
        },
    ]
    ```

    b. Run the evaluation command:

    ```bash
    cd patcheval/evaluation
    python run_evaluation.py \
        --output example \
        --patch_file YOUR_PATCH_PATH \
    ```

3. In your submission folder, please include the following files:

    - `summary.json`: Evaluation results for all cases
    - `run_evaluation.log`: Log of the evaluation process
    - `your_patch.json`: Must contain at least the `cve` and `fix_patch` keys
    - `logs/`: PatchEval evaluation artifacts, containing the `patch` and `log` results for each CVE. The folder structure should be as follows:

    ```bash
    logs
    ├── CVE-ID
    │   ├── fix.patch
    │   └── success_output.log
    └── CVE-ID
        ├── error_output.log
        └── fix.patch
    ```

    - `trajs/`: (Optional) Reasoning traces showing how your agent solved each problem

4. Create a pull request to the `patcheval/experiments` [repository](https://github.com/patcheval/experiments) with your new folder.
