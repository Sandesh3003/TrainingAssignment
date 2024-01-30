8. How many orders with a single return were recorded in the last month?

Query:
```sql
SELECT COUNT(*)
FROM return_item ri
JOIN (
   SELECT ri2.ORDER_ID
   FROM return_item ri2
   GROUP BY ri2.ORDER_ID
   HAVING COUNT(ri2.ORDER_ID) = 1
) AS unique_orders ON unique_orders.ORDER_ID = ri.ORDER_ID
JOIN return_header rh ON rh.RETURN_ID = ri.RETURN_ID AND rh.ENTRY_DATE > DATE_SUB(CURDATE(), INTERVAL 1 MONTH);
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/c8410bda-231b-4397-9a7d-fa04ac23be3e)

Query Execution Plan:

![Q3 8](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/45e9feef-833d-4d11-a2d8-372cc2be602c)



