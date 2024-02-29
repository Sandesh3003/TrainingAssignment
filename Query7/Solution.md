7. Fetch all the physical items ordered in the month of September 2023.

Query:

```sql
select 
	oi.ORDER_ID,
	oi.ORDER_ITEM_SEQ_ID
from order_item oi 
join product p 
on oi.PRODUCT_ID = p.PRODUCT_ID
join product_type pt 
on p.PRODUCT_TYPE_ID = pt.PRODUCT_TYPE_ID and pt.IS_PHYSICAL = "Y"
where  oi.CREATED_STAMP >="2023-09-01 00:00:00.000" and oi.CREATED_STAMP < "2023-10-01 00:00:00.000";
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/8784961c-e2c6-411f-81bb-34f2910a2227)


Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/045de54a-63e0-41ac-b503-7b96ed7c5dd3)

