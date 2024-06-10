# Notes:

1) Sex variable has 3 factors (0,1,2) which relate to "Male", "Female", "Unknown"
2) INSR_TYPE variable has 3 factors (1201,1202,1204) which relate to "Comprehensive", "Third Party with Fire and Theft", "Third Party Only"
3) Where there was missing data pertaining to a policyholder, all data surrounding that policyholder was removed, as the purpose is to at a later stage compile a summary for each policyholder

# Initial Setup

### Loading required Packages


```R
library(psych)
```

### Setting working directory


```R
setwd("~/02_Corporate Profile/Project Portfolio/Vehicle Insurance Data")
```

### Loading all vehicle insurance data


```R
motor_data_2014_2018 = read.csv("~/02_Corporate Profile/Project Portfolio/Vehicle Insurance Data/motor_data14-2018.csv")
```

# Initial Data Inspection & Cleaning


```R

```
