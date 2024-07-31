# Pizzahut__Analysis_Dashboard
     Basics Queries
Retrieve the total number of orders place
Calculate the total revenue generated from pizza sales.
dentify the highest-priced pizza.
Identify the most common pizza size ordered
result the most pizaa order is large pizzaa 
     Queires with Answers 
 select count(order_id) as total_orders from orders;
-- result 21350
select round(sum(order_details.quantity * pizzas.price),1) as total_revenue
from order_details join pizzas
on order_details.pizza_id = pizzas.pizza_id;
-- result 817860
 select name, price from pizza_types join pizzas using(pizza_type_id) order by price desc limit 1;
-- result the Greek pizza 35.95  
select pizzas.size, count(order_details.order_details_id) as order_count
from pizzas join order_details
on pizzas.pizza_id = order_details.pizza_id
group by pizzas.size order by order_count desc limit 5;
-- result the most pizaa order is large pizzaa 18526
select pizza_types.name, sum(order_details.quantity) as order_quantity
from pizza_types join pizzas
on pizza_types.pizza_type_id = pizzas.pizza_type_id
join order_details
on order_details.pizza_id = pizzas.pizza_id
group by pizza_types.name order by order_quantity desc limit 5;
result the hawai pizza 20453
     intermiate Queries 
 # Intermediate:
<br>Join the necessary tables to find the total quantity of each pizza category ordered.
Determine the distribution of orders by hour of the day.
Join relevant tables to find the category-wise distribution of pizzas.
Group the orders by date and calculate the average number of pizzas ordered per day.
Determine the top 3 most ordered pizza types based on revenue.</br>
     Quries <br>
select pizza_types.category, sum(order_details.quantity) as quantity
from pizza_types join pizzas
on pizza_types.pizza_type_id = pizzas.pizza_type_id
join order_details
on order_details.pizza_id = pizzas.pizza_id
group by pizza_types.category 
order by quantity desc limit 5;</br>
<br>select hour(order_time), count(order_id) from orders
group by hour(order_time);
-- Join relevant tables to find the category-wise distribution of pizzas.
select category, count(name) from pizza_types
group by category;</br>
<br>select hour(order_time), count(order_id) from orders
group by hour(order_time);
select category, count(name) from pizza_types
group by category;</br>
<br>
SELECT 
    ROUND(AVG(quantity), 0) AS avg_quantiy FROM
    (SELECT 
        orders.order_date, SUM(order_details.quantity) AS quantity FROM
        orders JOIN order_details ON orders.order_id = order_details.order_id
    GROUP BY orders.order_date) AS order_quantity;</br>
    <br>
select pizza_types.name,
sum(order_details.quantity * pizzas.price) as revenue
from pizza_types
join pizzas
on pizza_types.pizza_type_id = pizzas.pizza_type_id
join order_details
on order_details.pizza_id = pizzas.pizza_id
group by pizza_types.name
order by revenue desc limit 5;</br>
