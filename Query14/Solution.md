14. Fetch the inventory variances of the products where the reason is ‘VAR_LOST’ or VAR_DAMAGED.

Query:
```sql
select
	ii.PRODUCT_ID,
	iiv.AVAILABLE_TO_PROMISE_VAR,
	iiv.QUANTITY_ON_HAND_VAR,
	iiv.VARIANCE_REASON_ID 
from inventory_item ii 
join inventory_item_variance iiv 
on ii.INVENTORY_ITEM_ID = iiv.INVENTORY_ITEM_ID where iiv.VARIANCE_REASON_ID = "VAR_LOST" or iiv.VARIANCE_REASON_ID = "VAR_DAMAGED";
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/5b151930-05fd-4b4e-b667-c940135f12e6)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/09b5d692-4997-4473-b62b-c2118bb7befa)
