# Assignment-for-Data-Analyst
Interpreting the correlation between variables

Given data is coming from a battery installed in telecom tower. There are different values ralated to the battery.
Task is to find the correlations between two pairs of values
   1) Grid status and SOC
   2) Equivalent cycles and SOH
   3) SOC and Temprature and visualise the above mentioned pairs.

## Solution to the above mentioned task

import pandas as pd
import numpy as np
from scipy.stats import pearsonr
import seaborn as sns
import matplotlib.pyplot as plt
get_ipython().run_line_magic('matplotlib', 'inline')
matplotlib.style.use('ggplot')

# Read Data
data=pd.read_csv("./batteries.csv")

# Data Analysis
data.head()
data.dtypes
# Conclusion:*All Entities are Integer or Float types*

data.isna().sum()
# There are no NA values in this dataframe

## Task-1
### Calculate Correlation between Grid Status and SOC

Correlation1=np.corrcoef(data["Grid status"],data["SOC"])
print("The correlation between Grid Status and SOC is {}".format(Correlation1[0]))
# *Conclusion:* The value 0.22 is very small which means the Grid Status and SOC have weak linear relationship. 
#  It shows a Positive Correlation.

# Data visualisation
sns.set(style = "darkgrid" )
sns.regplot(x='Grid status',y='SOC', data=data, marker="*", color="red", fit_reg=True) # scatter plot and linear regplot
plt.show()


## Task-2
### Calculate Correlation between Equivalent Cycle and SOH

Correlation2=np.corrcoef(data["Equivalent cycle"],data["SOH"])
print("The correlation between Equivalent and SOH is {}".format(Correlation2[0]))
# *Conclusion:* The value -0.9842 is close to -1 which means Equivalent cycle and SOH shows a stong (negative) linear relationship.
# It shows a Positive Correlation.

# Data visualisation
sns.set(style = "darkgrid" )
sns.regplot(x='Equivalent cycle',y='SOH', data=data, marker="*", color="blue", fit_reg=True)  # scatter plot and linear regplot
plt.show()

## Task-3
### Calculate Correlation between SOC and Temprature
Correlation3=np.corrcoef(data["SOC"],data["Temperature"])
print("The correlation between SOC and Temperature is {}".format(Correlation3[0]))
# *Conclusion:* The value -0.3690 is small which means SOC and Temperature shows a weak (negative) linear relationship.
# It shows a Negative Correlation.

# Data visualisation
sns.set(style = "darkgrid" )
sns.regplot(x='SOC',y='Temperature', data=data, marker="*", color="purple", fit_reg=True)   # scatter plot and linear regplot 
plt.show()

