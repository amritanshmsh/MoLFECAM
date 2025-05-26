# 🧬 Molformer Continual Learning (MoLFECAM)

MoLFECAM is a **continual learning-based molecular property prediction system** built using the MoLFormer Transformer, EWC (Elastic Weight Consolidation), and a Feature Covariance-Aware Mahalanobis metric. It is benchmarked on critical biomedical datasets like BBBP, Tox21, ToxCast, SIDER, Bitter, Sweet, NP, and ClinTox.

---

## 🌟 Key Highlights

- **Zero Forgetting Measure (FM ≈ 0.0000)** across all tasks.
- **Exemplar-Free Class Incremental Learning** (No replay buffer).
- Based on **MoLFormer + MLP** classifier with frozen molecular representations.
- Integrates **task-aware regularization** using Mahalanobis feature alignment.

---

## 🚀 Product Overview

This repository provides a research-grade **prototype** of a **local inference tool** to incrementally train and evaluate molecular property prediction models **on-device**. It's designed for:

- **Medicinal chemistry researchers**
- **AI+Biotech product teams**
- **Federated/local pharma AI solutions**

The prototype currently runs locally and trains across 8 molecular tasks with structured outputs.

---

## 🖼️ System Workflow

![Model Workflow](./docs/molfecam_flowchart.png)

1. **Preprocessing SMILES → Tokenization**
2. **Feature extraction via frozen MoLFormer**
3. **Classifier trained with EWC regularization**
4. **Mahalanobis distance used to align task-specific statistics**
5. **Evaluation using FM and AAA**

---

## 📂 File Structure

```bash
Molformer/
├── data/                  # All 8 datasets in CSV (BBBP, Tox21, etc.)
│   ├── BBBP.csv
│   ├── Tox21.csv
│   └── ...
├── molfecam.py            # Main training + evaluation script
├── README.md              # This file
```

---

## 📦 Installation

```bash
git clone https://github.com/yourusername/molformer.git
cd molformer
pip install -r requirements.txt
```

---

## ▶️ Running the Prototype

Run the full training and evaluation loop:

```bash
python molfecam.py
```

This will sequentially train on all tasks and print:

- Accuracy per task
- Anytime Average Accuracy (AAA)
- Forgetting Measure (FM)

---

## 📊 Metrics

| Metric | Description |
|--------|-------------|
| **Accuracy** | Standard classification accuracy |
| **FM** | Measures degradation across tasks |
| **AAA** | Overall incremental performance |

---

## 🧠 Future Plans

- Convert to a web interface using Streamlit
- Add visual dashboards for task-wise progression
- Enable fine-tuning with small datasets

---

## 🤝 Contribute

If you are interested in turning this into a product-level system, feel free to open issues or discuss your use-case!

---

## 📌 Reference

Based on:
- MoLFormer by IBM Research
- Elastic Weight Consolidation (Kirkpatrick et al.)