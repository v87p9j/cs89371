java c
## Task 0 Getting employment data from the Bureau of Labor Statistics API (15 points)
** You can code as if the data files are in the same folder as this notebook**
Please use the Version 2 API from the BLS (registration required) to obtain the following data, [this example Python code](https://www.bls.gov/developers/api_python.htm#python2) may be useful to you.
In particular, we are interested in the [popular series](https://data.bls.gov/cgi-bin/surveymost?bls) titled:
- Unemployment Rate (Seasonally Adjusted)
- PPI Final Demand (Seasonally Adjusted), PPI = producer price index
Here's what we need to see:
- Please use the API to obtain the data from 2011 to 2022. IMPORTANT: you can only obtain a limited number of records from BLS so one approach is to query the years 2011-2018, then 2019-2022.
- Please use the `requsets` library in your answer.
- Please consolidate your results into two variables: `unemployment` and `ppi`. Both are lists of dictionaries containing the respective records where the output should look like
```
[{'year': '2022',
'period': 'M12',
'periodName': 'December',
'value': '3.5',
'footnotes': [{}]},
...
]
```
- Please show that the **length of your lists are both 144** then **print out the first 2 records** from your `ppi` variable.
### Task 1: Tidying the data (20 points)
** You can code as if the data files are in the same folder as this notebook**
Please create a data frame. called `labor` that contains the information from above. Each row should be a year-month and the columns should include:
- `ppi`, this should be a float
- `unemployment`, this should be a float
- `date`, this should be a datetime object with the format `'{year}-{month}-01'`
For grading:
- Please report the shape of `labor`
- Please verify with the keyword `assert` that no missing values exist
- Please verify with the keyword `assert` that no duplicate entries exist when we combined the data between `ppi` and `unemployment`
- Please report the row(s) with the highest unemployment.
- Your solution should not assume the series data from BLS are ordered the same way.
## Task 2: Wrangling (25 points)
** You can code as if the data files are in the same folder as this notebook**
To get the mental health data across years, we'll need to extract it from `exam_brfss_asc.json`.
Each record is one survey response from the BRFSS. The data is a single string where different characters contain the data for different variables. To know which variable correspond to which characters, you'll need to look at `exam_layout.csv`.
To obtain the human definition for each variable, you'll need to look at [code book on the CDC](https://www.cdc.gov/brfss/annual_data/2021/pdf/codebook21_llcp-v2-508.pdf). There are variab代 写Unemployment RatePython
代做程序编程语言les in the code book but not in the dataset because we only kept the variables that exist across all years.
Here is what the output should be, a data frame. called `health`, with the columns with the following data:
- `down30`, the value associated with the description "Now thinking about your mental health, which includes stress, depression, and problems with emotions, for how many days during the past 30 days was your mental health not good?"
- `age_group`, the integer associated with the variable `_AGEG5YR`
- `year`, the interview year, this may differ from the year in the JSON file.
- `month`, the interview month
Please print out the number of records for each `year` value in `health`.
## Task 3: tidying up (25 points)
** You can code as if the data files are in the same folder as this notebook**
- Please verify the following for `health` using the keyword `assert`:
- There are no missing values in `year` or `month`
- Please perform. the following transformations for `health`:
- For `down30`:
- The value that corresponds to `None` implies 0 days, replace those values with 0.
- Please convert "Refused", "Don’t know/Not sure", and "Not asked or Missing" into missing values.
- For `age_group`
- Simplify the groups into 3 categories: 18-34, 35-64, and others
- Please aggregate the data into a data frame. `health_agg` such that each row is a month/year/age group combination and the columns should contain:
- `date`: this should be a datetime object with format `'{year}-{month}-01'`
- `age_group`
- `simple_mean_down30`: this should contain the appropriate summary statistic from `down30`
- Please print out the row(s) that correspond to the age_group of 18-34 in `health_agg` in 2022.
## Task 4: Observing patterns (15 points)
** You can code as if the data files are in the same folder as this notebook**
If you haven't solve the problems before, you should load in the dataset `Q3_backup.csv` and `Q1_backup.csv` to move forward here.
Using `health_agg` and `labor` in our exam so far, please use **visualizations** (not significance test) to verify or answer the following questions:
- Is the 18-34 age group experiencing a larger decrease in mental health relative to other age groups? Please provide a 2 sentence answer based on your plot.
- Comparing prices vs unemployment, which one seems more correlated with the changes in mental health of the 18-34 age group?
## Task 5: (10 points)
There is a belief that people are on average more depressed during December (due to the holidays) so the interviews in December could be biased. How would you check this belief by analyzing the data. Your answer should address the fact that the mental health values fluctuate from person to person.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
