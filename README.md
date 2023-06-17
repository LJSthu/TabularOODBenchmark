## Tabular Benchmark with Specified Shift Patterns
> Jiashuo Liu, Tianyu Wang, Peng Cui, Hongseok Namkoong

> Tsinghua University, Columbia University

### 1. Dataset Access
Here we provide the access links for the 5 datasets used in our benchmark.

#### ACS Income
* The task is to predict whether an individual’s income is above \$50,000.
* Access link: https://github.com/socialfoundations/folktables
* Reference: Ding, F., Hardt, M., Miller, J., & Schmidt, L. (2021). Retiring adult: New datasets for fair machine learning. Advances in neural information processing systems, 34, 6478-6490.
* License: MIT License

#### ACS PubCov
* The task is to predict whether an individual has public health insurance.
* Access link: https://github.com/socialfoundations/folktables
* Reference: Ding, F., Hardt, M., Miller, J., & Schmidt, L. (2021). Retiring adult: New datasets for fair machine learning. Advances in neural information processing systems, 34, 6478-6490.
* License: MIT License

#### ACS Mobility
* The task is to predict whether an individual had the same residential address one year ago.
* Access link: https://github.com/socialfoundations/folktables
* Reference: Ding, F., Hardt, M., Miller, J., & Schmidt, L. (2021). Retiring adult: New datasets for fair machine learning. Advances in neural information processing systems, 34, 6478-6490.
* License: MIT License


#### Taxi Dataset
* The task is to predict whether the total ride duration time exceeds 30 minutes, based on location and temporal features.
* Access link: 
  * https://www.kaggle.com/datasets/mnavas/taxi-routes-for-mexico-city-and-quito
  * https://www.kaggle.com/competitions/nyc-taxi-trip-duration/data    
* License: CC BY-SA 4.0


#### US Accident Dataset
* The task is to predict whether an accident is severe (long delay) or not (short delay) based on weather features and Road condition features.
* Access link: https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents
* License: CC BY-SA 4.0


### 2. Python Package: `tabularoodbench`
Here we provide the scripts to get data in our proposed settings.

#### Install the package
```
pip3 install tabularoodbench
```

#### For settings utilizing ACS Income, Public Coverage, Mobility datasets
  * `get_data(task, state, year, need_preprocess, root_dir)` function
    * `task` values: 'income', 'pubcov', 'mobility'
  * examples:
    ```python
    from tabularoodbench import get_data
    # for ACS Income
    X, y, feature_names = get_data("income", "CA", 2018, True, './datasets/acs/')
    # for ACS Public Coverage
    X, y, feature_names = get_data("pubcov", "CA", 2018, True, './datasets/acs/')
    # for ACS Mobility
    X, y, feature_names = get_data("mobility", "CA", 2018, True, './datasets/acs/')
    ```
  * support `state` values: 
    * ['AL', 'AK', 'AZ', 'AR', 'CA', 'CO', 'CT', 'DE', 'FL', 'GA', 'HI', 'ID', 'IL', 'IN', 'IA', 'KS', 'KY', 'LA', 'ME', 'MD', 'MA', 'MI', 'MN', 'MS', 'MO', 'MT', 'NE', 'NV', 'NH', 'NJ', 'NM', 'NY', 'NC', 'ND', 'OH', 'OK', 'OR', 'PA', 'RI', 'SC', 'SD', 'TN', 'TX', 'UT', 'VT', 'VA', 'WA', 'WV', 'WI', 'WY', 'PR']


#### For settings utilizing US Accident, Taxi datasets
  * download data files:
    ```python
    # US Accident:
    https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents
    # Taxi
    https://www.kaggle.com/competitions/nyc-taxi-trip-duration
    ```
  * put data files in dir `./datasets/`
    * accident: `./datasets/Accident/US_Accidents_Dec21_updated.csv`
    * taxi: `./datasets/Taxi/{city}_clean.csv`
  * pass the `path to the data file` of `get_data` function
  * example:
    ```python
    from tabularoodbench import get_data
    # for US Accident
    X, y = get_data("accident", "CA", True, './datasets/Accident/US_Accidents_Dec21_updated.csv')
    # for Taxi
    X, y = get_data("taxi", "CA", True, './datasets/Taxi/{city}_clean.csv')
    ```
  * support `state` values:
    * for US Accident:  ['CA', 'TX', 'FL', 'OR', 'MN', 'VA', 'SC', 'NY', 'PA', 'NC', 'TN', 'MI', 'MO']
    * for Taxi: ['nyc', 'bog', 'uio', 'mex']


ps: we modify the <a href="https://github.com/socialfoundations/folktables">`folktables`</a> code to support `year` before 2014, and therefore we involve it in our package. 