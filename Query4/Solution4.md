4. What is the total number of orders originating from New York?
   
Query:
```sql
select count(ocm.ORDER_ID) as Order_Count from order_contact_mech ocm
join postal_address pa
on ocm.CONTACT_MECH_ID = pa.CONTACT_MECH_ID and ocm.CONTACT_MECH_PURPOSE_TYPE_ID = 'BILLING_LOCATION' and pa.CITY = 'NEW YORK';
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/e0fb80ac-1fce-4643-9dfd-b2993e022053)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/6e135a42-be71-4ca4-a7f3-e9add3dcd4f2)
