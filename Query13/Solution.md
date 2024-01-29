13. Fetch the following details for orders completed in August of 2023.<br>
 i.    PRODUCT_ID<br>
 ii.   PRODUCT_TYPE_ID<br>
 iii.  PRODUCT_STORE_ID <br>
 iv.   TOTAL_QUANTITY<br>
 v.    INTERNAL_NAME <br>
 vi.   FACILITY_ID<br>
 vii.  EXTERNAL_ID <br>
 viii. FACILITY_TYPE_ID<br> 
 ix.   ORDER_HISTORY_ID<br>
 x.    ORDER_ID<br>
 xi.   ORDER_ITEM_SEQ_ID<br>
 xii.  SHIP_GROUP_SEQ_ID<br>

Query:
```sql
select
	p.PRODUCT_ID,
	p.PRODUCT_TYPE_ID,
	oh.PRODUCT_STORE_ID,
	oi.QUANTITY as TOTAL_QUANTITY,
	p.INTERNAL_NAME,
	oisg.FACILITY_ID,
	oh.EXTERNAL_ID,
	f.FACILITY_TYPE_ID,
	oh2.ORDER_HISTORY_ID,
	oh.ORDER_ID,
	oi.ORDER_ITEM_SEQ_ID,
	oisg.SHIP_GROUP_SEQ_ID 
from order_header oh
join order_item oi
on oh.ORDER_ID = oi.ORDER_ID
join product p 
on oi.PRODUCT_ID = p.PRODUCT_ID 
join order_history oh2 
on oi.ORDER_ID = oh2.ORDER_ID and oi.ORDER_ITEM_SEQ_ID = oh2.ORDER_ITEM_SEQ_ID 
join order_item_ship_group_assoc oisga 
on oi.ORDER_ID = oisga.ORDER_ID and oi.ORDER_ITEM_SEQ_ID = oisga.ORDER_ITEM_SEQ_ID 
join order_item_ship_group oisg 
on oisga.ORDER_ID = oisg.ORDER_ID and oisga.SHIP_GROUP_SEQ_ID = oisg.SHIP_GROUP_SEQ_ID 
join facility f 
on oisg.FACILITY_ID = f.FACILITY_ID
join order_status os 
on oh.ORDER_ID = os.ORDER_ID and os.STATUS_ID = "ORDER_COMPLETED"
where  os.STATUS_DATETIME  >="2023-08-01 00:00:00.000" and os.STATUS_DATETIME <= "2023-08-31 23:59:59.999";
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/5ab48b02-11ef-4c44-8293-adfbc03db42b)

Query Execution Plan:

![q13](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/992a615c-2ca8-4720-8a39-d5c46ec09d28)
