# Tutorial of Machine Learning in Metabolomics 

Welcome! This repository is a step-by-step beginner’s guide to using machine learning in metabolomics, with a specific focus on data processing and interpretation. You do not need much coding experience to get started. All instructions are written for beginners.

---

## What is This?

This tutorial will help you:
- Prepare and clean metabolomics data
- Train and evaluate machine learning models
- Understand and interpret model results

You will use interactive notebooks (Jupyter Notebooks) that let you run code and see results immediately, with explanations at every step.

---

## What You Need

**1. Python 3.8 or higher**
  - If you do not have Python, you can either download and install it from [python.org](https://www.python.org/downloads/) or install the Anaconda distribution (recommended for beginners).

**2. (Recommended) Install Anaconda**
  - Anaconda is a free distribution of Python that includes Jupyter Notebook and many scientific libraries. It makes setup easier for beginners.
  - Download the installer for your operating system from: [https://www.anaconda.com/products/distribution](https://www.anaconda.com/products/distribution)
  - Run the installer and follow the instructions (default options are fine).
  - After installation, you can open the "Anaconda Prompt" (Windows) or use your terminal (Mac/Linux) to continue.

**3. Jupyter Notebook**
  - If you installed Anaconda you already have Jupyter. Simply activate (or open) your Anaconda environment and run:
    ```bash
    jupyter lab   # or: jupyter notebook
    ```
  - If a browser does not open automatically, copy the URL with the token from the terminal into your browser.
  - For remote servers (optional): run `jupyter lab --no-browser --port 8888` remotely and SSH tunnel: `ssh -N -L 8888:localhost:8888 user@remote_host` then open http://localhost:8888.

---

## How to Set Up (Step by Step)


### 0. Install Git Bash (Windows Only)

If you are using Windows, it’s recommended to install Git Bash. This gives you a terminal similar to Mac/Linux and makes following the instructions easier.

1. Download Git Bash from the official website: [https://gitforwindows.org/](https://gitforwindows.org/)
2. Run the installer and follow the prompts (default options are fine).
3. After installation, you can open “Git Bash” from your Start menu.

If you are on Mac or Linux, you already have a terminal installed.

---

### 1. Download the Tutorial

Click the green “Code” button on this page and choose “Download ZIP”. Unzip the file to a folder on your computer.

Or, if you know how to use git:
```bash
git clone https://github.com/HuanLab/ML4MassSpec.git
```

### 2. Open a Terminal or Command Prompt

- **Windows:** Search for “Anaconda Prompt” or “Command Prompt” in your Start menu.
- **Mac:** Open “Terminal” from Applications > Utilities.
- **Linux:** Open your usual terminal.

Use the `cd` command to go to the folder where you unzipped or cloned the tutorial.

Examples (copy one that matches your system):

- Windows (if you downloaded a ZIP to Downloads):
  ```bat
  cd "C:\Users\YourName\Downloads\ML4MassSpec"
  ```
  If you cloned with `git clone` in your home folder, it likely created a folder named `ML4MassSpec` there:
  ```bat
  cd "C:\Users\YourName\ML4MassSpec"
  ```

- macOS:
  ```bash
  cd ~/Downloads/ML4MassSpec
  # or, if you cloned in your home folder
  cd ~/ML4MassSpec
  ```

- Linux:
  ```bash
  cd ~/Downloads/ML4MassSpec
  # or, if you cloned in your home folder
  cd ~/ML4MassSpec
  ```

Tips for beginners:
- Paths with spaces must be quoted, e.g., `cd "C:\Users\Your Name\Documents\ML4MassSpec"` or `cd "/Users/Your Name/ML4MassSpec"`.
- Press the Tab key after typing part of a folder name to auto-complete.
- After changing directory, you can run `pwd` (macOS/Linux) or `cd` (Windows) to confirm your current folder.

### 3. (Optional) Create and Activate a Virtual Environment

Creating a separate environment keeps this tutorial’s packages isolated and avoids conflicts.

Option A — Built-in Python venv (works without Anaconda):

- macOS/Linux:
  ```bash
  python3 -m venv .venv
  source .venv/bin/activate
  ```
- Windows (Command Prompt or PowerShell):
  ```bat
  python -m venv .venv
  .venv\Scripts\activate
  ```

Option B — Conda (if you use Anaconda/Miniconda):
```bash
conda create -n ml4ms python=3.10 -y
conda activate ml4ms
```

How to know it worked: your terminal prompt will start with the environment name, like `(ml4ms)` or `(.venv)`.

If you prefer not to use a virtual environment, you can skip this step.

### 4. Install All Required Packages

This tutorial uses several Python libraries. You can install them all at once using the provided requirements file. Just copy and paste this command:

```bash
pip install -r requirements.txt
```

If you see an error about `pip` not being found, try `python -m pip install -r requirements.txt` instead.

If you are using Anaconda, you can also use:
```bash
conda install --file requirements.txt
```

Optional but helpful:
- Upgrade pip first if installation complains:
  ```bash
  python -m pip install --upgrade pip
  ```
- If you created a virtual environment, ensure it’s activated before running `pip`.

### 5. Start Jupyter Notebook

In the same terminal, type:
```bash
jupyter notebook
```
This will open a new window in your web browser.

If you see an error, make sure you installed Jupyter as shown above.

---

## How to Use the Tutorial

1. In the Jupyter window, open the `notebooks/` folder.
2. Start with `1_Data_Preparation.ipynb`.
3. Read the instructions in each notebook cell, then click “Run” (the ▶ button) to execute the code and see the results.
4. Work through the notebooks in order:
    - 1_Data_Preparation.ipynb
    - 2_Model_Training.ipynb
    - 3_Model_Evaluation.ipynb
    - 4_Model_Interpretability.ipynb

All notebooks load the dataset directly from Hugging Face (CSV files hosted on the Hub). If network access is restricted, you can also download the CSVs and point the paths locally. See the dataset link below.

If you get stuck, read the comments and explanations in each cell. Most steps are explained in plain language.

---

## Dataset on Hugging Face

This tutorial uses data hosted on the Hugging Face Hub:

- Dataset: https://huggingface.co/datasets/chen1028/Cl-Containing-Compound

In code, the notebooks load the CSV splits like:

- Train: hf://datasets/chen1028/Cl-Containing-Compound/train.csv
- Test:  hf://datasets/chen1028/Cl-Containing-Compound/test.csv

If the hf:// scheme is unavailable in your environment, the notebooks automatically fall back to https://huggingface.co/datasets/chen1028/Cl-Containing-Compound/resolve/main/train.csv (and test.csv).

---

## What’s in Each Notebook?

### 1. Data Preparation
Learn how to load, clean, and prepare metabolomics data for machine learning. Topics include:
- Loading and exploring datasets
- Splitting data into training, validation, and test sets
- Handling missing values
- Feature engineering and scaling
- Dealing with imbalanced datasets

### 2. Model Training
Understand how to choose and train machine learning models:
- Selecting models
- Hyperparameter tuning (Grid Search, Random Search)
- Cross-validation
- Model complexity

### 3. Model Evaluation
Learn how to measure model performance:
- Classification metrics (accuracy, precision, recall, F1-score)
- Overfitting and underfitting
- Comparing models
- Visualizing results

### 4. Model Interpretability
See how to interpret and explain model predictions:
- White box vs. black box models
- Feature importance
- SHAP (Shapley Additive Explanations)
- Practical interpretation tips

---

## Troubleshooting & Tips

- If you see an error about a missing package, double-check you ran `pip install -r requirements.txt`.
- If Jupyter Notebook does not open, try closing and reopening your terminal, or restarting your computer.
- If you are new to Python, these beginner guides may help:
    - [Python.org Beginner's Guide](https://docs.python.org/3/tutorial/index.html)
    - [W3Schools Python Tutorial](https://www.w3schools.com/python/)
  For more help, search for the error message online—many answers are available on Stack Overflow.

---

## Contact & Support

If you have questions or suggestions, please open an issue on the GitHub repository or email the maintainer at Application tasks chenzhao@ece.ubc.ca (Chen Zhao) and thuan@chem.ubc.ca (Tao Huan).
