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
 

