1. Fetch the following columns for completed order items for sales orders of SM_STORE product store and that are physical items.<br>
	i.    ORDER_ID<br>
	ii.   ORDER_ITEM_SEQ_ID<br>
 	iii.  PRODUCT_ID<br>
	iv.   PRODUCT_TYPE_ID<br>
	v.    IS_PHYSICAL<br>
 	vi.   IS_DIGITAL<br>
	vii.  SALES_CHANNEL_ENUM_ID<br>
	viii. ORDER_DATE<br>
	ix.   ENTRY_DATE<br>
	x.    STATUS_ID<br>
	xi.   STATUS_DATETIME<br>
	xii.  ORDER_TYPE_ID<br>
	xiii. PRODUCT_STORE_ID <br>


Query:
```sql
select 
	oh.ORDER_ID,
	oi.ORDER_ITEM_SEQ_ID,
	p.PRODUCT_ID,
	p.PRODUCT_TYPE_ID,
	pt.IS_PHYSICAL,
	pt.IS_DIGITAL,
	oh.SALES_CHANNEL_ENUM_ID, 
	oh.ORDER_DATE,
	oh.ENTRY_DATE,
	oi.STATUS_ID,
	os.STATUS_DATETIME, 
	oh.ORDER_TYPE_ID,
	oh.PRODUCT_STORE_ID 
from order_header oh
join order_item oi
on oh.ORDER_ID = oi.ORDER_ID
join order_status os
on oi.ORDER_ID = os.ORDER_ID and oi.ORDER_ITEM_SEQ_ID = os.ORDER_ITEM_SEQ_ID
join product p
on oi.PRODUCT_ID = p.PRODUCT_ID
join product_type pt 
on p.PRODUCT_TYPE_ID = pt.PRODUCT_TYPE_ID
where oh.ORDER_TYPE_ID = "SALES_ORDER" and 
oh.PRODUCT_STORE_ID = "SM_STORE" and pt.IS_PHYSICAL = "Y" and os.STATUS_ID ="ITEM_COMPLETED";
```
Output:
![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/3b0b4300-1d52-482a-8351-151d13baebf3)


Query Execution Plan:
![q1](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/aacb95d5-77ac-4d10-b6bb-517ebf2d543b)

