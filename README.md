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
