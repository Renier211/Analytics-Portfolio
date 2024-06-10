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
# Path to the Excel data file
file_path = r'C:\Users\27825\Documents\02_Corporate Profile\Project Portfolio\Buxton Project\91.xlsx'

# Read all sheets of the Excel file into a dictionary
all_sheets = pd.read_excel(file_path, sheet_name=None)

# Convert the dictionary keys to a list and assign to sheet_names
sheet_names = list(all_sheets.keys())
print(sheet_names)
```

    ['Ninety_One_Commodity_2005Q1', 'Ninety_One_Commodity_2005Q2', 'Ninety_One_Commodity_2005Q3', 'Ninety_One_Commodity_2005Q4', 'Ninety_One_Commodity_2006Q1', 'Ninety_One_Commodity_2006Q2', 'Ninety_One_Commodity_2006Q3', 'Ninety_One_Commodity_2006Q4', 'Ninety_One_Commodity_2007Q1', 'Ninety_One_Commodity_2007Q3', 'Ninety_One_Commodity_2008Q1', 'Ninety_One_Commodity_2008Q2', 'Ninety_One_Commodity_2008Q3', 'Ninety_One_Commodity_2008Q4', 'Ninety_One_Commodity_2009Q1', 'Ninety_One_Commodity_2009Q2', 'Ninety_One_Commodity_2009Q3', 'Ninety_One_Commodity_2009Q4', 'Ninety_One_Commodity_2010Q1', 'Ninety_One_Commodity_2010Q2', 'Ninety_One_Commodity_2010Q3', 'Ninety_One_Commodity_2010Q4', 'Ninety_One_Commodity_2011Q1', 'Ninety_One_Commodity_2011Q2', 'Ninety_One_Commodity_2011Q3', 'Ninety_One_Commodity_2011Q4', 'Ninety_One_Commodity_2012Q1', 'Ninety_One_Commodity_2012Q2', 'Ninety_One_Commodity_2012Q3', 'Ninety_One_Commodity_2012Q4', 'Ninety_One_Commodity_2013Q1', 'Ninety_One_Commodity_2013Q2', 'Ninety_One_Commodity_2013Q3', 'Ninety_One_Commodity_2013Q4', 'Ninety_One_Commodity_2014Q1', 'Ninety_One_Commodity_2014Q2', 'Ninety_One_Commodity_2014Q3', 'Ninety_One_Commodity_2014Q4', 'Ninety_One_Commodity_2015Q1', 'Ninety_One_Commodity_2015Q2', 'Ninety_One_Commodity_2015Q3', 'Ninety_One_Commodity_2015Q4', 'Ninety_One_Commodity_2016Q1', 'Ninety_One_Commodity_2016Q2', 'Ninety_One_Commodity_2016Q3', 'Ninety_One_Commodity_2016Q4', 'Ninety_One_Commodity_2017Q1', 'Ninety_One_Commodity_2017Q2', 'Ninety_One_Commodity_2017Q3', 'Ninety_One_Commodity_2017Q4', 'Ninety_One_Commodity_2018Q1', 'Ninety_One_Commodity_2018Q2', 'Ninety_One_Commodity_2018Q3', 'Ninety_One_Commodity_2018Q4', 'Ninety_One_Commodity_2019Q1', 'Ninety_One_Commodity_2019Q2', 'Ninety_One_Commodity_2019Q3', 'Ninety_One_Commodity_2019Q4', 'Ninety_One_Commodity_2020Q1', 'Ninety_One_Commodity_2020Q2', 'Ninety_One_Commodity_2020Q3', 'Ninety_One_Commodity_2020Q4', 'Ninety_One_Commodity_2021Q1', 'Ninety_One_Commodity_2021Q2', 'Ninety_One_Commodity_2021Q3', 'Ninety_One_Commodity_2021Q4', 'Ninety_One_Commodity_2022Q1', 'Ninety_One_Commodity_2022Q2', 'Ninety_One_Commodity_2022Q3', 'Ninety_One_Commodity_2022Q4']
    

### Collect Unique FundISIN and Tickers


```python
# Create an empty dictionary to store unique FundISIN and their corresponding Tickers
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

# Convert the dictionary to a dataframe for better visualization and handling
unique_stocks_df = pd.DataFrame(list(unique_stocks.items()), columns=['FundISIN', 'Ticker'])

# Sort the dataframe alphabetically by the 'FundISIN' column
unique_stocks_df.sort_values(by='FundISIN', inplace=True)

# Reset the index of the dataframe after sorting
unique_stocks_df.reset_index(drop=True, inplace=True)
unique_stocks_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>FundISIN</th>
      <th>Ticker</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A E C I Limited</td>
      <td>AFE</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ABSA BANK LTD ZAR Call Account Cash</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>AECI Ltd</td>
      <td>AFE</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abn Amro Bank Nv Sa Branch</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Absa Bank Ltd Zar Call Account</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>300</th>
      <td>Yellow Cake Plc Ordinary Shares</td>
      <td>YCA</td>
    </tr>
    <tr>
      <th>301</th>
      <td>Zambezi Platinum Pfd</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>302</th>
      <td>Zijin Mining Group Co., Ltd.</td>
      <td>02899</td>
    </tr>
    <tr>
      <th>303</th>
      <td>db Monthly Short WTI Crude Oil ETC</td>
      <td>XETW</td>
    </tr>
    <tr>
      <th>304</th>
      <td>db Physical Rhodium ETC</td>
      <td>XRH0</td>
    </tr>
  </tbody>
