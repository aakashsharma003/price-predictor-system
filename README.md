# Price Predictor System - Setup Guide

## Prerequisites
Make sure you have the following installed before proceeding:
- Python (>=3.8)
- Pip (latest version)
- Virtual Environment (`venv`)
- ZenML
- MLflow

## Step 1: Create a New Folder
Create a new folder to contain the project and navigate into it:
```sh
mkdir price_predictor_system
cd price_predictor_system
```

## Step 2: Set Up a Virtual Environment
### On Mac:
```sh
python3 -m venv vnv
```

### On Windows:
```sh
python -m venv vnv
```

## Step 3: Activate the Virtual Environment
### On Mac:
```sh
source vnv/bin/activate
```

### On Windows:
```sh
vnv\Scripts\activate
```

Once activated, you should see `(vnv)` at the beginning of your terminal prompt.

## Step 4: Install Required Packages
Make sure you have a `requirements.txt` file with the necessary dependencies. Install them using:
```sh
pip install -r requirements.txt
```

### Example `requirements.txt` File:
```
zenml
mlflow
pandas
numpy
scikit-learn
matplotlib
```

## Step 5: Install ZenML Integrations
ZenML requires specific integrations for MLflow. Install them using:
```sh
zenml integration install mlflow -y
```

## Step 6: Configure ZenML Stack
ZenML requires a stack configuration for MLflow experiment tracking and model deployment. Run the following commands:
```sh
zenml experiment-tracker register mlflow_tracker --flavor=mlflow
zenml model-deployer register mlflow --flavor=mlflow
zenml stack register local-mlflow-stack -a default -o default -d mlflow -e mlflow_tracker --set
```

## Step 7: Running the Project
To run the project, execute the following command:
```sh
python run_deployment.py
```

Make sure the virtual environment is activated before running any command.

---

### Notes:
- Always activate the virtual environment before running the project.
- Ensure that all dependencies are installed correctly.
- If you encounter any errors, check the installed packages using:
  ```sh
  pip list
  ```

