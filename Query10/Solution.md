10. Fetch all the order items that are in the created status and the order type should be a sales order
a. ORDER_ID<br>
b. PRODUCT_TYPE_ID<br>
c. ORDER_LINE_ID<br>
d. EXTERNAL_ID<br>
e. SALES_CHANNEL<br>
f. QUANTITY<br>
g. ITEM_STATUS<br> 
h. PRODUCT_ID<br>
i. BILL_CITY<br>
j. BILL_COUNTRY<br>
k. BILL_POSTALCODE<br>
l. BILL_ADDRESS1<br>
m. BILL_ADDRESS2<br>
n. SHIP_CITY<br>
o. SHIP_COUNTRY<br>
p. SHIP_POSTALCODE<br>
q. SHIP_ADDRESS1<br>
r. SHIP_ADDRESS2<br>

Query:
```sql
select 
	oh.ORDER_ID,
	p.PRODUCT_TYPE_ID,
	oi.ORDER_ITEM_SEQ_ID,
	oi.EXTERNAL_ID,
	oh.SALES_CHANNEL_ENUM_ID,
	oi.QUANTITY,
	oi.STATUS_ID,
	p.PRODUCT_ID,
	pa.CITY BILL_CITY,
	pa.COUNTRY_GEO_ID BILL_COUNTRY,
	pa.POSTAL_CODE BILL_POSTALCODE,
	pa.ADDRESS1 BILL_ADDRESS1,
	pa.ADDRESS2 BILL_ADDRESS2,
	pa2.CITY SHIP_CITY,
	pa2.COUNTRY_GEO_ID SHIP_COUNTRY,
	pa2.POSTAL_CODE SHIP_POSTALCODE,
	pa2.ADDRESS1 SHIP_ADDRESS1,
	pa2.ADDRESS2 SHIP_ADDRESS2
from order_header oh
join order_item oi 
on oh.ORDER_ID = oi.ORDER_ID and oh.ORDER_TYPE_ID = "SALES_ORDER"
join product p 
on p.PRODUCT_ID = oi.PRODUCT_ID 
join order_contact_mech ocm 
on oh.ORDER_ID = ocm.ORDER_ID and (CONTACT_MECH_PURPOSE_TYPE_ID="BILLING_LOCATION" or ocm.CONTACT_MECH_PURPOSE_TYPE_ID="SHIPPING_LOCATION")
left join postal_address pa 
on pa.CONTACT_MECH_ID = ocm.CONTACT_MECH_ID and ocm.CONTACT_MECH_PURPOSE_TYPE_ID = "BILLING_LOCATION"
left join postal_address pa2 
on pa2.CONTACT_MECH_ID = ocm.CONTACT_MECH_ID and ocm.CONTACT_MECH_PURPOSE_TYPE_ID = "SHIPPING_LOCATION"
where oi.STATUS_ID = "ITEM_CREATED";
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/99d0f48e-e92a-4469-b995-f7b93d2891c7)

Query Execution Plan:

![q10](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/92b88e62-6910-4333-a436-60c374653121)
