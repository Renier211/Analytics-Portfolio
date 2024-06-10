```python
import pandas as pd
```


```python
file_path = r'C:\Users\27825\Documents\02_Corporate Profile\Project Portfolio\Buxton Project\91.xlsx'
```


```python
all_sheets = pd.read_excel(file_path, sheet_name=None)
```


```python
print(all_sheets.keys())
```

    dict_keys(['Ninety_One_Commodity_2005Q1', 'Ninety_One_Commodity_2005Q2', 'Ninety_One_Commodity_2005Q3', 'Ninety_One_Commodity_2005Q4', 'Ninety_One_Commodity_2006Q1', 'Ninety_One_Commodity_2006Q2', 'Ninety_One_Commodity_2006Q3', 'Ninety_One_Commodity_2006Q4', 'Ninety_One_Commodity_2007Q1', 'Ninety_One_Commodity_2007Q3', 'Ninety_One_Commodity_2008Q1', 'Ninety_One_Commodity_2008Q2', 'Ninety_One_Commodity_2008Q3', 'Ninety_One_Commodity_2008Q4', 'Ninety_One_Commodity_2009Q1', 'Ninety_One_Commodity_2009Q2', 'Ninety_One_Commodity_2009Q3', 'Ninety_One_Commodity_2009Q4', 'Ninety_One_Commodity_2010Q1', 'Ninety_One_Commodity_2010Q2', 'Ninety_One_Commodity_2010Q3', 'Ninety_One_Commodity_2010Q4', 'Ninety_One_Commodity_2011Q1', 'Ninety_One_Commodity_2011Q2', 'Ninety_One_Commodity_2011Q3', 'Ninety_One_Commodity_2011Q4', 'Ninety_One_Commodity_2012Q1', 'Ninety_One_Commodity_2012Q2', 'Ninety_One_Commodity_2012Q3', 'Ninety_One_Commodity_2012Q4', 'Ninety_One_Commodity_2013Q1', 'Ninety_One_Commodity_2013Q2', 'Ninety_One_Commodity_2013Q3', 'Ninety_One_Commodity_2013Q4', 'Ninety_One_Commodity_2014Q1', 'Ninety_One_Commodity_2014Q2', 'Ninety_One_Commodity_2014Q3', 'Ninety_One_Commodity_2014Q4', 'Ninety_One_Commodity_2015Q1', 'Ninety_One_Commodity_2015Q2', 'Ninety_One_Commodity_2015Q3', 'Ninety_One_Commodity_2015Q4', 'Ninety_One_Commodity_2016Q1', 'Ninety_One_Commodity_2016Q2', 'Ninety_One_Commodity_2016Q3', 'Ninety_One_Commodity_2016Q4', 'Ninety_One_Commodity_2017Q1', 'Ninety_One_Commodity_2017Q2', 'Ninety_One_Commodity_2017Q3', 'Ninety_One_Commodity_2017Q4', 'Ninety_One_Commodity_2018Q1', 'Ninety_One_Commodity_2018Q2', 'Ninety_One_Commodity_2018Q3', 'Ninety_One_Commodity_2018Q4', 'Ninety_One_Commodity_2019Q1', 'Ninety_One_Commodity_2019Q2', 'Ninety_One_Commodity_2019Q3', 'Ninety_One_Commodity_2019Q4', 'Ninety_One_Commodity_2020Q1', 'Ninety_One_Commodity_2020Q2', 'Ninety_One_Commodity_2020Q3', 'Ninety_One_Commodity_2020Q4', 'Ninety_One_Commodity_2021Q1', 'Ninety_One_Commodity_2021Q2', 'Ninety_One_Commodity_2021Q3', 'Ninety_One_Commodity_2021Q4', 'Ninety_One_Commodity_2022Q1', 'Ninety_One_Commodity_2022Q2', 'Ninety_One_Commodity_2022Q3', 'Ninety_One_Commodity_2022Q4'])
    


