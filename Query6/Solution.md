6. Fetch all the physical items completed from Warehouse in September of 2023.

Query:

```sql
select 
	oi.ORDER_ID, 
	oi.ORDER_ITEM_SEQ_ID  from order_item oi 
join order_item_ship_group oisg 
on oi.ORDER_ID = oisg.ORDER_ID and oi.SHIP_GROUP_SEQ_ID = oisg.SHIP_GROUP_SEQ_ID 
join facility f 
on oisg.FACILITY_ID  = f.FACILITY_ID and f.FACILITY_TYPE_ID = "WAREHOUSE"
join order_status os 
on oi.ORDER_ID = os.ORDER_ID and oi.ORDER_ITEM_SEQ_ID = os.ORDER_ITEM_SEQ_ID and os.STATUS_ID="ITEM_COMPLETED"
join product p 
on oi.PRODUCT_ID = p.PRODUCT_ID
join product_type pt 
on p.PRODUCT_TYPE_ID = pt.PRODUCT_TYPE_ID and pt.IS_PHYSICAL = "Y"
where  os.STATUS_DATETIME >="2023-09-01 00:00:00.000" and os.STATUS_DATETIME <"2023-10-01 00:00:00.000";
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/b55284b7-0930-4d5b-a5b6-135b73e4e24a)


Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/d364182d-90f6-4b5b-a27d-62c0c5b63ca9)

