# Air Quality Prediction Using Machine Learning

A beginner-friendly machine learning mini-project that estimates **carbon monoxide concentration (`CO(GT)`)** from the UCI Air Quality dataset and compares three regression models.

> \*\*Scope clarification:\*\* The source dataset does not contain an official AQI label or PM2.5/PM10 columns. This project estimates `CO(GT)` concentration; it does not calculate official Indian AQI and does not forecast future hours.

## Project objectives

* Load and inspect a real-world air-quality dataset.
* Clean missing-value markers and prepare numerical features.
* Explore carbon monoxide concentration over time.
* Train Linear Regression, Random Forest, and Gradient Boosting models.
* Compare models using MAE, RMSE, and R².
* Visualize actual vs predicted values and Random Forest feature importance.
* Export the comparison table and save the selected model.

## Dataset

**Source:** [UCI Machine Learning Repository — Air Quality](https://archive.ics.uci.edu/dataset/360/air+quality)

The dataset contains hourly air-quality sensor observations collected in an Italian city. In the original file, `-200` is used as a missing-value marker. The notebook converts this marker to missing values before training.

### Target and features

* **Target:** `CO(GT)` (reference carbon monoxide concentration, mg/m³).
* **Features:** other numeric pollutant and sensor measurements, excluding `CO(GT)`.

Because input measurements are from the same observation time, this is a **same-time concentration-estimation task**, not future forecasting. Some input sensors may be strongly related to the target, so the results should be interpreted with this limitation in mind.

## Machine learning models

1. Linear Regression
2. Random Forest Regressor
3. Gradient Boosting Regressor

Each model uses a median imputer in a scikit-learn pipeline. The dataset is split chronologically: first 80% for training and final 20% for testing.

## Evaluation metrics

|Metric|Meaning|Preferred result|
|-|-|-|
|MAE|Mean absolute prediction error|Lower|
|RMSE|Root mean squared error; penalizes large errors more|Lower|
|R²|Variance explained relative to a mean baseline|Generally higher, closer to 1|

The notebook selects the model with the lowest RMSE on the test subset. Record the actual values produced by your run in your project report; results are not pre-filled because they depend on running the notebook.

## Repository contents

```text
Air-Quality-Prediction/
├── Air\_Quality\_Prediction\_Documented.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## How to run

### Option A — Google Colab (recommended)

1. Download `Air\_Quality\_Prediction\_Documented.ipynb` from this repository.
2. Open [Google Colab](https://colab.research.google.com/).
3. Select **File → Upload notebook** and upload the notebook.
4. Download the dataset from the [UCI dataset page](https://archive.ics.uci.edu/dataset/360/air+quality).
5. Run the cells in order. When prompted, upload the dataset CSV file.
6. Review the metric table and plots. The final cells download `air\_quality\_model.pkl` and `model\_comparison.csv`.

### Option B — Run locally

Install Python 3.10+ and the packages listed in `requirements.txt`. The notebook currently uses `google.colab.files` for uploads/downloads, so for local execution you must replace the Colab upload/download cells with local file paths and standard file saving.

## Outputs

When run successfully, the notebook displays:

* Dataset preview and missing-value summary
* Statistical summary
* CO concentration over time
* Model comparison table
* Actual vs predicted plot
* RMSE comparison chart
* Top 10 Random Forest feature importances
* Example prediction with absolute error

It also creates:

* `air\_quality\_model.pkl` — selected trained pipeline and feature metadata
* `model\_comparison.csv` — MAE, RMSE, and R² results

## Limitations and future work

* The project does not predict official AQI.
* It does not forecast future hours because the current features come from the same timestamp as the target.
* Dataset geography and collection period may limit generalization.
* Feature importance does not establish causation.
* Future versions could use a dataset with official AQI labels, PM2.5/PM10, location, lagged features, and time-series validation.

## References

* [UCI Air Quality dataset](https://archive.ics.uci.edu/dataset/360/air+quality)
* [pandas documentation](https://pandas.pydata.org/docs/)
* [scikit-learn documentation](https://scikit-learn.org/stable/)
* [Matplotlib documentation](https://matplotlib.org/stable/)

## Author

Snehal Kalkote, Computer Engineering, JSPM's RSCOE Thathwade, (2026-27)

