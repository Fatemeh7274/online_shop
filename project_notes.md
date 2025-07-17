My Note of cleaning dateset of Online_Shopp
day1:
من دیتاست هارو از kaggle.com دانلود کردم .

I used "Brazilian E-Commerce Public Dataset by Olist" 
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

['olist_customers_dataset.csv', 'olist_geolocation_dataset.csv', 'olist_orders_dataset.csv', 'olist_order_items_dataset.csv', 'olist_order_payments_dataset.csv', 'olist_order_reviews_dataset.csv', 'olist_products_dataset.csv', 'olist_sellers_dataset.csv', 'product_category_name_translation.csv']

import pandas as pd        کتابخانه pandas رو صدا میزنیم که بتونیم از تابع های اون استفاده کنیم و به اختصار pd می نامیم #
olist_customers_dataset = pd.read_csv('olist_customers_dataset.csv')بدون نیاز به مسیر #
olist_customers_dataset.head()  

customer_id	customer_unique_id	customer_zip_code_prefix	customer_city	customer_state
0	06b8999e2fba1a1fbc88172c00ba8bc7	861eff4711a542e4b93843c6dd7febb0	14409	franca	SP
1	18955e83d337fd6b2def6b18a428ac77	290c77bc529b7ac935b93aa66c333dc3	9790	sao bernardo do campo	SP
2	4e7b3e00288586ebd08712fdd0374a03	060e732b5b29e8181a18229c7b0b2b5e	1151	sao paulo	SP
3	b2b6027bc5c5109e529d4dc6358b12c3	259dac757896d24d7702b9acbbff3f3c	8775	mogi das cruzes	SP
4	4f2d8ab171c80ec8364f7c12e35b23ad	345ecd01c38d18a9036ed96c73b8d066	13056	campinas	SP


    olist_customers_dataset.shape    # تعداد ستون ها و سطرها
    (99441, 5)
    
   olist_customers_dataset.info  # یک سری اطلاعات درباره data ها میده 
#   Column                    Non-Null Count  Dtype 
---  ------                    --------------  ----- 
 0   customer_id               99441 non-null  object     این جدول ۵ تا ستون داره #
 1   customer_unique_id        99441 non-null  object
 2   customer_zip_code_prefix  99441 non-null  int64 
 3   customer_city             99441 non-null  object
 4   customer_state            99441 non-null  object
dtypes: int64(1), object(4) 
memory usage: 3.8+ MB
.
.

---Questions--
------------------------------------------------------------
چند فایل مختلف داریم؟
import os
print(os.listdir())    # نمایش فایل‌های موجود در پوشه

['olist_customers_dataset.csv', 'olist_geolocation_dataset.csv', 'olist_orders_dataset.csv', 'olist_order_items_dataset.csv', 'olist_order_payments_dataset.csv', 'olist_order_reviews_dataset.csv', 'olist_products_dataset.csv', 'olist_sellers_dataset.csv', 'product_category_name_translation.csv']
9 Files
هر فایل چند رکورد دارد؟
import pandas as pd
'olist_customers_dataset = pd.read_csv(''olist_customers_dataset.csv')   
'olist_customers_dataset.head()    => (99441, 5)  => 99441 records 
dtypes: int64(1), object(4)
memory usage: 3.8+ MB
olist_customers_dataset.isnull().sum()   این دستور مجموع تعداد # null رو در هر ستون مشخص میکنه 
customer_id                 0
customer_unique_id          0
customer_zip_code_prefix    0
customer_city               0
customer_state              0

olist_geolocation_dataset = pd.read_csv('olist_geolocation_dataset.csv')
olist_geolocation_dataset.shape       => (1000163, 5)   => 1000163 records 
dtypes: float64(2), int64(1), object(2)
memory usage: 38.2+ MB
geolocation_zip_code_prefix    0
geolocation_lat                0
geolocation_lng                0
geolocation_city               0
geolocation_state              0

olist_orders_dataset =pd.read_csv('olist_orders_dataset.csv')
olist_orders_dataset.shape  =>  (99441, 8) => 99441 records  
dtypes: object(8)  
memory usage: 6.1+ MB
order_id                            0
customer_id                         0
order_status                        0
order_purchase_timestamp            0
order_approved_at                 160
order_delivered_carrier_date     1783
order_delivered_customer_date    2965
order_estimated_delivery_date       0


olist_order_items_dataset = pd.read_csv('olist_order_items_dataset.csv')
olist_order_items_dataset.shape      =>  (112650, 7)  => 112650 records
dtypes: float64(2), int64(1), object(4)
memory usage: 6.0+ MB
order_id               0
order_item_id          0
product_id             0
seller_id              0
shipping_limit_date    0
price                  0
freight_value          0



