# The Fundemantal Prerequisites

## Section 1: Understanding Modeling, Model and Training

<style>
.prerequisite-slides {
  --ink: #203334;
  --accent: #167d78;
  --line: #8bb8af;
  --paper: #f2f7f4;
  --muted: #aebbb6;
  max-width: 760px;
  margin: 2rem auto;
  padding: 2rem;
  color: var(--ink);
  background: var(--paper);
  border: 1px solid #d5e3dd;
  border-radius: 12px;
  font-family: Georgia, "Times New Roman", serif;
}

.prerequisite-slides .slide-choice,
.metric-slides .slide-choice {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  clip-path: inset(50%);
}

.prerequisite-slides .slide {
  display: none;
  min-height: 220px;
  text-align: center;
}

#prereq-slide-1:checked ~ .slide-one,
#prereq-slide-2:checked ~ .slide-two,
#prereq-slide-3:checked ~ .slide-three,
#prereq-slide-4:checked ~ .slide-four {
  display: block;
}

#pattern-slide-1:checked ~ .pattern-one,
#pattern-slide-2:checked ~ .pattern-two,
#pattern-slide-3:checked ~ .pattern-three {
  display: block;
}

.prerequisite-slides .concept-row {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
  margin: 2rem 0;
}

.prerequisite-slides .concept {
  display: grid;
  place-items: center;
  min-width: 150px;
  min-height: 82px;
  padding: 0.75rem 1.25rem;
  border: 2px solid var(--line);
  border-radius: 4px;
  background: #fff;
  color: var(--ink);
  font-size: 1.35rem;
}

.prerequisite-slides .concept-row.dimmed .concept {
  border-color: var(--muted);
  background: #e1e6e3;
  color: #77827d;
}

.prerequisite-slides .service {
  display: grid;
  place-items: center;
  box-sizing: border-box;
  width: min(100%, 300px);
  min-height: 170px;
  margin: 1.25rem auto 0;
  border: 3px solid var(--accent);
  border-radius: 6px;
  background: #dcefeb;
  color: var(--ink);
  font-size: 1.65rem;
}

.prerequisite-slides .navigation {
  display: flex;
  justify-content: center;
  gap: 0.75rem;
  margin-top: 1.25rem;
}

.prerequisite-slides .next,
.prerequisite-slides .previous {
  display: inline-block;
  padding: 0.65rem 1.2rem;
  border-radius: 4px;
  cursor: pointer;
  font: 600 1rem Arial, sans-serif;
  text-decoration: none;
}

.prerequisite-slides .next:hover,
.prerequisite-slides .next:focus-visible {
  background: #105d59;
  outline: 3px solid #9ed1c7;
  outline-offset: 3px;
}

.prerequisite-slides .next {
  border: 0;
  background: var(--accent);
  color: #fff;
}

.prerequisite-slides .previous {
  border: 1px solid var(--accent);
  background: #fff;
  color: var(--accent);
}

.prerequisite-slides .previous:hover,
.prerequisite-slides .previous:focus-visible {
  background: #e1f0eb;
  outline: 3px solid #9ed1c7;
  outline-offset: 3px;
}

.prerequisite-slides button.previous:disabled {
  border-color: var(--muted);
  background: #e1e6e3;
  color: #77827d;
  cursor: not-allowed;
}

.prerequisite-slides .slide-choice:focus-visible + .slide {
  outline: 3px solid #9ed1c7;
}

@media (max-width: 520px) {
  .prerequisite-slides {
    padding: 1rem;
  }

  .prerequisite-slides .concept {
    width: 100%;
  }
}

.metric-slides {
  max-width: 760px;
  margin: 2rem auto;
  padding: 1.5rem;
  border: 1px solid #313735;
  border-radius: 8px;
  background: #111412;
  color: #c3c7c5;
  font-family: Arial, sans-serif;
}

.metric-slides .slide {
  display: none;
  text-align: left;
}

#metric-slide-1:checked ~ .classification-slide,
#metric-slide-2:checked ~ .regression-slide {
  display: block;
}

.metric-slides h3 {
  margin: 0 0 1.25rem;
  color: #e1e5e3;
  font-size: 1.3rem;
}

