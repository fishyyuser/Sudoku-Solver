<h1>📱 Sudoku Solver — Computer Vision & Applied ML System</h1>

<p>
<strong>Sudoku Solver</strong> is an end-to-end <strong>computer vision + machine learning system</strong>
that extracts, validates, and solves Sudoku puzzles from real-world images captured using a mobile camera.
</p>

<p>
The project focuses on <strong>robust digit extraction under noisy visual conditions</strong>,
<strong>ML inference integration</strong>, and <strong>system-level tradeoffs between on-device and server-side processing</strong>.
</p>

<hr/>

<h2>🎯 Problem Statement</h2>
<p>
Camera-captured Sudoku images suffer from perspective distortion, glare, uneven lighting,
and OCR noise. Fully automated pipelines frequently fail due to misclassified or hallucinated digits.
</p>

<p>
This project addresses the problem using a <strong>hybrid ML + algorithmic approach</strong>:
<ul>
  <li>Computer vision and CNN-based digit recognition for extraction</li>
  <li>Human-in-the-loop correction for noisy predictions</li>
  <li>Deterministic backtracking solver for correctness guarantees</li>
</ul>
</p>

<hr/>

<h2>🧠 ML & CV Pipeline</h2>
<ol>
  <li><strong>Image Preprocessing:</strong> Grayscale conversion, adaptive thresholding, contour detection (OpenCV)</li>
  <li><strong>Perspective Transformation:</strong> Grid isolation and normalization</li>
  <li><strong>Cell Extraction:</strong> 81 individual cell crops</li>
  <li><strong>Digit Recognition:</strong> CNN trained on digit dataset, exported as TensorFlow Lite</li>
  <li><strong>Post-processing:</strong> Empty-cell filtering and grid validation</li>
</ol>

<p>
The digit recognition model is optimized for <strong>fast inference</strong> and deployed as a
<strong>TFLite artifact</strong> for mobile-friendly execution.
</p>

<hr/>

<h2>🛠️ System Architecture & Design Decisions</h2>
<ul>
  <li>
    <strong>Server-side CV Processing:</strong>
    OpenCV-based preprocessing and digit extraction hosted on a Flask API (AWS EC2)
    to handle computationally heavy image operations.
  </li>
  <li>
    <strong>On-device Solving:</strong>
    Sudoku solving implemented locally using an optimized backtracking algorithm to
    avoid unnecessary network calls and ensure low-latency responses.
  </li>
  <li>
    <strong>Human-in-the-loop Correction:</strong>
    Due to real-world OCR noise (glare, screen capture artifacts),
    the grid is made editable to allow user correction before solving.
  </li>
</ul>

<p>
This mirrors real-world ML systems where <strong>model predictions are probabilistic</strong>
and require validation or correction layers.
</p>

<hr/>

<h2>⚠️ Failure Modes & Robustness</h2>
<ul>
  <li>False positives caused by glare and screen refresh artifacts</li>
  <li>Digit hallucination in empty cells</li>
  <li>Invalid grids rejected using Sudoku rule validation</li>
</ul>

<p>
Invalid predictions are surfaced to the user rather than silently solved,
prioritizing <strong>correctness over blind automation</strong>.
</p>

<hr/>

<h2>🛠️ Tech Stack</h2>
<ul>
  <li><strong>Mobile:</strong> Android (Java)</li>
  <li><strong>Backend:</strong> Python, Flask</li>
  <li><strong>Computer Vision:</strong> OpenCV</li>
  <li><strong>Machine Learning:</strong> TensorFlow, TensorFlow Lite</li>
  <li><strong>Cloud:</strong> AWS EC2</li>
</ul>

<hr/>

<h2>📦 Repository Structure</h2>
<ul>
  <li><code>app/</code> — Android application (camera capture, UI, solver integration)</li>
  <li><code>server/</code> — Flask API for CV preprocessing and digit inference</li>
  <li><code>model/</code> — CNN training scripts and exported TFLite model</li>
</ul>

<hr/>

<h2>🎥 Demo</h2>
<p>
A full end-to-end demo of image capture, digit extraction, correction, and solving:
</p>
<p>
<a href="https://drive.google.com/file/d/1FAq8XycbCRtoZnkP5xXUnmeYsvL5E6gW/view">▶️ Video Demo</a>
</p>
