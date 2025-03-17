(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc init
(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc stage add -n data_collection -d src/data/data_colletion.py
 -o data/raw python src/data/data_collection.py
(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc repro
(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc dag
(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc stage add -n pre_processing -d src/data/data/data_prep.py -
d data/raw -o data/processed python src/data/data_prep.py
(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc repro
(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc dag
(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc stage add -n model_building -d src/model/model_building.py 
-d data/processed -o models/model.pkl python src/model/model_b
uilding.py
Add this line in dvc.yaml in data_collection stage under depe
params:
    - data_collection.test_size
Add this line in dvc.yaml in model_building stage under dependencies
params:
    - model_building.n_estimators
(myenv) D:\projects\DVC project2\water-potability-prediction>dvc repro
(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc stage add -n model_eval -d src/model/model_eval.py -d model
s/model.pkl --metrics reports/metrics.json python src/model/mo
del_eval.py
(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc repro
(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc dag
(myenv) D:\projects\DVC project2\water-potability-prediction>d
vc metrics show

water-potability-prediction
==============================

water potability prediction using ML

Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
