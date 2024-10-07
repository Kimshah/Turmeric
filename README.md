# Turmeric

Clinical Trial Matching Algorithm

This project processes patient data and clinical trial data to match patients with eligible clinical trials based on specific inclusion criteria such as age and medical conditions.

Table of Contents
- [Project Overview](#project-overview)
- [Installation](#installation)
- [Usage](#usage)
- [Data Input Format](#data-input-format)
- [Functions](#functions)
- [Testing](#testing)
- [Contributing](#contributing)

 Project Overview
This project is designed to help researchers or medical institutions match patients with clinical trials they are eligible for. The matching is based on two main criteria:
1. Patient's age falls within the trial's required age range.
2. Patient's medical condition matches one of the conditions listed in the trial.

 Installation
To run this project, you need the following dependencies installed:
- Python 3.x
- Pandas
- tqdm (for progress tracking)

You can install the necessary packages using `pip`:

```bash
pip install pandas tqdm
```

 Usage
1. Load your clinical trial data and patient data into Pandas dataframes.
2. Call the function `is_eligible(patient, trial)` to determine if a specific patient is eligible for a clinical trial.

 Example Code:

```python
def is_eligible(patient, trial):
    min_age = trial['Min Age']
    max_age = trial['Max Age']
    conditions = trial['Conditions'].split('|')

    patient_age = patient['AGE']
    patient_condition = patient['DESCRIPTION']

    if min_age <= patient_age <= max_age and patient_condition in conditions:
        return True
    return False
```

3. You can run the test function provided to verify that the eligibility function works correctly:

```python
test_is_eligible()
```

Data Input Format
The clinical trial and patient data should be in the form of Pandas dataframes with the following columns:

### Clinical Trials Data
| Column Name   | Description                                      |
|---------------|--------------------------------------------------|
| NCT Number    | Identifier for the clinical trial                |
| Study Title   | Title of the study                               |
| Study URL     | URL of the study for more details                |
| Study Status  | Current status (e.g., recruiting, completed)     |
| Conditions    | Medical conditions the trial addresses           |
| Age           | Age range for eligibility (Min Age, Max Age)     |

### Patient Data
| Column Name       | Description                                      |
|-------------------|--------------------------------------------------|
| Patient Id        | Unique identifier for each patient               |
| Patient Description | Short description of the patient's condition    |
| AGE               | Age of the patient                               |

 Functions

### `is_eligible(patient, trial)`
- **Parameters**:
  - `patient`: A dictionary containing patient's age and medical condition.
  - `trial`: A dictionary representing a clinical trial with minimum and maximum age and medical conditions.
Returns
  - `True` if the patient is eligible for the trial, otherwise `False`.

 Testing
A test function `test_is_eligible()` is included in the notebook to ensure that the eligibility function works as expected. To run the test:

```python
test_is_eligible()
```

Contact
For any questions or further information, feel free to reach out.



