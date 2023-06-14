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


### 2. Get Data of Our Settings
Here we provide the scripts to get data in our proposed settings.

#### 2.1 For ACS Income, Public Coverage, Mobility
* Import our `get_data.py` 
* Using functions:
  * `get_ACSIncome(method, state, year)`: get data for settings utilizing ACS Income dataset
  * `get_ACSPubCov(method, state, year)`: get data for settings utilizing ACS Public Coverage dataset
  * `get_ACSMobility(method, state, year)`: get data for settings utilizing ACS Mobility dataset
* Support `state`: ['AL', 'AK', 'AZ', 'AR', 'CA', 'CO', 'CT', 'DE', 'FL', 'GA', 'HI', 'ID', 'IL', 'IN', 'IA', 'KS', 'KY', 'LA', 'ME', 'MD', 'MA', 'MI', 'MN', 'MS', 'MO', 'MT', 'NE', 'NV', 'NH', 'NJ', 'NM', 'NY', 'NC', 'ND', 'OH', 'OK', 'OR', 'PA', 'RI', 'SC', 'SD', 'TN', 'TX', 'UT', 'VT', 'VA', 'WA', 'WV', 'WI', 'WY', 'PR']
* Example:

  ```python
  from get_data import get_ACSIncome
  X, y, features = get_ACSIncome('xgb', 'CA', 2018)
  ```

#### 2.2 For US Accident, Taxi
* Run `preprocess.py` with `python3 preprocess.py --dir './dataset'`(default file dir)
* Import our `get_data.py` 
* Using functions:
  * `get_USAccident(method, state)`: get data for settings utilizing US Accident dataset
  * `get_taxi(method, state)`: get data for settings utilizing Taxi dataset
* Support `state`:
  * US Accident: ['CA', 'TX', 'FL', 'OR', 'MN', 'VA', 'SC', 'NY', 'PA', 'NC', 'TN', 'MI', 'MO']
  * Taxi: ['bog', 'nyc', 'uio', 'mex']
* Example:

  ```python
  from get_data import get_USAccident
  X, y = get_USAccident('xgb', 'CA')
  ```