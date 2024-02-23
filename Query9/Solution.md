9. Find all the orders whose two or more items are canceled but the orders are still in the approved status.

Query:

```sql
select 
	oh.ORDER_ID 
from order_header oh 
join order_item oi
on oi.ORDER_ID = oh.ORDER_ID and oh.STATUS_ID = "ORDER_APPROVED" and oi.STATUS_ID="ITEM_CANCELLED"
group by oh.ORDER_ID
having count(oh.ORDER_ID)>=2;
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/a39735d2-3c27-4b41-8764-01c6a224eebf)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/c5401d52-d790-444b-b255-3f70d5a25850)
