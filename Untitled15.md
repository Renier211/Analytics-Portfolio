# Introduction

The provided code is designed to analyze quarterly mutual fund data from an Excel file, specifically focusing on tracking the holdings of various stocks over multiple quarters. The purpose of the code is to aggregate and organize data to determine which stocks were held by the mutual fund in each quarter and to identify unique stock tickers based on their ISIN (International Securities Identification Number).

### Key Operations

1) Loading the Excel File: The code begins by loading the Excel file, which contains multiple sheets, each representing the mutual fund's holdings for a specific quarter.

2) Extracting Sheet Names: It identifies and lists the sheet names corresponding to each quarter from the Excel file.

3) Collecting Unique FundISIN and Tickers: By iterating through each sheet, the code collects unique FundISINs and their corresponding tickers. This information is stored in a dictionary and then converted into a DataFrame for better handling and visualization.

4) Extracting Quarters: The code extracts and sorts the quarters based on the sheet names to ensure they are processed in chronological order.

5) Creating and Populating the DataFrame: An empty DataFrame is created with rows representing unique stocks and columns representing each quarter. The DataFrame is then populated with data from each sheet, marking the presence of each stock in the respective quarters and assigning the appropriate ticker values.

6) Saving the Combined DataFrame: The final aggregated DataFrame, which contains the stocks and the quarters they were held, is saved to a new Excel file for further analysis or reporting.

7) Validating Data Consistency: The code performs a validation step to ensure the accuracy of the stock counts by comparing the actual number of stocks in each quarter with the calculated values from the aggregated DataFrame. This helps identify any discrepancies.




### Purpose

The main objective of this code is to provide a comprehensive view of the mutual fund's holdings over time, facilitating the analysis of investment trends and portfolio composition. By organizing the data into a structured format, the code enables easier tracking of stock holdings and aids in identifying any missing or inconsistent data across different quarters. This can be particularly useful for financial analysts, portfolio managers, and other stakeholders involved in investment decision-making processes.

# Code:

### Import required packages


```python
import pandas as pd
```

### Load Excel File and Read Sheets


```python
# Path to the Excel file
file_path = r'C:\Users\27825\Documents\02_Corporate Profile\Project Portfolio\Buxton Project\91.xlsx'

# Read all sheets of the Excel file into a dictionary
all_sheets = pd.read_excel(file_path, sheet_name=None)

# Print the keys (sheet names) of the dictionary
print(all_sheets.keys())
```

    dict_keys(['Ninety_One_Commodity_2005Q1', 'Ninety_One_Commodity_2005Q2', 'Ninety_One_Commodity_2005Q3', 'Ninety_One_Commodity_2005Q4', 'Ninety_One_Commodity_2006Q1', 'Ninety_One_Commodity_2006Q2', 'Ninety_One_Commodity_2006Q3', 'Ninety_One_Commodity_2006Q4', 'Ninety_One_Commodity_2007Q1', 'Ninety_One_Commodity_2007Q3', 'Ninety_One_Commodity_2008Q1', 'Ninety_One_Commodity_2008Q2', 'Ninety_One_Commodity_2008Q3', 'Ninety_One_Commodity_2008Q4', 'Ninety_One_Commodity_2009Q1', 'Ninety_One_Commodity_2009Q2', 'Ninety_One_Commodity_2009Q3', 'Ninety_One_Commodity_2009Q4', 'Ninety_One_Commodity_2010Q1', 'Ninety_One_Commodity_2010Q2', 'Ninety_One_Commodity_2010Q3', 'Ninety_One_Commodity_2010Q4', 'Ninety_One_Commodity_2011Q1', 'Ninety_One_Commodity_2011Q2', 'Ninety_One_Commodity_2011Q3', 'Ninety_One_Commodity_2011Q4', 'Ninety_One_Commodity_2012Q1', 'Ninety_One_Commodity_2012Q2', 'Ninety_One_Commodity_2012Q3', 'Ninety_One_Commodity_2012Q4', 'Ninety_One_Commodity_2013Q1', 'Ninety_One_Commodity_2013Q2', 'Ninety_One_Commodity_2013Q3', 'Ninety_One_Commodity_2013Q4', 'Ninety_One_Commodity_2014Q1', 'Ninety_One_Commodity_2014Q2', 'Ninety_One_Commodity_2014Q3', 'Ninety_One_Commodity_2014Q4', 'Ninety_One_Commodity_2015Q1', 'Ninety_One_Commodity_2015Q2', 'Ninety_One_Commodity_2015Q3', 'Ninety_One_Commodity_2015Q4', 'Ninety_One_Commodity_2016Q1', 'Ninety_One_Commodity_2016Q2', 'Ninety_One_Commodity_2016Q3', 'Ninety_One_Commodity_2016Q4', 'Ninety_One_Commodity_2017Q1', 'Ninety_One_Commodity_2017Q2', 'Ninety_One_Commodity_2017Q3', 'Ninety_One_Commodity_2017Q4', 'Ninety_One_Commodity_2018Q1', 'Ninety_One_Commodity_2018Q2', 'Ninety_One_Commodity_2018Q3', 'Ninety_One_Commodity_2018Q4', 'Ninety_One_Commodity_2019Q1', 'Ninety_One_Commodity_2019Q2', 'Ninety_One_Commodity_2019Q3', 'Ninety_One_Commodity_2019Q4', 'Ninety_One_Commodity_2020Q1', 'Ninety_One_Commodity_2020Q2', 'Ninety_One_Commodity_2020Q3', 'Ninety_One_Commodity_2020Q4', 'Ninety_One_Commodity_2021Q1', 'Ninety_One_Commodity_2021Q2', 'Ninety_One_Commodity_2021Q3', 'Ninety_One_Commodity_2021Q4', 'Ninety_One_Commodity_2022Q1', 'Ninety_One_Commodity_2022Q2', 'Ninety_One_Commodity_2022Q3', 'Ninety_One_Commodity_2022Q4'])
    


