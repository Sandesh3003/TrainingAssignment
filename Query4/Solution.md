Query: 
```sql
select 
	oh.ORDER_ID,
	oh.GRAND_TOTAL TOTAL_AMOUNT,
	pmt.DESCRIPTION PAYMENT_METHOD,
	oi.ID_VALUE SHOPIFY_ORDER_NAME
from order_header oh
join order_payment_preference opp 
on oh.ORDER_ID = opp.ORDER_ID 
join payment_method_type pmt
on opp.PAYMENT_METHOD_TYPE_ID = pmt.PAYMENT_METHOD_TYPE_ID 
join order_identification oi
on oh.ORDER_ID = oi.ORDER_ID and oi.ORDER_IDENTIFICATION_TYPE_ID = "SHOPIFY_ORD_NAME"
where oh.STATUS_ID = "ORDER_CREATED";

```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/b947c273-be55-4dc8-aada-a3686ac0bad2)

Query Execution Plan:
![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/3ef6021a-eb3d-4b2f-b306-ddda6af79893)

