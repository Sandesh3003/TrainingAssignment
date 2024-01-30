1. How many single-item orders were fulfilled from warehouses in the last month?
```sql
select count(*) Single_Item_Orders from
(
	select
		oi.ORDER_ID
	from order_item oi
	join order_item_ship_group_assoc oisga
	on oi.ORDER_ID = oisga.ORDER_ID and oi.ORDER_ITEM_SEQ_ID = oisga.ORDER_ITEM_SEQ_ID
	join order_item_ship_group oisg
	on oisga.ORDER_ID = oisg.ORDER_ID and oisga.SHIP_GROUP_SEQ_ID = oisg.SHIP_GROUP_SEQ_ID
	join facility f
	on oisg.FACILITY_ID = f.FACILITY_ID and f.FACILITY_TYPE_ID = "WAREHOUSE"
	join shipment s
	on oisg.ORDER_ID = s.PRIMARY_ORDER_ID and oisg.SHIP_GROUP_SEQ_ID = s.PRIMARY_SHIP_GROUP_SEQ_ID
	join shipment_status ss
	on s.SHIPMENT_ID = ss.SHIPMENT_ID and s.STATUS_ID = ss.STATUS_ID
	where ss.STATUS_DATE > date_sub(curdate() , interval 1 month)
	group by oi.ORDER_ID
	having count(oi.ORDER_ID)=1
) as Orders;
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/7362e6cd-8bc6-47d2-8a89-e542d4052d35)

Query Execution Cost:

![Q3 1](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/8b1c58be-cce0-4852-af56-a2786dffee75)
