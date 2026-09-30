# Notebook 04 Review: Run the API in Docker

## 1. Objective

This notebook demonstrates how to package the FastAPI application into a Docker container and run it while still connecting to the local MLflow server running on the host machine.

## 2. Why this step matters

The local Python workflow proves the service works, but Docker adds realism and portability. This step shows how the same API can be run in a containerized environment while still using the model registered on the local MLflow server.

---

## 3. Build the Docker image

From the repository root, run:

```bash
docker build -t ml-api-local .
```

This builds the API image based on the repository's `Dockerfile`.

Expected result:

- the image builds successfully,
- the image appears in Docker as `ml-api-local`.

---

## 4. Run the container

Before starting the container, stop any local `uvicorn` process if it is already running on port 9696.

Then run:

```bash
docker run --rm -p 9696:9696 \
  --add-host=host.docker.internal:host-gateway \
  --env-file .env \
  -e MLFLOW_TRACKING_URI=http://host.docker.internal:5000 \
  -v "$PWD/mlartifacts:$PWD/mlartifacts" \
  ml-api-local
```

This command does three important things:

- exposes the API on port 9696,
- makes the container able to reach the MLflow server using `host.docker.internal`,
- mounts the local `mlartifacts` folder so the model can be loaded correctly.

---

## 5. Test the containerized API

After the container is running, send a request:

```bash
curl -X POST http://127.0.0.1:9696/predict \
  -H "Content-Type: application/json" \
  -d '{
    "ride_id": "docker-001",
    "PULocationID": 161,
    "DOLocationID": 236,
    "trip_distance": 4.2
  }'
```

This confirms the container can serve the same model endpoint as the local API.

---

## 6. Troubleshooting for Docker deployment

If the request fails, first confirm:

- the local MLflow server from Notebook 01 is still running,
- `.env` exists at the repository root,
- `mlartifacts/` exists and contains the model artifacts,
- port 9696 is not already occupied by a local app,
- Docker Desktop is running correctly.

On Windows, path handling for Docker can be more sensitive, so the volume mount may need adjustment depending on the environment.

---

## 7. What this step demonstrates

This notebook shows that the local model workflow is portable and can be run in a containerized environment without changing the core MLflow-based design.

It highlights three useful deployment points:

- the API can run as a local Python service,
- the same API can be packaged in Docker,
- containerized services can still reach host-side infrastructure such as MLflow.

---

## 8. Final trainer-ready conclusion

Notebook 04 completes the learning path by packaging the working API into Docker. It shows how to move from local execution to a containerized deployment while preserving access to the same local MLflow model registry.

This final step is important because it demonstrates that the project is not only functional in a developer environment, but also ready to be packaged and deployed in a more production-like setup.