.metric-slides .table-wrap {
  overflow-x: auto;
}

.metric-slides table {
  width: 100%;
  min-width: 620px;
  border-collapse: collapse;
  table-layout: fixed;
  line-height: 1.55;
}

.metric-slides th,
.metric-slides td {
  padding: 0.7rem 0.75rem;
  border-bottom: 1px solid #3a403d;
  text-align: left;
  vertical-align: middle;
}

.metric-slides th {
  border-bottom-color: #a0a5a2;
  color: #d8dcda;
}

.metric-slides th:first-child,
.metric-slides td:first-child {
  width: 18%;
}

.metric-slides th:nth-child(2),
.metric-slides td:nth-child(2) {
  width: 49%;
}

.metric-slides th:nth-child(3),
.metric-slides td:nth-child(3) {
  width: 33%;
}

.metric-slides .metric-note {
  margin: 1rem 0 0;
  line-height: 1.55;
}

.metric-slides .navigation {
  display: flex;
  justify-content: space-between;
  margin-top: 1.25rem;
}

.metric-slides .next,
.metric-slides .previous {
  display: inline-block;
  padding: 0.6rem 1rem;
  border-radius: 4px;
  cursor: pointer;
  font: 600 1rem Arial, sans-serif;
  text-decoration: none;
}

.metric-slides .next {
  border: 0;
  background: #167d78;
  color: #fff;
}

.metric-slides .previous {
  border: 1px solid #8bb8af;
  background: transparent;
  color: #c3e0d8;
}

.metric-slides .next:hover,
.metric-slides .next:focus-visible,
.metric-slides .previous:hover,
.metric-slides .previous:focus-visible {
  outline: 3px solid #9ed1c7;
  outline-offset: 3px;
}

.metric-slides button.previous:disabled {
  border-color: #59615d;
  color: #818985;
  cursor: not-allowed;
}

@media (max-width: 520px) {
  .metric-slides {
    padding: 1rem;
  }
}

.model-families {
  max-width: 760px;
  margin: 2rem auto;
  padding: 1.5rem;
  border: 1px solid #313735;
  border-radius: 8px;
  background: #111412;
  color: #c3c7c5;
  font-family: Arial, sans-serif;
}

.model-families .table-wrap {
  overflow-x: auto;
}

.model-families table {
  width: 100%;
  min-width: 620px;
  border-collapse: collapse;
  table-layout: fixed;
  line-height: 1.55;
}

.model-families th,
.model-families td {
  padding: 0.6rem 0.75rem;
  border-bottom: 1px solid #3a403d;
  text-align: left;
  vertical-align: middle;
}

.model-families th {
  border-bottom-color: #a0a5a2;
  color: #d8dcda;
}

.model-families th:first-child,
.model-families td:first-child {
  width: 20%;
}

.model-families th:nth-child(2),
.model-families td:nth-child(2) {
  width: 30%;
}

.model-families th:nth-child(3),
.model-families td:nth-child(3) {
  width: 50%;
}

@media (max-width: 520px) {
  .model-families {
    padding: 1rem;
  }
}

.split-methods {
  max-width: 760px;
  margin: 2rem auto;
  padding: 1.5rem;
  border: 1px solid #313735;
  border-radius: 8px;
  background: #111412;
  color: #c3c7c5;
  font-family: Arial, sans-serif;
}

.split-methods h3 {
  margin: 0 0 1rem;
  color: #e1e5e3;
  font-size: 1.25rem;
}

.split-methods h3:not(:first-child) {
  margin-top: 2rem;
}

.split-methods .table-wrap {
  overflow-x: auto;
}

.split-methods table {
  width: 100%;
  min-width: 620px;
  border-collapse: collapse;
  table-layout: fixed;
  line-height: 1.55;
}

.split-methods th,
.split-methods td {
  padding: 0.6rem 0.75rem;
  border-bottom: 1px solid #3a403d;
  text-align: left;
  vertical-align: middle;
}

.split-methods th {
  border-bottom-color: #a0a5a2;
  color: #d8dcda;
}

.split-methods th:first-child,
.split-methods td:first-child {
  width: 21%;
}

