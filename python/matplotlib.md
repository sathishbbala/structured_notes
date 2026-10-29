

``` python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

x = [1,2,3,4,5,6,7,8,9,10]
y = [0.9, 0.6, 0.4, 0.3, 0.8, 0.1, 0.7, 0.4, 0.6, 0.5]
plt.xlabel('Numbers')
plt.ylabel('Probability of Numbers')
plt.title("Basic Line Graph", fontdict={"fontname": "Calibri", "fontsize": 20})

plt.xticks([0,2,4,6,8])
plt.yticks([0.0,0.2,0.4,0.6,0.8])
plt.plot(x,y, label = 'prob(x)', color = '#616161', linewidth = 2, 
          marker = '.', markersize = 10, linestyle = '--', markeredgecolor = 'blue')
plt.show()

```
<img width="640" height="480" alt="Figure_1" src="https://github.com/user-attachments/assets/647c77d7-cd8d-4bb7-b22a-f2e477644eab" />
