# MLOps-Pipeline-DVC-S3
This is for understanding of creating a Machine Learning Pipeline and experimenting around it using DVC for experiment tracking and Data versioning using AWS S3.

# 📦 MLOps Pipeline with DVC & S3 - Day 3

This repository showcases an end-to-end Machine Learning Pipeline built using MLOps best practices. It includes automation, modular components, experiment tracking, and data versioning with AWS S3 and DVC.

---

### 🧾 Logging Concepts
* Logging is handled with two handlers:

- Console Handler: Logs printed in terminal

- File Handler: Logs saved in /logs/

#### Log Levels:
* DEBUG: Internal events for debugging

* INFO: General information (e.g., task completed)

* WARNING: Unexpected behavior but not critical

* ERROR: Operation failed

* CRITICAL: Severe errors, system failure

---

## 🔁 ML Pipeline Components

- **Data Ingestion**
- **Preprocessing**
- **Feature Engineering**
- **Model Training**
- **Model Evaluation**

Each component is modularized and orchestrated using DVC pipelines.

---

## 🧠 What I Practiced Today

### 🧩 End-to-End Pipeline
- Structured code into modules (`src/`)
- Included `logging` and `exception` handling
- Configurable pipeline using `params.yaml`

### ⚙️ Automating with DVC
```bash
dvc init
dvc stage add -n data_ingestion -d src/data_ingestion.py -o data/raw_data.csv python src/data_ingestion.py
dvc repro
```

🛠️ Using params.yaml
### Centralized config management for all stages:

```yaml
data_source: "path/to/data"
model:
  type: "RandomForest"
  params:
    n_estimators: 100
```

### 📊 Experiment Tracking with `dvclive`
```python
from dvclive import Live
live = Live()
live.log_metric("accuracy", 0.87)
```

### ☁️ AWS S3 Setup for DVC
```bash
dvc remote add -d myremote s3://mybucket/mlops
dvc push
```

logger.debug("Loading config file...")
logger.info("Data ingestion completed")
logger.error("File not found")
```  
