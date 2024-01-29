8. Find all the orders whose two or more items are completed but the orders are still in the approved status.

Query:

```sql
select 
	oh.ORDER_ID 
from order_item oi 
join order_status os 
on oi.ORDER_ID = os.ORDER_ID and oi.ORDER_ITEM_SEQ_ID = os.ORDER_ITEM_SEQ_ID and os.STATUS_ID="ITEM_COMPLETED"
join order_header oh
on oi.ORDER_ID = oh.ORDER_ID and oh.STATUS_ID = "ORDER_APPROVED"
group by oh.ORDER_ID
having count(os.ORDER_ID)>=2;
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/5d15418e-b501-4943-9149-08e010bf4fe6)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/a8f19990-c9e3-4174-a72f-ef5ccc090ac1)
