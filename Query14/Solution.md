14. Fetch the inventory variances of the products where the reason is ‘VAR_LOST’ or VAR_DAMAGED.

Query:
```sql
select
	P.PRODUCT_ID,
	iiv.AVAILABLE_TO_PROMISE_VAR,
	iiv.QUANTITY_ON_HAND_VAR,
	iiv.VARIANCE_REASON_ID 
from product p 
join inventory_item ii 
on p.PRODUCT_ID = ii.PRODUCT_ID
join inventory_item_variance iiv 
on ii.INVENTORY_ITEM_ID = iiv.INVENTORY_ITEM_ID and (iiv.VARIANCE_REASON_ID = "VAR_LOST" or iiv.VARIANCE_REASON_ID = "VAR_DAMAGED");
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/5b151930-05fd-4b4e-b667-c940135f12e6)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/e87122b7-fdf2-4ebb-a7ff-d67c4cae7c94)
