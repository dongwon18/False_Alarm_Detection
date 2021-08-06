# Purpose
- Using open data set, train machine learning models(Random Forest, Support Vector Machine, Logistic Regression) and Deep learning Model(CNN, ANN).  

# Dataset Source
- [RONTO dataset](https://www.kaggle.com/afrniomelo/pronto-benchmark)
## publication
-  A. Stief, R. Tan, Y. Cao, J. R. Ottewill, N. F. Thornhill, J. Baranowski, A heterogeneous benchmark dataset for data analytics: Multiphase flow facility case study, Journal of Process Control, 79 (2019) 41–55, DOI: https://doi.org/10.1016/j.jprocont.2019.04.009

- The dataset has been used in the following works:

  - A. Stief, R. Tan, Y. Cao, J. R. Ottewill. Analytics of heterogeneous process data: Multiphase flow facility case study. IFAC-PapersOnLine, 51(18):363–368, 2018. DOI: https://doi.org/10.1016/j.ifacol.2018.09.327

  - A. Stief, J. R. Ottewill, R. Tan, Y. Cao. Process and alarm data integration under a two-stage Bayesian framework for fault diagnostics. IFAC-PapersOnLine, 51(24):1220–1226, 2018. DOI: https://doi.org/10.1016/j.ifacol.2018.09.696

  - A. Stief, J. R. Ottewill, J. Baranowski. Investigation of the diagnostic properties of sensors and features in a multiphase flow facility case study. in: 12th IFAC Symposium on Dynamics and Control of Process Systems (in press), 2019

  - M. Lucke, X. Mei, A. Stief, M. Chioua, N. F. Thornhill. Variable selection for fault detection and identification based on mutual information of multi-valued alarm series, in: 12th IFAC Symposium on Dynamics and Control of Process Systems (in press), 2019

  - R. Tan, T. Cong, N. F. Thornhill, J. R. Ottewill, J. Baranowski. Statistical monitoring of processes with multiple operating modes, in: 12th IFAC Symposium on Dynamics and Control of Process Systems (in press), 2019.

# Dataset Features
- The data set was collected through 3 days
- There is merged data in `Pre-processed data/Aligned and labelled alarm and process data/Testday+_merged.csv`
- in csv format, with header
- In the file
  - 29 columns
    - [:, 0] ~ [:,11]: alarm value(1: active, 0: inactive)
    - [:, 12] ~ [:,27]: sensor value
    - [:, 28]: failure(1: failure, 0: normal)
  - rows
    - testday2: 12,420 rows
    - testday3: 21,300 rows
    - testday4: 11,700 rows
  - No NaN for each testday, however only testday2 and testday4 ahve LI502 data. On the other hand, only testday3 has LI505 data.
  
# Operating Environment
- Google Colaboratory(using TPU, on July.28th.2021)

# Result
- make tsv file
## Failure Prediction

|accuracy|CNN|ANN|Random Forest|SVM(linear)|SVM(rbf)|SVM(poly)|Logistic Regression|
|:------:|---:|---:|--------:|---:|---:|---:|---:|
|train|0.894|0.812|1|0.859|0.686|0.535|0.738|
|val|0.901|0.812|0.999|0.845|0.681|0.538|0.730|
|test|0.941|0.896|1|0.858|0.683|0.536|0.737|

## Alarm Prediction

|accuracy|CNN|ANN|Random Forest|SVM(linear)|SVM(rbf)|SVM(poly)|Logistic Regression|
|:------:|---:|---:|--------:|---:|---:|---:|---:|
|train|0.794|0.701|1|0.679|0.679|0.679|0.679|
|val|0.797|0.701|0.997|0.677|0.677|0.677|0.677|
|test|0.819|0.737|0.998|0.679|0.679|0.679|0.679|

- seems strange that all ML models except Random Rorest have same accuracy

# Conclusion
- Need to modify hyper parameter more to get good results.
- Among models ensemble model has the best score
  → Need voting ensemble model to combine all machine learning and deep learning models
