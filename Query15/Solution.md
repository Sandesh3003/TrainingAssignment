15. Find all the orders that have more than one return.

Query:
```sql
select ri.ORDER_ID from return_item ri 
group by ri.ORDER_ID 
having count(ri.ORDER_ID)>1;
```

Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/5a9b8665-3d0f-48f5-88df-c7971fced6ca)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/4efe6aa3-ab5b-4472-b33c-b93aa8c7fce6)
