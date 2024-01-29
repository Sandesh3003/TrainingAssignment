Query:

```sql
select 
	oh.ORDER_ID, 
	ocm.CONTACT_MECH_ID, 
	os.STATUS_DATETIME  
from order_header oh 
join order_contact_mech ocm 
on oh.ORDER_ID = ocm.ORDER_ID and ocm.CONTACT_MECH_PURPOSE_TYPE_ID = "SHIPPING_LOCATION" 
join order_status os 
on oh.ORDER_ID = os.ORDER_ID and os.STATUS_ID = "ORDER_COMPLETED"
where  os.STATUS_DATETIME >="2023-10-01 00:00:00.000" and os.STATUS_DATETIME <= "2023-10-31 23:59:59.999";
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/2d68f03e-4e1e-4f6d-806e-9abacede1217)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/dc38b877-2153-4c30-b95f-03377a50ad61)


