   price = (SELECT MAX(price) FROM pizzas);
```

| name         | pizza_id      | pizza_name   | pizza_size | price |
|--------------|---------------|--------------|------------|-------|
| name         | pizza_id      | pizza_size | price |
|--------------|---------------|------------|-------|
| The Greek Pizza | the_greek_xxl | XXL          | 35.95      |

## Q4: Identify the Most Common Pizza Size Ordered

```sql
SELECT 
    size, COUNT(size) AS orders
FROM
    order_details
    JOIN pizzas ON order_details.pizza_id = pizzas.pizza_id
GROUP BY size
ORDER BY orders DESC
LIMIT 1;
```

| size | orders |
|------|--------|
| L    | 18526  |

## Q5: List the Top 5 Most Ordered Pizza Types Along with Their Quantities

```sql
SELECT 
    pizza_types.name, COUNT(order_details.pizza_id) AS orders
