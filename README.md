# AIML Learning Repository 🧠🚀

Welcome to my Machine Learning and Artificial Intelligence learning repository! This monorepo serves as a structured playground where I explore data science, predictive modeling, and machine learning algorithms.

Each project is isolated with its own dependencies and python environments managed by [uv](https://github.com/astral-sh/uv), a fast Python package installer and resolver.

---

## 📂 Repository Structure

The repository contains the following learning projects:

```text
aiml/
├── .gitignore                   # Global ignore rules for Python, Jupyter, and ML files
├── README.md                    # Repository documentation (this file)
│
├── f1-winner-predictor/         # 🏎️ Formula 1 Winner Prediction Project
│   ├── data/                    # Dataset directory (raw CSVs ignored by Git)
│   │   ├── raw/
│   │   └── processed/
│   ├── models/                  # Saved model checkpoints (*.pkl, *.joblib)
│   ├── notebooks/               # Jupyter notebooks for exploration and training
│   ├── pyproject.toml           # Project configuration & dependencies
│   └── uv.lock                  # Lockfile for reproducible environment
│
└── titanic/                     # 🚢 Titanic Survival Prediction Project
    ├── data/                    # Dataset directory (ignored by Git)
    ├── 01_eda.ipynb             # Exploratory Data Analysis notebook
    ├── pyproject.toml           # Project configuration & dependencies
    └── uv.lock                  # Lockfile for reproducible environment
```

---

## 🛠️ Tech Stack & Dependencies

All projects utilize a modern Python data science ecosystem:

| Project | Core Purpose | Key Libraries |
| :--- | :--- | :--- |
| **`titanic`** | Binary classification to predict survival rate. | `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`, `plotly`, `jupyter` |
| **`f1-winner-predictor`** | Predict F1 race winners using historical race data. | `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `joblib`, `jupyter` |

---

## 🚀 Getting Started

This repository uses **`uv`** for extremely fast dependency installation. If you don't have `uv` installed, get it via curl:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### 1. Setting Up a Project

Navigate to either project folder to initialize the virtual environment and install dependencies:

```bash
# Go to a project directory
cd titanic

# Install all dependencies and create .venv
uv sync
```

### 2. Running Jupyter Notebooks

To start Jupyter within the project environment, run:

```bash
uv run jupyter notebook
```
This ensures Jupyter runs using the exact dependencies and Python version defined in `pyproject.toml`.

---

## 🧼 Clean Jupyter Notebook Workflow

Jupyter Notebooks (`.ipynb` files) store code execution history, cell outputs, and metadata. Committing notebooks with outputs results in:
* Large file sizes (especially when plots and data tables are embedded).
* Noisy Git diffs showing execution counts and metadata changes rather than code changes.

To maintain a clean notebook history for learning, follow these practices:

### Option A: Automatic Stripping (Recommended)
You can configure Git to automatically strip output cells from notebooks whenever you run `git commit`. The local notebook remains intact, but the version pushed to GitHub will be perfectly clean.

1. **Install `nbstripout`** in your toolchain or global environment:
   ```bash
   uv pip install --system nbstripout
   ```
2. **Enable it for this repository**:
   ```bash
   # Run from the root of the repository
   nbstripout --install
   ```

Now, Git will automatically clean notebooks before staging them!

### Option B: Manual Clearing
If you prefer not to use external tools, remember to clear outputs manually before saving and committing:
1. In Jupyter, go to the top menu.
2. Select **Kernel** ➡️ **Restart & Clear Output**.
3. Save the notebook and commit.

---

> [!NOTE]
> All raw datasets (`.csv`, `.xlsx`, etc.) and trained model files (`.pkl`, `.joblib`) are automatically ignored by `.gitignore` to keep the repository lightweight. Be sure to download the necessary datasets locally into the respective project `data/` folder before running the notebooks.
