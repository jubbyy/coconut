# coconut

*A LimeSurvey data extractor*

## Installation
I am not familiar with setting this repo as pypi , you still need to installed the original limesirvey-coconut then copy lime.py on the same directory (lib/site-packages/coconut)
```
pip install limesurvey-coconut
```

## Usage


```python
from coconut import LimeAPI, Survey, Workbook

# Create a LimeAPI instance  and disable all log by setting "log" = False (default log=True for backward compatible)
lime = LimeAPI(
        url="https://surveys.my-lime-survey-instance.org",
        username="admin",
        password="password",
        log=False
    )

# Create the survey instance
survey = Survey(survey_id=119618, lime_api=lime)

# Load questions, responses, survey info
survey.load_data()

# Save the data to an Excel file
survey.to_excel("survey.xlsx")

# Save response data to a CSV file
survey.to_csv("survey.csv")

# Update a Google Sheets workbook
workbook = Workbook(
    workbook_id="abc123",
    survey=survey,
    service_account_json_path="google-cloud-creds.json"
)
workbook.sync()
```
