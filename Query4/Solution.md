4. Fetch the following columns for created orders. These should be sales orders.
- ORDER_ID
- TOTAL_AMOUNT
- PAYMENT_METHOD
- SHOPIFY_ORDER_NAME
<br>
NOTE: 
<br>The total amount represents the total amount of the order.
<br>The payment method is the method by which payment was made, like Cash, mastercard, visa, paypal, etc.

Query: 
```sql
select 
	oh.ORDER_ID,
	oh.GRAND_TOTAL TOTAL_AMOUNT,
	pmt.DESCRIPTION PAYMENT_METHOD,
	oi.ID_VALUE SHOPIFY_ORDER_NAME
from order_header oh
join order_payment_preference opp 
on oh.ORDER_ID = opp.ORDER_ID and oh.ORDER_TYPE_ID="SALES_ORDER" and oh.STATUS_ID="ORDER_CREATED"
join payment_method_type pmt
on opp.PAYMENT_METHOD_TYPE_ID = pmt.PAYMENT_METHOD_TYPE_ID 
left join order_identification oi
on oh.ORDER_ID = oi.ORDER_ID and oi.ORDER_IDENTIFICATION_TYPE_ID = "SHOPIFY_ORD_NAME" and (oi.THRU_DATE=null or oi.THRU_DATE>curdate());

```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/9882450a-958a-4537-a945-f60d11a9ff12)

Query Execution Plan:
![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/aa27d8ce-efe6-4c3d-8dea-c9ff8e70dc3e)

