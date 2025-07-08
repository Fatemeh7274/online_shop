My Note of cleaning dateset of Online_Shopp
day1:

I used "Online Shop 2024" dateset of kaggle(https://www.kaggle.com/datasets/marthadimgba/online-shop-2024?select=suppliers.csv)
-------------------------------------
To make sure I installed pandas, I used the code
!pip install pandas

I used this method to read the files:
---
import pandas as pd
import os

folder_path = r"C:\Users\hp\OneDrive\Desktop\ecommerce-data-engineering\raw_data"

customers = pd.read_csv(os.path.join(folder_path, "customers.csv"))

print(customers.head()) 

--In this project I have 8 tables that I will clean separately.
--
customers:  
print(customers.shape)    (10000, 6)

Index(['customer_id', 'first_name', 'last_name', 'address', 'email',
       'phone_number'],
      dtype='object')


