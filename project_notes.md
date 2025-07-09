My Note of cleaning dateset of Online_Shopp
day1:
من دیتاست هارو از kaggle.com دانلود کردم .

I used "Online Shop 2024" dateset of kaggle(https://www.kaggle.com/datasets/marthadimgba/online-shop-2024?select=suppliers.csv)
-------------------------------------
To make sure I installed pandas, I used the code
!pip install pandas

I used this method to read the files(customers):
---
%cd C:\Users\hp\OneDrive\Desktop\ecommerce-data-engineering\raw_data       # مسیر دیتاست ها 
از %cd استفاده می‌کنیم تا مسیر نوت‌بوک را به پوشه raw_data تغییر دهیم و بعد بتوانیم راحت فایل‌ها را بدون آدرس کامل بخوانیم. 

--In this project I have 8 tables that I will clean separately.
--
import os
print(os.listdir())    # نمایش فایل‌های موجود در پوشه

['customers.csv', 'orders.csv', 'order_items.csv', 'payment.csv', 'products.csv', 'reviews.csv', 'shipments.csv', 'suppliers.csv']

import pandas as pd   کتابخانه pandas رو صدا میزنیم که بتونیم از تابع های اون استفاده کنیم و به اختصار pd می نامیم 
customers = pd.read_csv('customers.csv')  # بدون نیاز به مسیر 
customers.head()

customer_id	first_name	last_name	address	              email	              phone_number
0	1	James	Smith	123 Main St, Springfield, IL	jsmith1@customer.com	       555-190-3233
1	2	James	Johnson123 Main St, Springfield, IL	jjohnson2@customer.com	555-525-8357
2	3	James	Williams123 Main St, Springfield, IL	jwilliams3@customer.com	555-933-4447
3	4	James	Brown	123 Main St, Springfield, IL	jbrown4@customer.com	       555-897-0326
4	5	James	Jones	123 Main St, Springfield, IL	jjones5@customer.com	       555-762-5836

    customers.shape    # تعداد ستون ها و سطرها
    (10000,6)
    
    customer.info  # یک سری اطلاعات درباره data ها میده 
.
.
.

---Questions--
------------------------------------------------------------
چند فایل مختلف داریم؟
import os
print(os.listdir())    # نمایش فایل‌های موجود در پوشه

['customers.csv', 'orders.csv', 'order_items.csv', 'payment.csv', 'products.csv', 'reviews.csv', 'shipments.csv', 'suppliers.csv']
8 Files
هر فایل چند رکورد دارد؟
import pandas as pd
customers = pd.read_csv('customers.csv')   
customers.head()    => (10000, 6)  => 10000 records

...........................................................
orders = pd.read_csv('orders.csv')
orders.shape       => (15000, 4)   => 15000 records

...............................................................
order_items =pd.read_csv('order_items.csv')
order_items.shape  =>  (20000, 5) => 20000 records

...................................................................
payment = pd.read_csv('payment.csv')
payment.shape      =>  (15000, 5) => 15000 records

........................................................................
products = pd.read_csv('products.csv')
products.shape     =>  (2000, 5) => 2000 records

..............................................................................
reviews = pd.read_csv('reviews.csv')
reviews.shape     =>  (1106, 6) => 1106 records

......................................................................................
shipments = pd.read_csv('shipments.csv')
shipments.shape   => (15000, 7)  => 15000 records

..............................................................................................
suppliers = pd.read_csv('suppliers.csv')
suppliers.shape   => (100, 6)  => 100 records

.......................................................................................................

داده‌ها کلید مشترک دارند؟