</table>
<p>305 rows × 2 columns</p>
</div>



### Extract Quarters from Sheet Names


```python
# Create set to store quarters
quarters = set()

# Extract quarters from sheet names
for i in range(len(sheet_names)):
    quarter = sheet_names[i][len('Ninety_One_Commodity_'):]
    quarters.add(quarter)

quarters = sorted(list(quarters))
print(quarters)
```

    ['2005Q1', '2005Q2', '2005Q3', '2005Q4', '2006Q1', '2006Q2', '2006Q3', '2006Q4', '2007Q1', '2007Q3', '2008Q1', '2008Q2', '2008Q3', '2008Q4', '2009Q1', '2009Q2', '2009Q3', '2009Q4', '2010Q1', '2010Q2', '2010Q3', '2010Q4', '2011Q1', '2011Q2', '2011Q3', '2011Q4', '2012Q1', '2012Q2', '2012Q3', '2012Q4', '2013Q1', '2013Q2', '2013Q3', '2013Q4', '2014Q1', '2014Q2', '2014Q3', '2014Q4', '2015Q1', '2015Q2', '2015Q3', '2015Q4', '2016Q1', '2016Q2', '2016Q3', '2016Q4', '2017Q1', '2017Q2', '2017Q3', '2017Q4', '2018Q1', '2018Q2', '2018Q3', '2018Q4', '2019Q1', '2019Q2', '2019Q3', '2019Q4', '2020Q1', '2020Q2', '2020Q3', '2020Q4', '2021Q1', '2021Q2', '2021Q3', '2021Q4', '2022Q1', '2022Q2', '2022Q3', '2022Q4']
    

### Create DataFrame for Quarterly Stock Data


```python
# Create column list for final_stock_df columns
column_list = ['Ticker'] + quarters
column_list

# Create an empty DataFrame with rows as unique stocks and columns as quarters
final_stock_df = pd.DataFrame(index=sorted(list(unique_stocks)), columns=column_list)
final_stock_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
      <th>2005Q1</th>
      <th>2005Q2</th>
      <th>2005Q3</th>
      <th>2005Q4</th>
      <th>2006Q1</th>
      <th>2006Q2</th>
      <th>2006Q3</th>
      <th>2006Q4</th>
      <th>2007Q1</th>
      <th>...</th>
      <th>2020Q3</th>
      <th>2020Q4</th>
      <th>2021Q1</th>
      <th>2021Q2</th>
      <th>2021Q3</th>
      <th>2021Q4</th>
      <th>2022Q1</th>
      <th>2022Q2</th>
      <th>2022Q3</th>
      <th>2022Q4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A E C I Limited</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>ABSA BANK LTD ZAR Call Account Cash</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>AECI Ltd</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Abn Amro Bank Nv Sa Branch</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Absa Bank Ltd Zar Call Account</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 71 columns</p>
</div>



### Populate the final_stock_df Dataframe with Stock Data


```python
# Iterate through each quarter
for quarter in quarters:
    # Adjust the sheet name based on the quarter
    sheet_name = f'Ninety_One_Commodity_{quarter}'
    
    # Read the sheet for the given quarter
    sheet_df = pd.read_excel(file_path, sheet_name=sheet_name)
    
    # Iterate through each ISIN in the sheet
    for isin in list(sheet_df['FundISIN']):
        # Check if the ISIN is in the final_stock_df index
        if isin in final_stock_df.index:
            # Get the row number of the ISIN in the final_stock_df
            row_number = final_stock_df.index.get_loc(isin)
            
            # Mark the stock as held in the given quarter
            final_stock_df.loc[isin, quarter] = 1 
            
            # Find the corresponding Ticker from sheet_df using boolean indexing
            ticker_value = sheet_df.loc[sheet_df['FundISIN'] == isin, 'Ticker'].values[0]
            
            # Assign the Ticker value to the final_stock_df
            final_stock_df.loc[isin, 'Ticker'] = ticker_value

# Fill any remaining NaN values with 0
final_stock_df.fillna(0, inplace=True)
final_stock_df.head()
```

    C:\Users\27825\AppData\Local\Temp\ipykernel_26912\232007965.py:26: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      final_stock_df.fillna(0, inplace=True)
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
      <th>2005Q1</th>
      <th>2005Q2</th>
      <th>2005Q3</th>
      <th>2005Q4</th>
      <th>2006Q1</th>
      <th>2006Q2</th>
      <th>2006Q3</th>
      <th>2006Q4</th>
      <th>2007Q1</th>
      <th>...</th>
      <th>2020Q3</th>
      <th>2020Q4</th>
      <th>2021Q1</th>
      <th>2021Q2</th>
      <th>2021Q3</th>
      <th>2021Q4</th>
      <th>2022Q1</th>
      <th>2022Q2</th>
      <th>2022Q3</th>
      <th>2022Q4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A E C I Limited</th>
      <td>AFE</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>ABSA BANK LTD ZAR Call Account Cash</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>AECI Ltd</th>
      <td>AFE</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Abn Amro Bank Nv Sa Branch</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Absa Bank Ltd Zar Call Account</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 71 columns</p>
</div>



### Save the Combined DataFrame to Excel


```python
# Define the file path for saving the Excel file
save_path = r'C:\Users\27825\Documents\02_Corporate Profile\Project Portfolio\Buxton Project\output.xlsx'

# Export 'final_stock_df' DataFrame to Excel at 'save_path'
final_stock_df.to_excel(save_path, index=True)
```
