5. In New York, which product has the highest sales?

```sql
select
	oi.PRODUCT_ID,
	sum(oi.QUANTITY * oi.UNIT_PRICE) TOTAL_SALES from order_item oi
join order_contact_mech ocm
on oi.ORDER_ID = ocm.ORDER_ID and ocm.CONTACT_MECH_PURPOSE_TYPE_ID = 'BILLING_LOCATION'
join postal_address pa
on ocm.CONTACT_MECH_ID = pa.CONTACT_MECH_ID and pa.CITY = 'NEW YORK'
group by oi.product_id
order by TOTAL_SALES desc limit 1;
```
Ouput:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/00ee42e0-e74b-4535-a159-1e380511860c)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/4bb9ec23-05cf-4670-9a46-67275be27237)