olist_order_payments_dataset = pd.read_csv('olist_order_payments_dataset.csv')
olist_order_payments_dataset.shape     =>  (103886, 5)  => 103886 records
dtypes: float64(1), int64(2), object(2) 
memory usage: 4.0+ MB
order_id                0
payment_sequential      0
payment_type            0
payment_installments    0
payment_value           0


olist_order_reviews_dataset = pd.read_csv('olist_order_reviews_dataset.csv')
olist_order_reviews_dataset.shape     =>  (99224, 7) => 99224 records
dtypes: int64(1), object(6)
memory usage: 5.3+ MB
review_id                      0
order_id                       0
review_score                   0
review_comment_title       87656
review_comment_message     58247
review_creation_date           0
review_answer_timestamp        0

 
olist_products_dataset = pd.read_csv('olist_products_dataset.csv')
olist_products_dataset.shape   => (32951, 9)   => 32951 records
dtypes: float64(7), object(2)
memory usage: 2.3+ MB         
product_id                      0
product_category_name         610
product_name_lenght           610
product_description_lenght    610
product_photos_qty            610
product_weight_g                2
product_length_cm               2
product_height_cm               2
product_width_cm                2

 
olist_sellers_dataset = pd.read_csv('olist_sellers_dataset.csv')
olist_sellers_dataset.shape   => (3095, 4)  => 3095 records
dtypes: int64(1), object(3)
memory usage: 96.8+ KB
seller_id                 0
seller_zip_code_prefix    0
seller_city               0
seller_state              0


product_category_name_translation = pd.read_csv('product_category_name_translation.csv')
product_category_name_translation.shape  =>  (71, 2) 71 records
dtypes: object(2)
memory usage: 1.2+ KB
product_category_name            71
product_category_name_english    71



داده‌ها کلید مشترک دارند؟

olist_customers_dataset table:
customer_id (primary key)

olist_orders_dataset table:
order_id (primary key)
costomer_id (foreign key ref:olist_customers_dataset)

olist_order_items_dataset table:
order_items_id (primary key)
order_id (foreign key ref:olist_orders_dataset)
product_id (foreign key ref:olist_products_dataset)
seller_id (foreign key ref:olist_sellers_dataset)

olist_order_payments_dataset table:
order_id (foreign key ref:olist_orders_dataset)

olist_order_reviews_dataset table:
review_id (primary key)
order_id (foreign key ref:olist_orders_dataset)

olist_products_dataset table:
product_id (primary key)

olist_sellers_dataset table:
seller_id (primary key)

## Issues for Data Cleaning
##Initial review: df.info(), df.describe()
 ## مراحل پاک‌ سازی داد (Data Cleaning Workflow) 
## First, we check the nulls in the tables with : df.isnull().sum()

olist_orders_dataset table has nulls in volumns:
order_approved_at                 160
order_delivered_carrier_date     1783
order_delivered_customer_date    2965


    
 

## تبدیل رشته به "Datetime"

olist_orders_dataset['order_purchase_timestamp'] = pd.to_datetime(olist_orders_dataset['order_purchase_timestamp'])
olist_orders_dataset['order_approved_at'] = pd.to_datetime(olist_orders_dataset['order_approved_at'])
olist_orders_dataset['order_delivered_carrier_date'] = pd.to_datetime(olist_orders_dataset['order_delivered_carrier_date'])
olist_orders_dataset['order_delivered_customer_date'] = pd.to_datetime(olist_orders_dataset['order_delivered_customer_date'])
olist_orders_dataset['order_estimated_delivery_date'] = pd.to_datetime(olist_orders_dataset['order_estimated_delivery_date'])

## تمام ردیف‌هایی که مقدار date آن‌ها خالی (null) هست رو حذف می‌کنیم. 
                      ## "dataframes"میسازم که "null "ها رو نداشته باشه 

olist_orders_dataset = olist_orders_dataset[olist_orders_dataset['order_approved_at'].notnull()]
olist_orders_dataset = olist_orders_dataset[olist_orders_dataset['order_delivered_carrier_date'].notnull()]
olist_orders_dataset = olist_orders_dataset[olist_orders_dataset['order_delivered_customer_date'].notnull()]

olist_orders_dataset.isnull().sum()
order_id                         0
customer_id                      0
order_status                     0
order_purchase_timestamp         0
order_approved_at                0
order_delivered_carrier_date     0
order_delivered_customer_date    0
order_estimated_delivery_date    0

Data columns (total 8 columns):
 #   Column                         Non-Null Count  Dtype         
---  ------                         --------------  -----         
 0   order_id                       99281 non-null  object        
 1   customer_id                    99281 non-null  object        
 2   order_status                   99281 non-null  object        
 3   order_purchase_timestamp       99281 non-null  datetime64[ns]
 4   order_approved_at              99281 non-null  object        
 5   order_delivered_carrier_date   99281 non-null  object        
 6   order_delivered_customer_date  99281 non-null  datetime64[ns]
 7   order_estimated_delivery_date  99281 non-null  object  







 

