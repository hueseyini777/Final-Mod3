# Notebook 02 Review: Run the API Locally

## 1. Objective

This notebook focuses on serving predictions through a local FastAPI application. After the model is registered in MLflow, the API loads it from the MLflow Model Registry and exposes prediction endpoints so external clients can request ride-duration estimates.

## 2. Why this step matters

This is the first operational deployment step in the project. It transforms the trained and registered model into a usable service.

The API provides:

- a health endpoint,
- a single ride prediction endpoint,
- a batch prediction endpoint.

These endpoints make the model accessible to real applications without needing a full web frontend.

---

## 3. Project files used in this step

The local API lives in the `webservice_locally` package:

- `app.py` defines the FastAPI routes,
- `data_model.py` defines the request and response schema,
- `predict.py` loads the registered model and performs prediction logic.

These files work together to validate incoming data, prepare model features, and return prediction outputs.

---

## 4. Start the API locally

From the repository root, run:

```bash
uv run uvicorn webservice_locally.app:app --reload --port 9696
```

This starts the API at:

- `http://127.0.0.1:9696`

The interactive docs are available at:

- `http://127.0.0.1:9696/docs`

---

## 5. Routes available in the app

### GET /

Purpose:

- health check

This confirms the server is running and ready to accept requests.

### POST /predict

Purpose:

- score a single taxi ride

Example request:

```bash
curl -X POST http://127.0.0.1:9696/predict \
  -H "Content-Type: application/json" \
  -d '{
    "ride_id": "ride-101",
    "PULocationID": 161,
    "DOLocationID": 236,
    "trip_distance": 3.5
  }'
```

Expected response pattern:

```json
{
  "ride_id": "ride-101",
  "PULocationID": 161,
  "DOLocationID": 236,
  "trip_distance": 3.5,
  "predicted_duration": 16.88
}
```

### POST /predict_batch

Purpose:

- score multiple rides in one request

Example request:

```bash
curl -X POST http://127.0.0.1:9696/predict_batch \
  -H "Content-Type: application/json" \
  -d '[
    {
      "ride_id": "ride-201",
      "PULocationID": 161,
      "DOLocationID": 236,
      "trip_distance": 3.5
    },
    {
      "ride_id": "ride-202",
      "PULocationID": 142,
      "DOLocationID": 239,
      "trip_distance": 1.7
    }
  ]'
```

Expected behavior:

- the API returns one prediction object per input ride,
- the order of the response matches the input request order.

---

## 6. How the app loads the model

The service loads the registered model using the production alias from MLflow. This means the API is not using a local pickled file directly; it is pulling the latest model version associated with `production` from the registry.

This is important because it creates a clean deployment pattern:

- train the model,
- register it,
- assign the production alias,
- let the API fetch the model when needed.

---

## 7. Key checks before moving on

Before continuing, confirm the following:

- the MLflow server is still running,
- the notebook completed successfully,
- the registered model has the `production` alias,
- the API responds on port 9696,
- the `/docs` page loads correctly.

If a prediction fails, the first thing to check is whether the local MLflow server is still active and whether the model alias is present.

---

## 8. Suggested validation steps

For a clean local check, do the following:

- call `GET /` and confirm the service is alive,
- use `/docs` to inspect the request schema,
- test a few different trip distances,
- verify `POST /predict_batch` preserves input ordering,
- confirm the API can be called without restarting the service after a model is already registered.

---

## 9. Common issues and fixes

### Issue: model loading error

Likely cause:

- MLflow server is not running,
- the model was not registered correctly,
- the `production` alias is missing.

Fix:

- revisit the notebook setup,
- confirm the server is active,
- verify the model alias in MLflow.

### Issue: app does not start

Possible causes:

- dependency issue,
- port 9696 already in use,
- wrong environment selected.

Fix:

- make sure the repo environment is active,
- stop any existing process using the port,
- rerun the `uvicorn` command.

---

## 10. Final trainer-ready conclusion

Notebook 02 proves that the local MLflow model can be exposed as a real application endpoint. The FastAPI service loads the registered model from the MLflow registry and turns it into a predictable API for single or batch prediction requests.

This step is the bridge between model registration and operational deployment. It demonstrates how a registered model becomes a live service that can be tested and reused in downstream workflows.
