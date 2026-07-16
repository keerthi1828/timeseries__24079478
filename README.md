Where Nonlinear Forecasting Helps — German Demand Regimes
Overview
This project forecasts German weekly electricity demand and evaluates models across demand regimes (winter, summer, holiday and peak weeks) and three forecast horizons: fixed-origin two-year forecasts (benchmarks, SARIMA, SARIMAX), a week-ahead CatBoost model, and a rolling one-hour-ahead LSTM. The focus is where nonlinear feature learning helps rather than average accuracy alone.
Data

German electricity load from Open Power System Data (hourly, 2015–2020) — downloaded automatically
Berlin temperature from the Open-Meteo archive API — downloaded automatically
German holiday and working-day calendar — generated in code

Libraries to install
pip install pandas numpy matplotlib statsmodels scikit-learn tensorflow catboost holidays requests
How to run

Open the notebook in Google Colab or Jupyter.
Run all cells top to bottom (Runtime → Run all).
Data download, model training, evaluation and all plots run automatically. Full run takes a few minutes.

Internet connection is needed on first run.
Results summary
No fixed-origin model beats the Seasonal Naive on average (RMSE 4,083 MW), and the SARIMA family's low shortfall record comes from upward bias, not skill. CatBoost is the only weekly model consistent across every regime — best directional accuracy (61.5%), strong peak-week error (1,618 MW) and bounded shortfalls — with holiday, working-day and lag-52 features among its top importances. The LSTM is highly accurate hour-ahead (RMSE 930 MW) but is a rolling one-step tool for operations, not a long-horizon forecast. Recommended roles: Seasonal Naive for fixed-origin baselines, CatBoost for week-ahead scheduling, LSTM for intraday operations. Full discussion, figures and tables are in the report.
