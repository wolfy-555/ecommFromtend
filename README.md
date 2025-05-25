## 📌 SQL Query: Customers in Cities with Above-Average Customer Counts

This query returns a list of countries and cities that have a **number of customers greater than the average** number of customers per city.

```sql
SELECT country_name, city_name, COUNT(customer.id) AS number_of_customer
FROM 
    country 
    JOIN city ON country.id = city.country_id
    JOIN customer ON city.id = customer.city_id
GROUP BY country_name, city_name
HAVING 
    COUNT(customer.id) > (
        SELECT AVG(customer_count)
        FROM (
            SELECT COUNT(customer.id) AS customer_count 
            FROM customer  
            GROUP BY city_id
        ) AS avg_city_customers
    )
ORDER BY country.country_name ASC;
```
## 📌 2
```sql

SELECT 
CASE
when red=green and green=blue then 'good'
when red=green OR red=blue or green=blue then 'bad'
else 'worse'
END AS TYPE_OF_COLLECTION
FROM
COLLECTION;

```
## 📌 3
```sql
SELECT 
CASE
when red=green and green=blue then 'good'
when red=green OR red=blue or green=blue then 'bad'
else 'worse'
END AS TYPE_OF_COLLECTION
FROM
COLLECTION;

```
## 📌 4
```sql
SELECT 
    a.iban AS IBAN,
    MIN(t.amount) AS min_transaction,
    MAX(t.amount) AS max_transaction,
    AVG(t.amount) AS avg_transaction,
    COUNT(*) AS total_transactions
FROM 
    accounts a
JOIN 
    transactions t ON a.id = t.account_id
WHERE 
    t.dt BETWEEN '2022-09-01' AND '2022-09-30'
GROUP BY 
    a.iban
ORDER BY 
    a.iban ASC;

```
## 📌 5
```sql
SELECT DISTINCT 
    p.NAME AS professor_name,
    c.NAME AS course_name
FROM 
    PROFESSOR p
JOIN 
    SCHEDULE s ON p.ID = s.PROFESSOR_ID
JOIN 
    COURSE c ON s.COURSE_ID = c.ID;
```
## 📌 6
```cs
using System;

namespace HelloWorld
{
    public abstract class Employee
    {
        public string department;
        public string name;
        public string location;
        public bool onVacation = false;

        public Employee(string department, string name, string location)
        {
            this.department = department;
            this.name = name;
            this.location = location;
        }

        public string getName()
        {
            return name;
        }

        public string getDepartment()
        {
            return department;
        }

        public string getLocation()
        {
            return location;
        }

        public bool getStatus()
        {
            return onVacation;
        }

        public void switchStatus()
        {
            onVacation = !onVacation;
        }
    }

    public class FinanceEmployee : Employee
    {
        public FinanceEmployee(string name, string location) : base("Finance", name, location) { }
    }

    public class MarketingEmployee : Employee
    {
        public MarketingEmployee(string name, string location) : base("Marketing", name, location) { }
    }
}

    
```