```python
print(all_sheets['Ninety_One_Commodity_2005Q1'])
```

                                   FundISIN Ticker  FirstDate    Weight  \
    0                      BHP Billiton PLC    BLT 2005-03-31  20.39845   
    1                           Sasol, Ltd.    SOL 2005-03-31  14.08312   
    2                    Anglo American PLC    AAL 2005-03-31  11.73502   
    3         Mittal Steel South Africa Ltd    ACL 2005-03-31   9.99259   
    4              Impala Platinum Holdings    IMP 2005-03-31   8.00847   
    5                        Assore Limited    ASR 2005-03-31   5.42667   
    6                                  Aeci    AFE 2005-03-31   4.76068   
    7                   Kumba Resources Ltd    EXX 2005-03-31   3.99115   
    8             AngloGold Ashanti Limited    ANG 2005-03-31   3.69559   
    9               Cash & Cash Equivalents    NaN        NaT   2.70078   
    10                      Trans Hex Group   TSXJ 2005-03-31   2.59205   
    11                           Lonmin PLC  LNMIF 2005-03-31   1.96756   
    12                  Gold Fields Limited    GFI 2005-03-31   1.94923   
    13                       Dorbyl Limited    DLV 2005-03-31   1.89397   
    14                 Illovo Sugar Limited    ILV 2005-03-31   1.70430   
    15      Palabora Mining Company Limited  PBOAF 2005-03-31   1.26892   
    16               Omnia Holdings Limited    OMN 2005-03-31   1.09517   
    17                   Group Five Limited    G6N 2005-03-31   0.77325   
    18                           Gencor Ltd    GCR 2005-03-31   0.67635   
    19                      Sallies Limited    SAL 2005-03-31   0.66526   
    20  Distrib. And Warehousing Network Ld    DAW 2005-03-31   0.62142   
    
           Shares     Value  
    0    467800.0  39225030  
    1    186457.0  27081015  
    2    153300.0  22565760  
    3    302601.0  19215164  
    4     29333.0  15399825  
    5     96622.0  10435176  
    6    215400.0   9154500  
    7    113700.0   7674750  
    8     32900.0   7106400  
    9         NaN   5193443  
    10   284821.0   4984368  
    11    32900.0   3783500  
    12    51700.0   3748250  
    13   121400.0   3642000  
    14   404600.0   3277260  
    15    73941.0   2440053  
    16    50082.0   2105948  
    17   102900.0   1486905  
    18  8670520.0   1300578  
    19  4738000.0   1279260  
    20   229800.0   1194960  
    


```python
# List of all sheet names
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


```python
# Initialize an empty set to store unique stocks
unique_stocks = set()
```


```python
# Iterate through each sheet and collect unique stock names
for sheet in sheet_names:
    df = pd.read_excel(file_path, sheet_name=sheet)
    ticker = df['Ticker']  # Assuming the column name for stocks is 'Stock Name'
    unique_stocks.update(ticker)
```


```python
# Convert the set to a DataFrame
unique_stocks_df = pd.DataFrame(unique_stocks, columns=['Unique Stocks'])
```


```python
# Display the DataFrame
print(unique_stocks_df)
```

        Unique Stocks
    0             HAR
    1            GFI2
    2              HL
    3             ELR
    4             GFI
    ..            ...
    220           CCJ
    221        ETFRHO
    222           CCO
    223          AEG1
    224           DTA
    
    [225 rows x 1 columns]
    


```python
quarters = set()
```


```python
for i in range(0,len(sheet_names)):
    quarter = sheet_names[i][len('Ninety_One_Commodity_'):]
    quarters.add(quarter)

