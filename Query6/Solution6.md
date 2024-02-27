6. In the past month, which store has the highest number of one-day shipped orders?

Query:
```sql
select oh.PRODUCT_STORE_ID, count(distinct oh.ORDER_ID) as ORDERS_SHIPPED from order_header oh 
join shipment s
on s.PRIMARY_ORDER_ID = oh.ORDER_ID and s.SHIPMENT_METHOD_TYPE_ID="NEXT_DAY"
join shipment_status ss
on ss.SHIPMENT_ID = s.SHIPMENT_ID and s.STATUS_ID = "SHIPMENT_SHIPPED"
where ss.STATUS_DATE > date_sub(curdate(), interval 1 month)
group by oh.PRODUCT_STORE_ID
order by ORDERS_SHIPPED desc LIMIT 1;
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/adf21427-ba18-4eb4-ba45-eb6fffa136d6)

Query Execution Plan:

![SQL3q6](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/69ee01f7-bae7-4203-beda-816d1a1cd243)
