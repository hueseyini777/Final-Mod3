# Notebook 03 Review: Test the API

## 1. Objective

This notebook focuses on validating the local API using automated tests. The goal is to protect the service from regressions by checking that the main endpoints behave as expected.

## 2. Why this step matters

Once the model is running through the API, it is important to verify behavior consistently. Without tests, small changes could silently break request handling or response formatting.

This step helps confirm that:

- the service starts correctly,
- requests are parsed properly,
- responses are returned in the right format,
- invalid or empty batch requests are handled safely.

---

## 3. Included test file

The project includes the test file:

- `tests/test_app.py`

The current test suite checks four main behaviors:

1. `GET /` returns the expected health message.
2. `POST /predict` returns the request payload plus a prediction field.
3. `POST /predict_batch` returns one prediction per input ride.
4. An empty list for `POST /predict_batch` returns an empty response without loading the model.

These tests keep the workflow focused on API behavior rather than requiring a live MLflow server for every check.

---

## 4. Run the tests

From the repository root, run:

```bash
uv run python -m pytest
```

This is the preferred command because it ensures the repository root is correctly included in Python's import path.

Expected result:

- all tests pass,
- the final output ends with `4 passed`.

---

## 5. What the tests validate

### GET /

Confirms the API is live and the root route is wired correctly.

### POST /predict

Checks that the API accepts a valid payload and responds with a prediction value in the correct structure.

### POST /predict_batch

Verifies that multiple inputs are accepted and that the result ordering matches the request ordering.

### Empty batch request

Ensures the API handles empty requests quietly and efficiently without unnecessary model loading.

---

## 6. Why testing is valuable in MLOps

This notebook demonstrates a simple but important principle: even a working model service should be protected by automated checks.

Testing is especially useful when you want to:

- add new endpoints,
- adjust request validation,
- change response structures,
- refactor prediction logic without breaking behavior.

---

## 7. Deliverable checklist

A clean repository state after testing should include:

- the route visible in `/docs`,
- all tests passing,
- the behavior described in project notes,
- compatibility with the local MLflow setup already completed.

---

## 8. Final trainer-ready conclusion

Notebook 03 is the quality-control step in the workflow. It validates that the API behaves correctly under normal and edge-case requests and protects the service from future regressions.

This is a practical reminder that a deployed model is not only about serving predictions; it is also about making sure the service remains reliable, predictable, and maintainable over time.