quarters 
```




    {'2005Q1',
     '2005Q2',
     '2005Q3',
     '2005Q4',
     '2006Q1',
     '2006Q2',
     '2006Q3',
     '2006Q4',
     '2007Q1',
     '2007Q3',
     '2008Q1',
     '2008Q2',
     '2008Q3',
     '2008Q4',
     '2009Q1',
     '2009Q2',
     '2009Q3',
     '2009Q4',
     '2010Q1',
     '2010Q2',
     '2010Q3',
     '2010Q4',
     '2011Q1',
     '2011Q2',
     '2011Q3',
     '2011Q4',
     '2012Q1',
     '2012Q2',
     '2012Q3',
     '2012Q4',
     '2013Q1',
     '2013Q2',
     '2013Q3',
     '2013Q4',
     '2014Q1',
     '2014Q2',
     '2014Q3',
     '2014Q4',
     '2015Q1',
     '2015Q2',
     '2015Q3',
     '2015Q4',
     '2016Q1',
     '2016Q2',
     '2016Q3',
     '2016Q4',
     '2017Q1',
     '2017Q2',
     '2017Q3',
     '2017Q4',
     '2018Q1',
     '2018Q2',
     '2018Q3',
     '2018Q4',
     '2019Q1',
     '2019Q2',
     '2019Q3',
     '2019Q4',
     '2020Q1',
     '2020Q2',
     '2020Q3',
     '2020Q4',
     '2021Q1',
     '2021Q2',
     '2021Q3',
     '2021Q4',
     '2022Q1',
     '2022Q2',
     '2022Q3',
     '2022Q4'}




```python
len(quarters)
```




    70




```python
stock_df = pd.DataFrame(index=range(len(unique_stocks_df)), columns=range(len(quarters)))
#stock_df.index = unique_stocks_df
stock_df.columns = quarters

```


```python
# Display the DataFrame
print(stock_df)
```

        2010Q2 2022Q3 2009Q2 2006Q1 2007Q1 2011Q4 2013Q4 2017Q3 2017Q4 2012Q4  \
    0      NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN   
    1      NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN   
    2      NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN   
    3      NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN   
    4      NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN   
    ..     ...    ...    ...    ...    ...    ...    ...    ...    ...    ...   
    220    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN   
    221    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN   
    222    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN   
    223    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN   
    224    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN   
    
         ... 2005Q4 2011Q3 2019Q4 2011Q2 2012Q1 2009Q4 2018Q4 2012Q3 2010Q4 2013Q2  
    0    ...    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN  
    1    ...    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN  
    2    ...    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN  
    3    ...    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN  
    4    ...    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN  
    ..   ...    ...    ...    ...    ...    ...    ...    ...    ...    ...    ...  
    220  ...    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN  
    221  ...    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN  
    222  ...    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN  
    223  ...    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN  
    224  ...    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN  
    
    [225 rows x 70 columns]
    


```python
print(stock_df.index)
print(stock_df.columns)
```

    Index([   ('HAR',),   ('GFI2',),     ('HL',),    ('ELR',),    ('GFI',),
              ('OCE',),   ('DRD2',),   ('NOC2',),   ('ILV3',),    ('WDS',),
           ...
              ('HES',),      (nan,),    ('UCP',),   ('HAR2',),    ('PET',),
              ('CCJ',), ('ETFRHO',),    ('CCO',),   ('AEG1',),    ('DTA',)],
          dtype='object', length=225)
    Index(['2010Q2', '2022Q3', '2009Q2', '2006Q1', '2007Q1', '2011Q4', '2013Q4',
           '2017Q3', '2017Q4', '2012Q4', '2014Q4', '2006Q2', '2006Q3', '2008Q4',
           '2019Q1', '2009Q3', '2022Q2', '2021Q4', '2016Q1', '2006Q4', '2016Q3',
           '2016Q4', '2013Q3', '2015Q1', '2013Q1', '2015Q2', '2015Q4', '2005Q3',
           '2017Q2', '2012Q2', '2020Q2', '2021Q2', '2020Q3', '2014Q3', '2007Q3',
           '2010Q1', '2009Q1', '2021Q3', '2022Q1', '2020Q4', '2010Q3', '2008Q3',
           '2018Q2', '2018Q1', '2008Q1', '2014Q2', '2014Q1', '2016Q2', '2011Q1',
           '2019Q3', '2021Q1', '2008Q2', '2005Q2', '2022Q4', '2005Q1', '2017Q1',
           '2018Q3', '2020Q1', '2019Q2', '2015Q3', '2005Q4', '2011Q3', '2019Q4',
           '2011Q2', '2012Q1', '2009Q4', '2018Q4', '2012Q3', '2010Q4', '2013Q2'],
          dtype='object')
    


```python
print(stock_df.iloc[[0],[69]])
```

      2013Q2
    0    NaN
    


```python

```
