2. Leading up to the New Year, what is the count of orders shipped from stores in the 25 days preceding the New Year?

Query:
```sql
select count(distinct os.ORDER_ID) Order_Count from order_shipment os 
join shipment s 
on os.SHIPMENT_ID = s.SHIPMENT_ID and os.ORDER_ID=s.PRIMARY_ORDER_ID and s.PRIMARY_SHIP_GROUP_SEQ_ID=os.SHIP_GROUP_SEQ_ID
join facility f 
on s.ORIGIN_FACILITY_ID = f.FACILITY_ID 
join facility_type ft 
on f.FACILITY_TYPE_ID = ft.FACILITY_TYPE_ID and ft.PARENT_TYPE_ID = 'PHYSICAL_STORE'
join shipment_status ss 
on s.SHIPMENT_ID = ss.SHIPMENT_ID and ss.STATUS_ID = "SHIPMENT_SHIPPED"
where ss.STATUS_DATE > "2023-12-06" and ss.STATUS_DATE <= "2023-12-31";
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/cd656db8-d075-464f-a83f-ab90d39a4687)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/06b93947-1cda-455e-aa63-fa38266fc03d)
