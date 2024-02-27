7. On a city-wise basis, what is the analysis of returns?

Query:
```sql
select pa.CITY, count(distinct rcm.RETURN_ID) RETURNS from return_contact_mech rcm
join postal_address pa
on rcm.CONTACT_MECH_ID = pa.CONTACT_MECH_ID
group by pa.CITY;
```
Output:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/79729cfe-2b4d-484b-9871-8c95730a07c9)

Query Execution Plan:

![image](https://github.com/Sandesh3003/TrainingAssignment/assets/77960808/2f329e15-e405-4025-8419-31efe9821b67)
