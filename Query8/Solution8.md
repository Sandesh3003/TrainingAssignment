8. How many orders with a single return were recorded in the last month?

Query:
```sql
SELECT COUNT(*) AS total_single_return_items
FROM (
    SELECT ri.ORDER_ID
    FROM return_item ri
    JOIN return_header rh ON rh.RETURN_ID = ri.RETURN_ID
    WHERE rh.ENTRY_DATE > DATE_SUB(CURDATE(), INTERVAL 1 MONTH)
    GROUP BY ri.ORDER_ID
    HAVING COUNT(ri.ORDER_ID) = 1
) AS single_return_items;
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/fa72c8fe-dbd8-432e-8697-ac95db65c331)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/e6c57233-8712-4c21-aecf-e12c570c0be9)



