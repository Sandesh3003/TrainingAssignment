5. In New York, which product has the highest sales?

```sql
select
	oi.PRODUCT_ID,
	sum(oi.QUANTITY) TOTAL_SALES from order_item oi
join order_contact_mech ocm
on oi.ORDER_ID = ocm.ORDER_ID and ocm.CONTACT_MECH_PURPOSE_TYPE_ID = 'BILLING_LOCATION'
join postal_address pa
on ocm.CONTACT_MECH_ID = pa.CONTACT_MECH_ID and pa.CITY = 'NEW YORK'
group by oi.product_id
order by TOTAL_SALES desc limit 1;
```
Ouput:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/7209efd6-98ba-4b43-9b46-21df6e68f6bc)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/909f3074-b5e3-45ca-a15a-131bf42f2329)

