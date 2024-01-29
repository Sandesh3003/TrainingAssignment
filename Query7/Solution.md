Query:

```sql
select 
	oi.ORDER_ID,
  oi.ORDER_ITEM_SEQ_ID
from order_item oi 
join order_status os 
on oi.ORDER_ID = os.ORDER_ID and oi.ORDER_ITEM_SEQ_ID = os.ORDER_ITEM_SEQ_ID and os.STATUS_ID="ITEM_CREATED"
join product p 
on oi.PRODUCT_ID = p.PRODUCT_ID
join product_type pt 
on p.PRODUCT_TYPE_ID = pt.PRODUCT_TYPE_ID and pt.IS_PHYSICAL = "Y"
where  os.STATUS_DATETIME >="2023-09-01 00:00:00.000" and os.STATUS_DATETIME <= "2023-09-30 23:59:59.999";
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/c44d2662-0ccd-4c27-85f9-3b4b3e50a982)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/c76e44e9-efa7-4ada-a4ed-9c7cc2851b67)
