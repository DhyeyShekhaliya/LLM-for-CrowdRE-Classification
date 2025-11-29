# LLM-for-CrowdRE-Classification

This repository contains Jupyter notebooks and supplementary resources designed to reproduce experiments in software requirements classification using Large Language Models (LLMs). The workflow encompasses the categorization of LLMs, preprocessing and organization of requirement datasets, and the execution of classification experiments both locally and via Google Colab.

Contributors:
Dhyey Shekhaliya (PDEU)
Dr. Arpit Sharma (IISER Bhopal)

---

## 📋 Prerequisites

Before running the notebooks, please ensure you have completed the following:

1. **Clone the repository**

   ```bash
   git clone https://github.com/anonymousscot-jpg/LLM-for-CrowdRE-Classification.git
   cd LLM-for-CrowdRE-Classification
   ```

2. **Create and activate a Python virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate   # On Mac/Linux
   venv\Scripts\activate      # On Windows
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Prepare datasets**
   Place the following files in the project’s **root directory**:

   * `Open source llms-2.csv`
   * `requirements.csv`

---

##  Step-by-Step Experiment Workflow

The experiment is divided into three main notebooks. **Run them in order.**

---

### **Step 1: Create LLM Size Categories**

* **Notebook:** `llm_classification.ipynb`
* **Purpose:** Categorizes LLMs into five size groups: *Tiny, Small, Medium, Large, Ultra*.

**How to Use**

1. Open the notebook.
2. Run all cells sequentially.

**Expected Output**

* Scatter plot visualizing clusters.
* Categorized list of LLMs with assigned size categories.

---

### **Step 2: Prepare the Software Requirements Dataset**

* **Notebook:** `data.ipynb`
* **Purpose:** Processes raw CrowdRE dataset into a clean format.

**How to Use**

1. Open the notebook.
2. Run all cells.

**Expected Output**

* `requirements_merged.csv`
* `requirements_merged_cleaned.csv`
* `Data_for_llm.zip` (to be used in the next step)

---

### **Step 3: Run the Main Classification Experiment**

You have **two options** depending on your environment:

---

#### **Option A: Run on Google Colab**

* **Notebook:** `llm_crowdRE_Colab.ipynb`

**Instructions**

1. Run **Cell 1**: Installs Ollama and pulls models. *(Large downloads, requires stable internet & disk space)*
2. Run **Cell 2**: Upload `Data_for_llm.zip`.
3. Run **Cell 3**: Starts classification.

You will be prompted to choose the experiment type:

* Binary
* Tertiary
* Quaternary
* Quinary

---

#### **Option B: Run Locally**

* **Notebook:** `llm_ondevice.ipynb`

**Prerequisites**

* Install [Ollama](https://ollama.com/) on your machine.
* Pull the required model:

  ```bash
  ollama pull phi4-mini-reasoning:3.8b
  ```

**Instructions**

1. Open the notebook.
2. Update the `csv_path` inside the `Config` class to point to your `requirements_merged_cleaned.csv`.
3. Run all cells.

---

## 📊 Expected Results

After running the classification:

* A directory named `classification_results` (or similar) will be created.
* Inside, you’ll find:

  * `comprehensive_report.html` → Detailed performance metrics, charts, and analysis.
  * `summary_results.csv` and `detailed_results.csv` → Tabular results for further analysis.
  * `experiment_log.json` → Raw output logs.

⚠️ **Note:** Running the classification is computationally intensive and may take several hours.

---

## 📂 Repository Structure

```
├── data.ipynb
├── llm_classification.ipynb
├── llm_crowdRE_Colab.ipynb
├── llm_ondevice.ipynb
├── requirements.txt
├── requirements.csv        # (to be added by user)
├── Open source llms-2.csv  # (to be added by user)
└── README.md
```

