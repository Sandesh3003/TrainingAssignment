11. Fetch all the customers created in June 2023.

Query:
```sql
elect p.PARTY_ID from party p 
join party_role pr 
on p.PARTY_ID = pr.PARTY_ID and pr.ROLE_TYPE_ID = 'CUSTOMER'
where  (p.CREATED_DATE  >="2023-06-01 00:00:00.000" and p.CREATED_DATE  <= "2023-06-30 23:59:59.999") and 
p.STATUS_ID = "PARTY_ENABLED";
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/d0f8240b-6c14-458b-9b8a-a3b72407118a)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/6d7405a7-3b21-4240-9da2-9d84a0ec1b98)
