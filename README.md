# Exno:1

Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
~~~
            import pandas as pd
          import numpy as np
          import seaborn as sns
          import os 
          df=pd.read_csv("SAMPLEIDS.csv")
          df
~~~

![image](https://github.com/user-attachments/assets/64ef021f-44b4-4060-9c7d-f133bdefad62)

~~~

         df.isnull().sum()
~~~

![image](https://github.com/user-attachments/assets/cc21f878-5c8a-49ae-a7ee-c4e8ccb85ce9)

~~~

         df.isnull().any()

~~~

![image](https://github.com/user-attachments/assets/d8a5ac06-07ad-4a68-b3ef-9803bd9b3650)

~~~

         df.dropna()

~~~

![image](https://github.com/user-attachments/assets/f557860f-b7e4-4040-b99f-35bcd59ee874)

~~~

         df.fillna(0)

~~~

![image](https://github.com/user-attachments/assets/c07712d5-c3e2-4ad4-b569-85d1ebf81386)

~~~

         df.fillna(method = 'ffill')

~~~

![image](https://github.com/user-attachments/assets/53a16105-9018-468c-aa4c-730b83d33ff4)

~~~

         df.fillna(method = 'bfill')

~~~

![image](https://github.com/user-attachments/assets/8c2d8f95-88b6-449b-af8d-64699e77621a)

~~~

         df_dropped = df.dropna()
           df_dropped
~~~

![image](https://github.com/user-attachments/assets/40e0c42a-9c86-40ba-ab9c-95e44114670d)

~~~

         df.fillna({'GENDER':'MALE','NAME':'KANISHKAR','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})

~~~

![image](https://github.com/user-attachments/assets/3ba7361a-257c-4aa0-af74-67aac55e13d4)

~~~

         import pandas as pd
         
         ir=pd.read_csv('iris.csv')
         ir

~~~

![image](https://github.com/user-attachments/assets/9ecff74e-c915-4677-9c61-aa36a6cad6d6)

~~~

         ir.describe()

~~~

![image](https://github.com/user-attachments/assets/964f402b-1897-495a-8a52-2871f259d6db)

~~~

         import seaborn as sns
         
         sns.boxplot(x='sepal_width',data=ir)

~~~

![image](https://github.com/user-attachments/assets/d747f55b-b09f-4f1b-a05d-7e07e1ec1a45)

~~~

           c1=ir.sepal_width.quantile(0.25)
           c3=ir.sepal_width.quantile(0.75)
           iq=c3-c1
           print(c3)
~~~
3.3
~~~

            rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
            rid['sepal_width']
~~~

![image](https://github.com/user-attachments/assets/58772d15-a601-42f4-b076-277611e5aee2)

~~~

            delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
            delid

~~~

![image](https://github.com/user-attachments/assets/4f184d9d-67c2-4a35-a6ec-9f1d50c57b99)

~~~

           sns.boxplot(x='sepal_width',data=delid)

~~~

![image](https://github.com/user-attachments/assets/0a96d8e9-21ec-4ef3-aaf2-e4432d1b4403)

~~~

            import matplotlib.pyplot as plt
            import pandas as pd
            import numpy as np
            import scipy.stats as stats

            dataset=pd.read_csv("heights.csv")
            dataset
~~~

![image](https://github.com/user-attachments/assets/b2cea7f7-f84a-49bd-9e2d-325b7793ba13)

~~~

            df = pd.read_csv("heights.csv")
            q1 = df['height'].quantile(0.25)
            q2 = df['height'].quantile(0.5)
            q3 = df['height'].quantile(0.75)
            
            iqr = q3-q1
            iqr

~~~
0.9249999999999998
~~~

        low = q1 - 1.5*iqr
        low
~~~

3.8625000000000003
~~~

        high = q3 + 1.5*iqr
        high
~~~

7.5625

~~~

        df1 = df[((df['height'] >=low)& (df['height'] <=high))]
        df1
~~~

![image](https://github.com/user-attachments/assets/5b8fe13c-2bb2-4283-bc23-ecb79df4a206)

~~~

        z = np.abs(stats.zscore(df['height']))
        z

~~~

![image](https://github.com/user-attachments/assets/0592abaf-3d3d-47fa-94aa-74e1f36e14f8)

~~~

        df1 = df[z<3]
        df1

~~~

![image](https://github.com/user-attachments/assets/a05ae446-5959-4362-94d1-b91f3f8f8da1)

# Result
Thus the given data successfully performed data cleaning and saved the cleaned data to a file.