.split-methods th:nth-child(2),
.split-methods td:nth-child(2) {
  width: 39%;
}

.split-methods th:nth-child(3),
.split-methods td:nth-child(3) {
  width: 40%;
}

@media (max-width: 520px) {
  .split-methods {
    padding: 1rem;
  }
}

.docker-comparison {
  max-width: 900px;
  margin: 2rem auto;
  overflow-x: auto;
  border: 1px solid #dedede;
  background: #fafafa;
  color: #171717;
  font-family: Georgia, "Times New Roman", serif;
  font-size: 1.15rem;
}

.docker-comparison table {
  width: 100%;
  min-width: 720px;
  border-collapse: collapse;
  table-layout: fixed;
  line-height: 1.4;
}

.docker-comparison th,
.docker-comparison td {
  padding: 0.6rem 0.8rem;
  border-bottom: 1px solid #dedede;
  text-align: left;
  vertical-align: top;
}

.docker-comparison th {
  background: #f0f0f0;
  font-weight: 600;
}

.docker-comparison th:first-child,
.docker-comparison td:first-child {
  width: 20%;
}

.docker-comparison th:nth-child(2),
.docker-comparison td:nth-child(2) {
  width: 38%;
}

.docker-comparison th:nth-child(3),
.docker-comparison td:nth-child(3) {
  width: 42%;
}

.docker-comparison tr:last-child td {
  border-bottom: 0;
}

@media (max-width: 520px) {
  .docker-comparison {
    font-size: 1rem;
  }
}
</style>

<div class="prerequisite-slides">
  <input class="slide-choice" type="radio" name="prerequisite-slide" id="prereq-slide-1" aria-label="Slide 1: Modelling" checked>
  <input class="slide-choice" type="radio" name="prerequisite-slide" id="prereq-slide-2" aria-label="Slide 2: Modelling and Model">
  <input class="slide-choice" type="radio" name="prerequisite-slide" id="prereq-slide-3" aria-label="Slide 3: Modelling, Model and Training">
  <input class="slide-choice" type="radio" name="prerequisite-slide" id="prereq-slide-4" aria-label="Slide 4: Service" />

  <section class="slide slide-one" aria-label="Slide 1">
    <div class="concept-row">
      <div class="concept">Modelling</div>
    </div>
    <nav class="navigation" aria-label="Slide navigation">
      <button class="previous" type="button" disabled>Previous</button>
      <label class="next" for="prereq-slide-2">Next</label>
    </nav>
  </section>

  <section class="slide slide-two" aria-label="Slide 2">
    <div class="concept-row">
      <div class="concept">Modelling</div>
      <div class="concept">Model</div>
    </div>
    <nav class="navigation" aria-label="Slide navigation">
      <label class="previous" for="prereq-slide-1">Previous</label>
      <label class="next" for="prereq-slide-3">Next</label>
    </nav>
  </section>

  <section class="slide slide-three" aria-label="Slide 3">
    <div class="concept-row">
      <div class="concept">Modelling</div>
      <div class="concept">Model</div>
      <div class="concept">Training</div>
    </div>
    <nav class="navigation" aria-label="Slide navigation">
      <label class="previous" for="prereq-slide-2">Previous</label>
      <label class="next" for="prereq-slide-4">Next</label>
    </nav>
  </section>

  <section class="slide slide-four" aria-label="Slide 4">
    <div class="concept-row dimmed">
      <div class="concept">Modelling</div>
      <div class="concept">Model</div>
      <div class="concept">Training</div>
    </div>
    <div class="service">Service</div>
    <nav class="navigation" aria-label="Slide navigation">
      <label class="previous" for="prereq-slide-3">Previous</label>
    </nav>
  </section>
</div>

## Section 2: Classification and Regression Metrics

