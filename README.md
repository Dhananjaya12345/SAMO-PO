# SAMO-PO: Security-Aware Multi-Objective Prompt Optimization

This repository contains the official implementation and benchmark dataset for the paper: 
**"Security-Aware Multi-Objective Prompt Optimization for LLM Agents: Balancing Task Performance and Adversarial Robustness."**

## 📌 Overview
Standard Automated Prompt Optimization (APO) improves task efficiency but often strips away safety guardrails, making LLM agents vulnerable to adversarial attacks. **SAMO-PO** is a black-box evolutionary framework that co-optimizes an agent's system prompt across three objectives:
1. **Task Utility** (Benign task execution)
2. **Security Robustness** (Resistance to direct and indirect prompt injections)
3. **Token Complexity** (Prompt length penalty)

The code in this repository reproduces all the empirical results reported in the paper, including Tables II, III, IV, and Figure 2 (the 3D Pareto Frontier).

## 💻 Hardware & Environment Requirements
The experiments were conducted using free cloud GPUs. To run this code, you will need:
*   **GPU:** NVIDIA Tesla T4 (16 GB VRAM) or equivalent. The code uses `float16` precision and explicitly checks for CUDA availability.
*   **Python:** 3.8+
*   **Key Libraries:** `torch`, `transformers`, `pandas`, `numpy`, `scikit-learn`, `matplotlib`

*Note: Because the framework runs two open-weight models locally (Qwen2.5-3B-Instruct and SmolLM2-1.7B-Instruct), an environment with at least 12GB of VRAM is highly recommended.*

## 🚀 How to Run (Google Colab)

The easiest way to reproduce the results is via Google Colab:

1. Open [Google Colab](https://colab.research.google.com/).
2. Upload the `SAMO_PO_Implementation.ipynb` notebook (provided in this repository).
3. **Crucial:** Go to `Runtime` -> `Change runtime type` -> Select **T4 GPU** -> Click `Save`.
4. Run the cells sequentially from top to bottom.
5. The script will automatically download the required models from HuggingFace, run the 4-generation evolutionary search, and evaluate the baselines.

## 📊 Reproducible Outputs
Upon successful execution, the notebook will generate the following files in your working directory:
*   `IEEE_SAMO_All_Candidates.csv`: Logs of all evaluated prompts across all 4 generations.
*   `IEEE_SAMO_Pareto_Front.csv`: The final non-dominated Pareto-optimal candidates.
*   `IEEE_Table2_Baselines.csv`: Main results comparing SAMO-PO against Manual, Task-Only APO, Static Hardened, and External Guardrail baselines.
*   `IEEE_Table3_Ablations.csv`: Ablation results showing the impact of the token penalty and weight sensitivity.
*   `IEEE_Judge_Audit.csv`: Reliability metrics (Cohen's Kappa, FPR, FNR) for the multi-model consensus judge.
*   `IEEE_Fig2_Pareto_Frontier.pdf` / `.png`: High-resolution (300 DPI) scatter plot mapping the utility-security trade-off space.

## 📝 Citation
If you use this code or dataset in your research, please cite our paper:

```bibtex
@inproceedings{2026SAMOPO,
  title={Security-Aware Multi-Objective Prompt Optimization for LLM Agents: Balancing Task Performance and Adversarial Robustness},
  author={Dhananjaya Lahiru Bandara},
  booktitle={Proceedings of the IEEE SCSE Conference},
  year={2026},
  doi={ DOI: 10.5281/zenodo.24406265} 
}
