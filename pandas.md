# Pandas

## Introduction

Pandas is a python library for data analysis and manipulation. Pandas provides two types of classes for handling data:

* Series (https://pandas.pydata.org/docs/reference/api/pandas.Series.html#pandas.Series)

* DataFrame (https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html#pandas.DataFrame)

```
dates = pd.date_range("20130101", periods=6)

dates
Out[6]: 
DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
               '2013-01-05', '2013-01-06'],
              dtype='datetime64[ns]', freq='D')
```

### Simple Methods to View Data

You can use following simple methods to view data:

```
df.head()

df.tail(3)

df.index

df.columns

df.to_numpy()

df.describe()

df.T

df.sort_index(axis=1, ascending=False)

df.sort_values(by="B")

df.nlargest(3, "B)

df["A"]

df[0:3]

df["20130102":"20130104"]
```

### Simple Methods to Select Data

```
df.loc[dates[0]]

df.loc[:, ["A", "B"]]

df.loc["20130102":"20130104", ["A", "B"]]

df.iloc[3]

df.iloc[3:5, 0:2]

df[df["A"] > 0]

df2[df2["E"].isin(["two", "four"])]
```

### Simple Methods to Set Data

```
df["F"] = s1

df.at[dates[0], "A"] = 0

df.iat[0, 1] = 0

df.loc[:, "D"] = np.array([5] * len(df))

df2[df2 > 0] = -df2
```

### References

https://pandas.pydata.org/docs/user_guide/10min.html

https://pandas.pydata.org/docs/user_guide/cookbook.html#cookbook

## Chart Visualization

The `plot` method allows to do basic plotting:

```
In [3]: np.random.seed(123456)

In [4]: ts = pd.Series(np.random.randn(1000), index=pd.date_range("1/1/2000", periods=1000))

In [5]: ts = ts.cumsum()

In [6]: ts.plot();
```

The [Cookbook](https://pandas.pydata.org/docs/user_guide/cookbook.html#cookbook-plotting) has more advanced strategies of plotting.

### References

https://pandas.pydata.org/docs/user_guide/visualization.html

## Table Visualization

The [Styler class](https://pandas.pydata.org/docs/reference/api/pandas.io.formats.style.Styler.html) is returned from the `DataFrame.style` method.

The methods `.format()` and `.format_index()` are used to control the display value and to format it differently than the actual value. The methods are using the [format spec string](https://docs.python.org/3/library/string.html#format-specification-mini-language).

```
import pandas as pd
import numpy as np
import matplotlib as mpl

df = pd.DataFrame({
    "strings": ["Adam", "Mike"],
    "ints": [1, 3],
    "floats": [1.123, 1000.23]
})
df.style \
  .format(precision=3, thousands=".", decimal=",") \
  .format_index(str.upper, axis=1) \
  .relabel_index(["row 1", "row 2"], axis=0)
```

### References

https://pandas.pydata.org/docs/user_guide/style.html
