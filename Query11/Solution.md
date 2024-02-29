11. Fetch all the customers created in June 2023.

Query:
```sql
select p.PARTY_ID from party p 
join party_role pr 
on p.PARTY_ID = pr.PARTY_ID and pr.ROLE_TYPE_ID = 'CUSTOMER'
where  (p.CREATED_DATE  >="2023-06-01 00:00:00.000" and p.CREATED_DATE  < "2023-07-01 00:00:00.000");
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/42f4ddb8-0f94-41d2-9be5-608ba85121c6)


Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/ead25390-10b6-4ee9-9506-86c06d1927dd)

