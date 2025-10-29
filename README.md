# My Online Beauty Shop SQL Project

<a name="readme-top"></a>

<!-- TABLE OF CONTENTS -->

# 📗 Table of Contents

- [My SQL Project](#about-project)
- [📗 Table of Contents](#-table-of-contents)
- [📖 My SQL Project](#about-project)
  - [🛠 Built With ](#-built-with-)
    - [Tech Stack ](#tech-stack-)
    - [Key Features ](#key-features-)
  - [💻 Getting Started ](#-getting-started-)
    - [Prerequisites](#prerequisites)
    - [Setup](#setup)
    - [Usage](#usage)
  - [👥 Authors ](#-authors-)
  - [🔭 Future Features ](#-future-features-)
  - [🤝 Contributing ](#-contributing-)

<!-- PROJECT DESCRIPTION -->

# 📖 My SQL Project <a name="about-project"></a>

**My SQL Project** is a simple Database that uses SQL, Postgres via Supabase and R to create, query and secure a **Online Beauty Shop** database.

## 🛠 Built With <a name="built-with"></a>

### Tech Stack <a name="tech-stack"></a>
- SQL
- Postgres DB

<!-- Features -->

### Key Features <a name="key-features"></a>

- [ ] **Tables**
- [ ] **Schema**
- [ ] **Access control**

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->

## 💻 Getting Started <a name="getting-started"></a>

To rebuild this DB, follow these steps.

### Prerequisites

To run this project, you need:
- [A Supabase account](https://supabase.com/)
- [Knowledge on SQL](https://www.w3schools.com/sql/)
- A schema for creating your tables in the DB

<!-- ### Setup -->
### Setup

Copy the contents of this Readme.md to your Project's file

OR

Clone this repository to your desired folder:

```sh
  git clone https://github.com/joyapisi/readme-template-data
  cd budget-app
```

<!-- ### DB Creation -->

### DB Schema

- The DB is made up of 3 tables. Eaach table has 5 entries.
- To create the table, you will need a schema as shown below:

```sql
-- Drop old tables
DROP TABLE IF EXISTS orders ;
DROP TABLE IF EXISTS customers ;
DROP TABLE IF EXISTS products;

-- Create customers table
CREATE TABLE customers (
  id SERIAL PRIMARY KEY,
  full_name TEXT NOT NULL,
  email TEXT UNIQUE NOT NULL,
  phone_number TEXT
);

-- Create products table
CREATE TABLE products (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  category TEXT,
  price NUMERIC(8,2) NOT NULL,
  in_stock BOOLEAN DEFAULT true
);

-- Create orders table
CREATE TABLE orders (
  id SERIAL PRIMARY KEY,
  customer_id INT REFERENCES customers(id),
  product_id INT REFERENCES products(id),
  order_date TIMESTAMP DEFAULT now()
);

-- Insert sample customers
INSERT INTO customers (full_name, email, phone_number) VALUES
  ('Sophia Njeri', 'sophia@example.com', '0712000001'),
  ('Lilian Mwangi', 'lilian@example.com', '0712000002'),
  ('Janet Otieno', 'janet@example.com', '0712000003'),
  ('Mary Achieng', 'mary@example.com', '0712000004'),
  ('Becky Wanjiku', 'becky@example.com', '0712000005');

-- Insert sample products
INSERT INTO products (name, category, price, in_stock) VALUES
  ('Shea Butter Lotion', 'Skincare', 1200.00, true),
  ('Matte Lipstick', 'Makeup', 950.00, true),
  ('Aloe Vera Face Wash', 'Skincare', 850.00, false),
  ('Perfume – Rose Essence', 'Fragrance', 1800.00, true),
  ('Nail Polish Set', 'Cosmetics', 600.00, true);

-- Insert sample orders
INSERT INTO orders (customer_id, product_id) VALUES
  (1, 1),
  (2, 2),
  (3, 4),
  (4, 3),
  (5, 5);

```

- The Tables should look like this in Supabase:

customers:
<img width="1116" height="309" alt="image" src="https://github.com/user-attachments/assets/2e1665fa-be38-4eba-8ca1-ce13498eca1e" />

products:
<img width="1048" height="239" alt="image" src="https://github.com/user-attachments/assets/726767bd-ad4a-412d-a1d8-31e39301cf1b" />

orders:

<img width="721" height="210" alt="image" src="https://github.com/user-attachments/assets/82408731-38f1-44a9-956b-e3b1e8e5e4ce" />


- The ERD screenshot from Supabase looks like this: 
<img width="818" height="558" alt="image" src="https://github.com/user-attachments/assets/fd708aa0-b6a3-42d4-af06-3149f43205ca" />


- To test the table, I used two queries: 

```sql
-- View all products in stock
SELECT * FROM products WHERE in_stock = TRUE;
````

```sql
-- View all orders by a specific customer
SELECT c.full_name, p.name AS product_name, o.order_date
FROM orders o
JOIN customers c ON o.customer_id = c.id
JOIN products p ON o.product_id = p.id
WHERE c.full_name = 'Sophia Njeri';
````

- Here are the results of the queries:
<img width="595" height="223" alt="image" src="https://github.com/user-attachments/assets/e701507d-3ddc-41e5-96c4-ffe4c4739000" />

<img width="483" height="121" alt="image" src="https://github.com/user-attachments/assets/e25425fd-e0f4-465c-adc6-3ef9706ed488" />


<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- AUTHORS -->

## 👥 Authors <a name="authors"></a>

👤 **Ruth Mwende**

- GitHub: [@mwender486](https://github.com/mwender486)
- Twitter: [@mwende134](https://twitter.com/mwende134)
- LinkedIn: [@ruthmwende](https://linkedin.com/in/ruthmwende)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- FUTURE FEATURES -->

## 🔭 Future Features <a name="future-features"></a>

- [ ] **Add security**
- [ ] **Link DB to R for visualisation purposes and further analyses**

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->

## 🤝 Contributing <a name="contributing"></a>

Contributions, issues, and feature requests are welcome!

Feel free to check the [issues page](../../issues/).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- SUPPORT -->