## olist_order_reviews_dataset table has nulls in column:
review_comment_title       87656
review_comment_message     58247

 خالی‌ها "null "  ها رو با عبارت "No title" یا "No comment" پر میکنم 
چون ترجیح میدم رکوردی رو حذف نکنم .
olist_order_reviews_dataset['review_comment_title'] = olist_order_reviews_dataset['review_comment_title'].fillna('No title')

olist_order_reviews_dataset['review_comment_message'] = olist_order_reviews_dataset['review_comment_message'].fillna('No comment')
olist_order_reviews_dataset.isnull().sum()
دیگه مقدار "null " وجود نداره .
review_id                  0
order_id                   0
review_score               0
review_comment_title       0
review_comment_message     0
review_creation_date       0
review_answer_timestamp    0




olist_products_dataset  table has nulls in columns:
product_id                      0
product_category_name         610
product_name_lenght           610
product_description_lenght    610
product_photos_qty            610
product_weight_g                2
product_length_cm               2
product_height_cm               2
product_width_cm                2

## product_category_name :پر کردن با مقدار "unknown"
olist_products_dataset['product_category_name'] = olist_products_dataset['product_category_name'].fillna("unknown")
یا میتونیم  "null " ها رو حذف کنیم چون تعداد قابل توجهی نیستند.

olist_products_dataset = olist_products_dataset.dropna(subset=['product_name_lenght'])
olist_products_dataset = olist_products_dataset.dropna(subset=['product_description_lenght'])
olist_products_dataset = olist_products_dataset.dropna(subset=['product_photos_qty'])
olist_products_dataset = olist_products_dataset.dropna(subset=['product_weight_g'])
olist_products_dataset = olist_products_dataset.dropna(subset=['product_length_cm'])
olist_products_dataset = olist_products_dataset.dropna(subset=['product_height_cm'])
olist_products_dataset = olist_products_dataset.dropna(subset=['product_width_cm'])

olist_products_dataset.isnull().sum()
product_id                    0
product_category_name         0
product_name_lenght           0
product_description_lenght    0
product_photos_qty            0
product_weight_g              0
product_length_cm             0
product_height_cm             0
product_width_cm              0

## برای حذف ردیف‌هایی که مقدار price در آن‌ها کمتر یا مساوی صفر است (price <= 0)، از فیلتر کردن با شرط استفاده می‌کنیم:
olist_order_items_dataset = olist_order_items_dataset[olist_order_items_dataset['price'] > 0]
## Cap freight_value at 99th percentile :  مقدار ستون  freight_value رو تا صدک ۹۹ محدود کن

percentile_99 = olist_order_items_dataset['freight_value'].quantile(0.99)

print(percentile_99)    ==>> 84.52  
 ##  مقدارهای بالاتر از صدک ۹۹ رو با خود صدک ۹۹ جایگزین (cap) :

olist_order_items_dataset['freight_value'] = olist_order_items_dataset['freight_value'].clip(upper=percentile_99)

## ردیف‌هایی از جدول پرداخت‌ها (olist_order_payments_dataset) که تکراری هستن رو حذف کنیم.
olist_order_payments_dataset.info()
 0   order_id              103886 
 1   payment_sequential    103886 
 2   payment_type          103886 
 3   payment_installments  103886 
 4   payment_value         103886 

 



olist_order_payments_dataset = olist_order_payments_dataset.drop_duplicates(subset=['order_id', 'payment_type', 'payment_value'])

olist_order_payments_dataset.info()
 0   order_id              103271 
 1   payment_sequential    103271 
 2   payment_type          103271 
 3   payment_installments  103271 
 4   payment_value         103271 

 ## اصلاح ساختار داده‌ها و نرمال‌سازی:
--تبدیل نام ستون‌ها به snake_case در همه فایل‌ها:
order_items.columns = order_items.columns.str.lower().str.strip().str.replace(" ", "_")

##  نرمال‌سازی دسته‌بندی‌ها:
olist_products_dataset['product_category_name'] = olist_products_dataset['product_category_name'].fillna("unknown")

## ذخیره داده‌های پاک‌سازی‌شده یک پوشه جدید: 
import os
os.listdir("cleaned_data")

olist_customers_dataset.to_csv('cleaned_data/olist_customers_dataset_cleaned.csv', index=False)
.
.
.


olist_customers_dataset table:
customer_id pk

olist_orders_dataset table:
order_id pk
fk:
costomer_id => olist_customers_dataset

olist_order_items_dataset table:
order_items_id pk
fk:
order_id => olist_orders_dataset
product_id => olist_products_dataset
seller_id => olist_sellers_dataset

olist_order_payments_dataset table:
fk:
order_id =>olist_orders_dataset

olist_order_reviews_dataset table:
review_id pk
fk:
order_id => olist_orders_dataset

olist_products_dataset table:
product_id pk

olist_sellers_dataset table:
seller_id pk
















