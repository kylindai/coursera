# City Accident Severity Prediction

## 2. Data description

### 2.1 data source
We get the data of collisions from the government website of The Seattle City, updated at October 3, 2020   
https://data.seattle.gov/Land-Base/Collisions/9kas-rb8d

### 2.2 dataset summary
This includes all types of collisions. Collisions will display at the intersection or
mid-block of a segment. Timeframe: 2004 to Present.

```python
import pandas as pd

df = pd.read_csv('./data/Collisions.csv')

print(df.shape)

(221525, 40)
```

### 2.3 data attributes

```python
df.dtypes


X                  float64
Y                  float64
OBJECTID             int64
INCKEY               int64
COLDETKEY            int64
REPORTNO            object
STATUS              object
ADDRTYPE            object
INTKEY             float64
LOCATION            object
EXCEPTRSNCODE       object
EXCEPTRSNDESC       object
SEVERITYCODE        object
SEVERITYDESC        object
COLLISIONTYPE       object
PERSONCOUNT          int64
PEDCOUNT             int64
PEDCYLCOUNT          int64
VEHCOUNT             int64
INJURIES             int64
SERIOUSINJURIES      int64
FATALITIES           int64
INCDATE             object
INCDTTM             object
JUNCTIONTYPE        object
SDOT_COLCODE       float64
SDOT_COLDESC        object
INATTENTIONIND      object
UNDERINFL           object
WEATHER             object
ROADCOND            object
LIGHTCOND           object
PEDROWNOTGRNT       object
SDOTCOLNUM         float64
SPEEDING            object
ST_COLCODE          object
ST_COLDESC          object
SEGLANEKEY           int64
CROSSWALKKEY         int64
HITPARKEDCAR        object
dtype: object

```
There is the data attributes information: https://www.seattle.gov/Documents/Departments/SDOT/GIS/Collisions_OD.pdf

### 2.4 target or label

The target or label column is SEVERITYCODE, that corresponds to the severity of the collision:
* 3—fatality
* 2b—serious injury
* 2—injury
* 1—prop damage
* 0—unknown

The distribution of SEVERITYCODE is as below:

```python
df['SEVERITYCODE'].value_counts()

1     137485
2      58698
0      21635
2b      3098
3        349
Name: SEVERITYCODE, dtype: int64
```


