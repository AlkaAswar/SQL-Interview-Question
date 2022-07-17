# SQL-Interview-Question
date	         customerid	 product_quantity    	price_per_item	      region	       transaction_id
09-10-2021	     CC1	         3	                   33	                 E	               1                
09-10-2021	     CC1	         4	                   22	                 A	               2
26-12-2020	     CC1	         2	                   111                	F	               3
27-12-2020	     CC2	         1	                    22	                G	               4
28-12-2020	     CC2	         4	                   11000	              G	               5
29-12-2020	     CC3	         2	                    33	                S	               6
30-12-2020	     CC3	         1	                    22	                S	               7
09-10-2021	     CC4	         3	                   11000	              E	               8
10-10-2021	     CC4	         4	                    33	                R	               9

Solve both in Python and SQL :

Question 1)
 
6 columns : date, customerid, product_quantity, sales, region, transaction_id. Which customer id bought maximum products? Tablename is questions.
(hint : get sales by multiplying product_quantity and price_per_item fields) 

SQL : select customerid,MAX(product_quantity)
           from question
           group by customerid;

Python : question['price_per_item fields']=question['sales']*question['product_quantity']
              question.groupby('customerid')[['price_per_item fields']].agg['max']

Question 2)

Get sales during Christmas period (21 dec 2020 - 27 dec 2020) by region.

SQL :select sales,date,region
from question
where ((date between 21 dec 2020 and  27 dec 2020))
group by region;

Python : question['Christmas_period'] = question["date"].between( 27 dec 2020,21 dec 2020 inclusive = False)  
 question.groupby('region')[[' Christmas_period'],['sales']]

Question 3)

Get count of transactions by region where customers had greater than 10000 $ sales and less than 10000 $ sales. (hint: create 2 columns for getting count of transaction ids - one where customers had greater than 10000 $ sales and another where customers had less than 10000 $ sales)

SQL : select customerid,count(transaction_id), region
from questions
group by region
having  sales>10000$ AND sales<10000$;

Python : question['transaction']=question['transaction_id'].value_counts()
question['condition']=(question['sales']>10000$ question['sales']<10000$)
question.groupby('region')[[' transaction'],['condition']]