```python
# List of sheet names corresponding to quarters
sheet_names = [
    'Ninety_One_Commodity_2005Q1', 'Ninety_One_Commodity_2005Q2', 'Ninety_One_Commodity_2005Q3',
    'Ninety_One_Commodity_2005Q4', 'Ninety_One_Commodity_2006Q1', 'Ninety_One_Commodity_2006Q2',
    'Ninety_One_Commodity_2006Q3', 'Ninety_One_Commodity_2006Q4', 'Ninety_One_Commodity_2007Q1',
    'Ninety_One_Commodity_2007Q3', 'Ninety_One_Commodity_2008Q1', 'Ninety_One_Commodity_2008Q2',
    'Ninety_One_Commodity_2008Q3', 'Ninety_One_Commodity_2008Q4', 'Ninety_One_Commodity_2009Q1',
    'Ninety_One_Commodity_2009Q2', 'Ninety_One_Commodity_2009Q3', 'Ninety_One_Commodity_2009Q4',
    'Ninety_One_Commodity_2010Q1', 'Ninety_One_Commodity_2010Q2', 'Ninety_One_Commodity_2010Q3',
    'Ninety_One_Commodity_2010Q4', 'Ninety_One_Commodity_2011Q1', 'Ninety_One_Commodity_2011Q2',
    'Ninety_One_Commodity_2011Q3', 'Ninety_One_Commodity_2011Q4', 'Ninety_One_Commodity_2012Q1',
    'Ninety_One_Commodity_2012Q2', 'Ninety_One_Commodity_2012Q3', 'Ninety_One_Commodity_2012Q4',
    'Ninety_One_Commodity_2013Q1', 'Ninety_One_Commodity_2013Q2', 'Ninety_One_Commodity_2013Q3',
    'Ninety_One_Commodity_2013Q4', 'Ninety_One_Commodity_2014Q1', 'Ninety_One_Commodity_2014Q2',
    'Ninety_One_Commodity_2014Q3', 'Ninety_One_Commodity_2014Q4', 'Ninety_One_Commodity_2015Q1',
    'Ninety_One_Commodity_2015Q2', 'Ninety_One_Commodity_2015Q3', 'Ninety_One_Commodity_2015Q4',
    'Ninety_One_Commodity_2016Q1', 'Ninety_One_Commodity_2016Q2', 'Ninety_One_Commodity_2016Q3',
    'Ninety_One_Commodity_2016Q4', 'Ninety_One_Commodity_2017Q1', 'Ninety_One_Commodity_2017Q2',
    'Ninety_One_Commodity_2017Q3', 'Ninety_One_Commodity_2017Q4', 'Ninety_One_Commodity_2018Q1',
    'Ninety_One_Commodity_2018Q2', 'Ninety_One_Commodity_2018Q3', 'Ninety_One_Commodity_2018Q4',
    'Ninety_One_Commodity_2019Q1', 'Ninety_One_Commodity_2019Q2', 'Ninety_One_Commodity_2019Q3',
    'Ninety_One_Commodity_2019Q4', 'Ninety_One_Commodity_2020Q1', 'Ninety_One_Commodity_2020Q2',
    'Ninety_One_Commodity_2020Q3', 'Ninety_One_Commodity_2020Q4', 'Ninety_One_Commodity_2021Q1',
    'Ninety_One_Commodity_2021Q2', 'Ninety_One_Commodity_2021Q3', 'Ninety_One_Commodity_2021Q4',
    'Ninety_One_Commodity_2022Q1', 'Ninety_One_Commodity_2022Q2', 'Ninety_One_Commodity_2022Q3',
    'Ninety_One_Commodity_2022Q4'
]
```