<div class="metric-slides">
  <input class="slide-choice" type="radio" name="metric-slide" id="metric-slide-1" aria-label="Classification metrics" checked>
  <input class="slide-choice" type="radio" name="metric-slide" id="metric-slide-2" aria-label="Regression metrics">

  <section class="slide classification-slide" aria-label="Classification metrics slide">
    <h3>Classification metrics</h3>
    <div class="table-wrap">
      <table>
        <thead>
          <tr><th>Metric</th><th>What it answers</th><th>When to use</th></tr>
        </thead>
        <tbody>
          <tr><td>Accuracy</td><td>What percentage of predictions were correct?</td><td>Classes are roughly balanced</td></tr>
          <tr><td>Precision</td><td>When the model says "yes," how often is it right?</td><td>False alarms are costly</td></tr>
          <tr><td>Recall</td><td>Of all real "yes" cases, how many were caught?</td><td>Missing a case is costly (disease, fraud)</td></tr>
          <tr><td>F1 score</td><td>Balance of precision and recall</td><td>Both matter, or classes are imbalanced</td></tr>
          <tr><td>Confusion matrix</td><td>Table of right and wrong predictions by type</td><td>Always worth checking</td></tr>
          <tr><td>ROC-AUC</td><td>How well the model separates the classes (0.5 = random, 1.0 = perfect)</td><td>Comparing models</td></tr>
          <tr><td>Log loss</td><td>Punishes confident wrong predictions</td><td>You care about probabilities</td></tr>
        </tbody>
      </table>
    </div>
    <p class="metric-note"><strong>Accuracy trap:</strong> with 99 normal transactions and 1 fraud, "always say not fraud" gets 99% accuracy but catches zero fraud.</p>
    <nav class="navigation" aria-label="Metric slide navigation">
      <button class="previous" type="button" disabled>Previous</button>
      <label class="next" for="metric-slide-2">Next</label>
    </nav>
  </section>

  <section class="slide regression-slide" aria-label="Regression metrics slide">
    <h3>Regression metrics</h3>
    <div class="table-wrap">
      <table>
        <thead>
          <tr><th>Metric</th><th>What it answers</th><th>When to use</th></tr>
        </thead>
        <tbody>
          <tr><td>MAE</td><td>Average size of the error</td><td>Simple and explainable</td></tr>
          <tr><td>MSE</td><td>Average squared error</td><td>Big errors are especially bad</td></tr>
          <tr><td>RMSE</td><td>MSE converted back to original units</td><td>Most common choice</td></tr>
          <tr><td>R<sup>2</sup></td><td>How much variation is explained (1 = perfect, 0 = no better than the average)</td><td>Overall "how good"</td></tr>
          <tr><td>MAPE</td><td>Average error in %</td><td>Comparing different scales</td></tr>
        </tbody>
      </table>
    </div>
    <nav class="navigation" aria-label="Metric slide navigation">
      <label class="previous" for="metric-slide-1">Previous</label>
    </nav>
  </section>
</div>

## Section 3: How many types of models are there?

<div class="model-families">
  <div class="table-wrap">
    <table>
      <thead>
        <tr><th>Family</th><th>Idea</th><th>Models</th></tr>
      </thead>
      <tbody>
        <tr><td>Linear</td><td>Best straight line</td><td>Linear Regression, Logistic Regression</td></tr>
        <tr><td>Tree-based</td><td>Yes/no questions</td><td>Decision Tree, Random Forest, Gradient Boosting (XGBoost, LightGBM)</td></tr>
        <tr><td>Distance-based</td><td>"You're like your neighbors"</td><td>K-Nearest Neighbors</td></tr>
        <tr><td>Probability-based</td><td>Probabilities of what goes together</td><td>Naive Bayes</td></tr>
        <tr><td>Margin-based</td><td>Widest gap between groups</td><td>SVM</td></tr>
        <tr><td>Neural networks</td><td>Layers of connected "neurons"</td><td>Deep learning</td></tr>
      </tbody>
    </table>
  </div>
</div>

## Section 4: How many types of splitting are there?

