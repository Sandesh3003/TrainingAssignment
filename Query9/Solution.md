9. Find all the orders whose two or more items are canceled but the orders are still in the approved status.

Query:

```sql
select 
	oh.ORDER_ID from order_item oi 
join order_status os 
on oi.ORDER_ID = os.ORDER_ID and oi.ORDER_ITEM_SEQ_ID = os.ORDER_ITEM_SEQ_ID and os.STATUS_ID="ITEM_CANCELLED"
join order_header oh
on oi.ORDER_ID = oh.ORDER_ID and oh.STATUS_ID = "ORDER_APPROVED"
group by oh.ORDER_ID 
having count(os.ORDER_ID)>=2;
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/a39735d2-3c27-4b41-8764-01c6a224eebf)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/0d6447a3-a43b-458c-bd18-c16c0eaab3b2)