### Collect Unique FundISIN and Tickers


```python
# Initialize an empty dictionary to store unique FundISIN and their corresponding Tickers
unique_stocks = {}

# Iterate through each sheet and collect unique FundISIN and Tickers
for sheet in sheet_names:
    df = pd.read_excel(file_path, sheet_name=sheet)
    
    # Iterate through each row in the DataFrame
    for index, row in df.iterrows():
        fund_isin = row['FundISIN']
        ticker = row['Ticker']
        
        # Add the FundISIN and Ticker to the dictionary if FundISIN is not already present
        if fund_isin not in unique_stocks:
            unique_stocks[fund_isin] = ticker

# Convert the dictionary to a DataFrame for better visualization and handling
unique_stocks_df = pd.DataFrame(list(unique_stocks.items()), columns=['FundISIN', 'Ticker'])

# Sort the DataFrame alphabetically by the 'FundISIN' column
unique_stocks_df.sort_values(by='FundISIN', inplace=True)

# Reset the index after sorting
unique_stocks_df.reset_index(drop=True, inplace=True)
```

### Extract Quarters from Sheet Names


```python
# Create set to store quarters
quarters = set()

# Extract quarters from sheet names
for i in range(len(sheet_names)):
    quarter = sheet_names[i][len('Ninety_One_Commodity_'):]
    quarters.add(quarter)

quarters = sorted(list(quarters))
```

### Create DataFrame for Stocks and Quarters


```python
# Create column list for final_stock_df columns
column_list = ['Ticker'] + quarters
column_list

# Create an empty DataFrame with rows as unique stocks and columns as quarters
final_stock_df = pd.DataFrame(index=sorted(list(unique_stocks)), columns=column_list)

```

### Populate the final_stock_df Dataframe with Stock Data


```python
for quarter in quarters:
    sheet_name = f'Ninety_One_Commodity_{quarter}'  # Adjust the sheet name based on the quarter
    sheet_df = pd.read_excel(file_path, sheet_name=sheet_name)  # Read the sheet
    
    for isin in list(sheet_df['FundISIN']):
        if isin in final_stock_df.index:
            row_number = final_stock_df.index.get_loc(isin)
            final_stock_df.loc[isin, quarter] = 1 
            
            # Find the corresponding Ticker from sheet_df using boolean indexing
            ticker_value = sheet_df.loc[sheet_df['FundISIN'] == isin, 'Ticker'].values[0]
            final_stock_df.loc[isin, 'Ticker'] = ticker_value

final_stock_df.fillna(0, inplace=True)
```

    C:\Users\27825\AppData\Local\Temp\ipykernel_19684\2739135139.py:14: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      final_stock_df.fillna(0, inplace=True)
    

### Save the Combined DataFrame to Excel


```python
# Define the file path for saving the Excel file.
save_path = r'C:\Users\27825\Documents\02_Corporate Profile\Project Portfolio\Buxton Project\output.xlsx'

# Export 'final_stock_df' DataFrame to Excel at 'save_path'.
final_stock_df.to_excel(save_path, index=True)
```

### Validate Data Consistency


```python
# Counting the number of stocks held in the Mutual Fund over the entire period
df_check = pd.DataFrame(index=sorted(list(quarters)), columns=['Actual','Calculated'])

for quarter in sorted(quarters):
    sheet_name = f'Ninety_One_Commodity_{quarter}'
    df = pd.read_excel(file_path, sheet_name=sheet_name)
    df_check.loc[quarter,'Actual'] = len(df['FundISIN'])

for quarter in sorted(quarters):
    df_check.loc[quarter,'Calculated'] = sum(pd.to_numeric(final_stock_df[quarter], errors='coerce'))

df_check['Difference'] = df_check['Actual'] - df_check["Calculated"]
print(df_check)
```

           Actual Calculated Difference
    2005Q1     21         21          0
    2005Q2     18         18          0
    2005Q3     23         23          0
    2005Q4     22         22          0
    2006Q1     22         22          0
    ...       ...        ...        ...
    2021Q4     26         26          0
    2022Q1     30         30          0
    2022Q2     35         35          0
    2022Q3     33         33          0
    2022Q4     32         32          0
    
    [70 rows x 3 columns]
    


```python

```
