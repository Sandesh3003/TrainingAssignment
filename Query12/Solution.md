12. Get all the appeasements in July month.<br>
a. How do we differentiate between returns and appeasements?<br>
b. Get all the below fields <br>
 i.    RETURN_ID<br>
 ii.   ENTRY_DATE <br>
 iii.  RETURN_ADJUSTMENT_TYPE_ID<br>
 iv.   AMOUNT<br>
 v.    COMMENTS <br>
 vi.   ORDER_ID<br>
 vii.  ORDER_DATE <br>
 viii. RETURN_DATE<br>
 ix.   PRODUCT_STORE_ID<br>

Query:
```sql
select 
	rh.RETURN_ID,
	rh.ENTRY_DATE,
	ra.RETURN_ADJUSTMENT_TYPE_ID,
	ra.AMOUNT,
	ra.COMMENTS,
	oh.ORDER_ID,
	oh.ORDER_DATE,
	rh.RETURN_DATE,
	oh.PRODUCT_STORE_ID 
from return_header rh 
join return_adjustment ra 
on rh.RETURN_ID = ra.RETURN_ID and ra.RETURN_ADJUSTMENT_TYPE_ID = 'APPEASEMENT'
join order_header oh 
on ra.ORDER_ID = oh.ORDER_ID 
where  rh.RETURN_DATE  >="2023-07-01 00:00:00.000" and rh.RETURN_DATE <= "2023-07-31 23:59:59.999";
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/f9109714-3c4a-4e77-acf8-6ee56b96681b)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/4199fca2-f25f-47cf-8345-52f40f92829d)
