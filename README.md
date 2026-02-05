# GrowthCurveAnalysis.mlx

This MATLAB pipeline processes bacterial growth data from Excel files and integrates population analysis via flow cytometry histograms.

## Setup & Requirements
* **MATLAB Toolboxes:** Requires the **Curve Fitting Toolbox**.
* **Dependencies:** Ensure `analyzeSyto9Histograms.mlx` is in your MATLAB path.
* **Paths:** Update the `folderPath` and `flowFolderPath` variables at the top of the script to match your local directory structure.

## Growth Curve Analysis
The script imports optical density (OD) data, generates publication-quality plots, and applies a mathematical model to the growth phase.

### Data Processing
* **Input File:** `LongCurve.xlsx`
* **Automated Handling:** Automatically detects the number of replicates and assigns unique identifiers (`rep1`, `rep2`, etc.).
* **Truncation:** The script is currently set to analyze the **first 11 time points** to focus on the active growth phase.

### Logistic Fitting
A **Logistic (Sigmoidal) Fit** is applied to the mean OD data using the following model:

$$y = \frac{C}{1 + e^{-b(t-a)}}$$

---

## Flow Cytometry Analysis
The second half of the script analyzes Syto9 histograms using the `analyzeSyto9Histograms.mlx` function.

### Gating Parameters
The analysis utilizes manual cutoffs to filter the population:
* **Low Cutoff:** `1.0e4` (Removes background noise and debris).
* **High Cutoff:** `1.5e5` (Removes doublets and outliers).


## Generated Outputs
The following files are saved to the defined `folderPath`:

| File Name | Description |
| :--- | :--- |
| `GC.pdf` | Growth curve of replicates on a log scale. |
| `GC_fit.pdf` | Growth curve with mean points and the logistic fit overlay. |
| `results` | Comprehensive structured data from flow cytometry. |
| `summaryByTime` | Statistical summary table indexed by time-point. |