<div class="split-methods">
  <h3>How many times you split</h3>
  <div class="table-wrap">
    <table>
      <thead>
        <tr><th>Type</th><th>How</th><th>Good for</th></tr>
      </thead>
      <tbody>
        <tr><td>Hold-out</td><td>One cut (80/20)</td><td>Large data, quick checks</td></tr>
        <tr><td>Train/val/test</td><td>Two cuts (60/20/20) &larr; <em>notebook</em></td><td>Decisions plus a final score</td></tr>
        <tr><td>K-fold CV</td><td>Rotate K parts</td><td>Small data</td></tr>
        <tr><td>Leave-one-out</td><td>K = number of rows</td><td>Tiny data</td></tr>
        <tr><td>Nested CV</td><td>CV inside CV</td><td>Very honest scores on small data</td></tr>
      </tbody>
    </table>
  </div>

  <h3>How rows are chosen</h3>
  <div class="table-wrap">
    <table>
      <thead>
        <tr><th>Type</th><th>How</th><th>Use when</th></tr>
      </thead>
      <tbody>
        <tr><td>Random</td><td>Shuffle and cut</td><td>Independent rows, balanced classes</td></tr>
        <tr><td>Stratified &larr; <em>notebook</em></td><td>Keeps class proportions</td><td>Classification, rare classes</td></tr>
        <tr><td>Group</td><td>Same "thing" stays together</td><td>Several rows per person / item</td></tr>
        <tr><td>Time-based</td><td>Past &rarr; train, future &rarr; test</td><td>Data over time</td></tr>
      </tbody>
    </table>
  </div>
</div>

## Section 5: Understanding Dockers and Containers enough

<div class="docker-comparison">
  <table>
    <thead>
      <tr><th>Term</th><th>What it is</th><th>PC comparison</th></tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>Dockerfile</strong></td>
        <td>A text file with step-by-step build instructions: "start from Python, copy my code, install these libraries, run this command"</td>
        <td>A recipe, or the setup instructions an IT person follows to prepare a new PC</td>
      </tr>
      <tr>
        <td><strong>Image</strong></td>
        <td>The finished, frozen package built from the Dockerfile: your app plus everything it needs (libraries, settings, a minimal Linux file system). It can't be changed; it's read-only.</td>
        <td>A <strong>setup.exe / installer file</strong>, or even better, a <strong>ghost image / disk image</strong> of a fully prepared PC that you can copy onto any machine</td>
      </tr>
      <tr>
        <td><strong>Container</strong></td>
        <td>A <em>running</em> instance of an image. It is isolated from other containers and the host.</td>
        <td>A <strong>running program</strong> (a process you'd see in Task Manager), but in its own sealed room with its own files. You can start many containers from one image, like opening several windows of the same program.</td>
      </tr>
    </tbody>
  </table>
</div>

## Section 6: Understanding patterns

<div class="prerequisite-slides pattern-slides">
  <input class="slide-choice" type="radio" name="pattern-slide" id="pattern-slide-1" aria-label="Batch" checked>
  <input class="slide-choice" type="radio" name="pattern-slide" id="pattern-slide-2" aria-label="Batch and API">
  <input class="slide-choice" type="radio" name="pattern-slide" id="pattern-slide-3" aria-label="Batch, API and Streaming">

  <section class="slide pattern-one" aria-label="Batch">
    <div class="concept-row">
      <div class="concept">Batch</div>
    </div>
    <nav class="navigation" aria-label="Pattern navigation">
      <button class="previous" type="button" disabled>Previous</button>
      <label class="next" for="pattern-slide-2">Next</label>
    </nav>
  </section>

  <section class="slide pattern-two" aria-label="Batch and API">
    <div class="concept-row">
      <div class="concept">Batch</div>
      <div class="concept">API</div>
    </div>
    <nav class="navigation" aria-label="Pattern navigation">
      <label class="previous" for="pattern-slide-1">Previous</label>
      <label class="next" for="pattern-slide-3">Next</label>
    </nav>
  </section>

  <section class="slide pattern-three" aria-label="Batch, API and Streaming">
    <div class="concept-row">
      <div class="concept">Batch</div>
      <div class="concept">API</div>
      <div class="concept">Streaming</div>
    </div>
    <nav class="navigation" aria-label="Pattern navigation">
      <label class="previous" for="pattern-slide-2">Previous</label>
    </nav>
  </section>
</div>

## Section 7: Introduction to MLflow

![MLflow workflow from notebook training through tracking and model registry to FastAPI prediction](assets/mlflow-workflow.svg)
