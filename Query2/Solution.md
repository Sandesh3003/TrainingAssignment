2. Fetch the following columns for completed return items of SM_STORE for ecom return channel.<br>
	- RETURN_ID <br>
	- ORDER_ID<br>
	- PRODUCT_STORE_ID<br> 
	- STATUS_DATETIME<br>
	- ORDER_NAME <br>
	- FROM_PARTY_ID <br>
	- RETURN_DATE <br>
	- ENTRY_DATE<br>
	- RETURN_CHANNEL_ENUM_ID<br>

Query :
```sql
select 
	rh.RETURN_ID,
	ri.RETURN_ITEM_SEQ_ID,
	oh.ORDER_ID,
	oh.PRODUCT_STORE_ID,
	rs.STATUS_DATETIME,
	oh.ORDER_NAME,
	rh.FROM_PARTY_ID,
	rh.RETURN_DATE,
	rh.ENTRY_DATE,
	rh.RETURN_CHANNEL_ENUM_ID 
	from return_header rh 
	join return_item ri
	on rh.RETURN_ID = ri.RETURN_ID 
	join  order_header oh 
	on ri.ORDER_ID = oh.ORDER_ID and oh.PRODUCT_STORE_ID ="SM_STORE"
	join return_status rs 
	on ri.RETURN_ID = rs.RETURN_ID and ri.RETURN_ITEM_SEQ_ID = rs.RETURN_ITEM_SEQ_ID
	where rh.RETURN_CHANNEL_ENUM_ID = 'ECOM_RTN_CHANNEL' and rs.STATUS_ID ="RETURN_COMPLETED";
```
Output:
![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/02f6f015-23ad-42ee-b7dc-7bf49061b771)

Query Execution Plan:
![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/e9b19464-7ed6-4af2-acab-8a2566c8a2d7)
