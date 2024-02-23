3. In the period following the New Year, what is the number of orders shipped from stores in the first 25 days?

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
where ss.STATUS_DATE > "2023-12-31" and ss.STATUS_DATE <= "2024-01-25"; 
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/d1715e79-0174-4087-a10e-88795e32e36e)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/d1ed6be5-0bb0-4a58-b35b-d08d4b4b7028)
