This dataset contain detailed information about pizza orders, including specifics about the pizza variants, quantities, pricing, dates, times, and categorization details.

pizza_id: A unique identifier assigned to each distinct pizza variant available for ordering.
order_id: A unique identifier for each order made, which links to multiple pizzas.
pizza_name_id: An identifier linking to a specific name of the pizza.
quantity: The number of units of a specific pizza variant ordered within an order.
order_date: The date when the order was placed.
order_time: The time when the order was placed.
unit_price: The cost of a single unit of the specific pizza variant.
total_price: The aggregated cost of all units of a specific pizza variant in an order.
pizza_size: Represents the size of the pizza (e.g., small, medium, large).
pizza_category: Indicates the category of the pizza, such as vegetarian, non-vegetarian, etc.
pizza_ingredients: Provides a list or description of the ingredients used in the pizza.
pizza_name: Specifies the name of the specific pizza variant ordered.


- Tabela Fato
CREATE TABLE fact_pizza_sales (
    pizza_sales_key INT PRIMARY KEY AUTO_INCREMENT,
    pizza_id INT,
    order_id INT,
    date_key INT,
    time_key INT,
    quantity INT,
    unit_price DECIMAL(10,2),
    total_price DECIMAL(10,2),
    FOREIGN KEY (pizza_id) REFERENCES dim_pizza(pizza_key),
    FOREIGN KEY (order_id) REFERENCES dim_order(order_key),
    FOREIGN KEY (date_key) REFERENCES dim_date(date_key),
    FOREIGN KEY (time_key) REFERENCES dim_time(time_key)
);

-- Dimensão Pizza
CREATE TABLE dim_pizza (
    pizza_key INT PRIMARY KEY AUTO_INCREMENT,
    pizza_id INT,
    pizza_name_id VARCHAR(50),
    pizza_name VARCHAR(100),
    pizza_size CHAR(1),
    pizza_category VARCHAR(50),
    pizza_ingredients TEXT
);

-- Dimensão Pedido
CREATE TABLE dim_order (
    order_key INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    order_date DATE,
    order_time TIME
);

-- Dimensão Data
CREATE TABLE dim_date (
    date_key INT PRIMARY KEY,
    order_date DATE,
    day INT,
    month INT,
    year INT,
    quarter INT,
    day_of_week INT,
    week_number INT,
    is_weekend BOOLEAN
);

-- Dimensão Tempo
CREATE TABLE dim_time (
    time_key INT PRIMARY KEY,
    order_time TIME,
    hour INT,
    minute INT,
    time_period VARCHAR(20)
);


