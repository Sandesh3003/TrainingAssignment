Query:
```sql
select 
	oi.ORDER_ID,
	oi.ORDER_ITEM_SEQ_ID,
	oi2.ID_VALUE SHOPIFY_ORDER_ID,
	gi.ID_VALUE SHOPIFY_PRODUCT_ID
from order_item oi
join order_identification oi2
on oi.ORDER_ID = oi2.ORDER_ID and ORDER_IDENTIFICATION_TYPE_ID  ="SHOPIFY_ORD_ID"
join good_identification gi 
on oi.PRODUCT_ID = gi.PRODUCT_ID and gi.GOOD_IDENTIFICATION_TYPE_ID = "SHOPIFY_PROD_ID"
join order_status os 
on oi.ORDER_ID = os.ORDER_ID and oi.ORDER_ITEM_SEQ_ID = os.ORDER_ITEM_SEQ_ID and os.STATUS_ID = "ITEM_COMPLETED"
where  os.STATUS_DATETIME >="2023-07-01 00:00:00.000" and os.STATUS_DATETIME <= "2023-07-31 23:59:59.999";
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/9af82ba9-79b3-41f2-a718-98d9dcd34767)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/594cca9a-1299-4847-9093-d6db4aeb1fb0)
