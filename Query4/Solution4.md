4. What is the total number of orders originating from New York?

Approach: Fulfilling facility

Query:
```sql
select count(distinct s.PRIMARY_ORDER_ID) ORDERS from shipment s 
join facility_contact_mech_purpose fcmp  
on s.ORIGIN_FACILITY_ID = fcmp.FACILITY_ID and fcmp.CONTACT_MECH_PURPOSE_TYPE_ID='SHIP_ORIG_LOCATION'
join postal_address pa 
on fcmp.CONTACT_MECH_ID = pa.CONTACT_MECH_ID and pa.CITY = 'New York';
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/efefc4c0-f5e5-4fa5-bb9f-74046767b243)


Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/141e2d6a-0a21-4b73-a00e-ec63928b8723)

Approach: Customer
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
