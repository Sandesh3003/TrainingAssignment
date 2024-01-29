Query:

```sql
select 
	oi.ORDER_ID, 
	oi.ORDER_ITEM_SEQ_ID  from order_item oi 
join order_item_ship_group_assoc oisga 
on oi.ORDER_ID = oisga.ORDER_ID and oi.ORDER_ITEM_SEQ_ID = oisga.ORDER_ITEM_SEQ_ID 
join order_item_ship_group oisg 
on oisga.ORDER_ID =oisg.ORDER_ID and oisga.SHIP_GROUP_SEQ_ID = oisg.SHIP_GROUP_SEQ_ID 
join facility f 
on oisg.FACILITY_ID  = f.FACILITY_ID and f.FACILITY_TYPE_ID = "WAREHOUSE"
join order_status os 
on oi.ORDER_ID = os.ORDER_ID and oi.ORDER_ITEM_SEQ_ID = os.ORDER_ITEM_SEQ_ID and os.STATUS_ID="ITEM_COMPLETED"
join product p 
on oi.PRODUCT_ID = p.PRODUCT_ID
join product_type pt 
on p.PRODUCT_TYPE_ID = pt.PRODUCT_TYPE_ID and pt.IS_PHYSICAL = "Y"
where  os.STATUS_DATETIME >="2023-09-01 00:00:00.000" and os.STATUS_DATETIME <= "2023-09-30 23:59:59.999";
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/c4ddec30-976f-4b2a-b0e8-0e47960f2fbd)

Query Execution Plan:

![q6](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/e6ddc546-5284-4c4a-af48-6f9a06ac86f0)
