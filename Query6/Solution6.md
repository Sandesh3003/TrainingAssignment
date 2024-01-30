6. In the past month, which store has the highest number of one-day shipped orders?

Query:
```sql
select oh.PRODUCT_STORE_ID, count(oh.ORDER_ID) as ORDERS_SHIPPED from order_header oh 
join product_store_shipment_meth pssm
on oh.PRODUCT_STORE_ID = pssm.PRODUCT_STORE_ID
join shipment_method_type smt
on smt.SHIPMENT_METHOD_TYPE_ID =pssm.SHIPMENT_METHOD_TYPE_ID and (smt.PARENT_TYPE_ID = 'NEXT_DAY' or smt.SHIPMENT_METHOD_TYPE_ID = 'SAME_DAY')
join order_shipment os
on os.ORDER_ID = oh.ORDER_ID
join shipment_status ss
on ss.SHIPMENT_ID = os.SHIPMENT_ID and ss.STATUS_ID = "SHIPMENT_SHIPPED"
where ss.STATUS_DATE > date_sub(curdate(), interval 1 month)
group by oh.PRODUCT_STORE_ID
order by ORDERS_SHIPPED desc limit 1;
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/75004055-5d3b-4d1d-809c-8d4524d695db)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/05514b19-7701-4318-8e50-2009556bde64)
