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
where  rh.RETURN_DATE  >="2023-07-01 00:00:00.000" and rh.RETURN_DATE < "2023-08-01 00:00:00.000";
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/68ab78cd-ce74-4ca2-acf8-7dcc9d49b0a0)


Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/af8e3e98-0c11-4248-b4e3-05e239e1831f)

