# Notebook 01 Review: Run MLflow Locally

## 1. Objective

This first notebook introduces the local MLflow environment that supports the full machine learning deployment workflow. The aim is to start a local tracking server, confirm it is working, and train/register a demo model so it can later be used by the API.

## 2. Why this step matters

This is the foundation of the project. Without a running MLflow server:

- model training cannot be tracked,
- experiment metadata cannot be stored,
- the model registry cannot be used,
- the FastAPI service cannot load the production version of the model.

In practical terms, this step proves that the local MLOps environment is ready before building the service layer.

---

## 3. Prerequisites

Before starting, make sure the following are in place:

- the repository has been cloned locally,
- dependencies have been installed with `uv sync`,
- the `.env` file exists,
- VS Code is opened from the project root,
- Git Bash is used on Windows instead of PowerShell.

The important environment variables are:

- `MLFLOW_TRACKING_URI=http://127.0.0.1:5000`
- `REGISTERED_MODEL_NAME=lr-ride-duration`
- `MODEL_ALIAS=production`

---

## 4. Step-by-step procedure

### Step 1: Open the project folder

```bash
cd <repo-name>
```

### Step 2: Install the project dependencies

```bash
uv sync
```

This creates the project virtual environment and installs the required libraries, including MLflow, FastAPI, scikit-learn, pandas, and pytest.

### Step 3: Create the environment file

```bash
cp .env.example .env
```

Check that the file includes the local MLflow settings above. This keeps the notebook and app pointed to the same tracking server.

### Step 4: Open the repository in VS Code

```bash
code .
```

Open the project root in VS Code and select the Python environment created by `uv sync` as the notebook kernel.

### Step 5: Start the MLflow server

Run the following command from the repository root:

```bash
uv run mlflow server \
  --host 127.0.0.1 \
  --port 5000 \
  --backend-store-uri sqlite:///mlflow.db \
  --default-artifact-root ./mlartifacts \
  --allowed-hosts "localhost:5000,127.0.0.1:5000,host.docker.internal:5000"
```

This starts the local tracking server at:

- `http://127.0.0.1:5000`

The server keeps experiment metadata in `mlflow.db` and stores artifacts in `mlartifacts/`.

### Step 6: Verify the server is running

Open the MLflow UI in the browser and check that:

- the tracking server loads successfully,
- the local experiment page is accessible,
- the storage files appear in the repo.

### Step 7: Run the model registration notebook

Open the notebook:

- `src/register_mlflow_model.ipynb`

Then run the full workflow. The notebook should:

1. build a small taxi-duration dataset,
2. engineer the required features,
3. train a regression model,
4. log parameters and metrics to MLflow,
5. register the model in the Model Registry,
6. assign the alias `production`.

---

## 5. What to expect after the notebook runs

A successful run should show in the MLflow UI:

- a new experiment run,
- metrics such as MAE,
- model artifacts saved in `mlartifacts/`,
- a registered model named `lr-ride-duration`,
- the alias `production` assigned to the chosen model version.

This is the key success point of the notebook: the model is no longer just trained locally; it is now available to downstream services through the registry.

---

## 6. Evidence to show trainers

During presentation, it is useful to show:

- the MLflow URL in the browser,
- the experiment name and run details,
- the registered model name,
- the `production` alias,
- the local files `mlflow.db` and `mlartifacts/`.

This demonstrates that the environment is functioning and the model is ready for service deployment.

---

## 7. Common issues and fixes

### Issue: MLflow server will not start

Possible causes:

- wrong working directory,
- port 5000 already in use,
- dependencies not installed,
- missing environment values.

Fix:

- ensure you are in the repository root,
- check whether port 5000 is free,
- run `uv sync` again,
- restart the MLflow server.

### Issue: notebook kernel is missing

Fix:

- reopen VS Code from the repo root,
- choose the environment created by `uv sync`,
- restart the notebook session.

### Issue: model does not appear in MLflow UI

Fix:

- confirm the server is still running,
- check that the tracking URI points to `http://127.0.0.1:5000`,
- rerun the notebook cells from the start.

---

## 8. Final trainer-ready conclusion

Notebook 01 is the setup and validation step that powers the rest of the project. It proves that the repository is correctly configured, the local MLflow server is active, and the demo taxi-duration model has been trained and registered in the Model Registry.

This is the point where the project transitions from experimentation to deployment readiness, because the model is now available for use by the API in the next stage of the workflow.
