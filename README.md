# Bike Rental Shop

This is a project where running a script allows the user to interact with a PostgreSQL database for bike rentals and returns.

## How to run

First, you need to create a database with the following schema:
1. database: <strong>bikes</strong>
2. tables:
   <ol>
     <li><strong>bikes</strong></li>
     <ul>
       <li>bike_id serial not null primary key</li>
       <li>type varchar(50) not null</li>
       <li>size int not null</li>
       <li>available boolean not null default true</li>
       <li>foreign key (bike_id) REFERENCES bikes(bike_id)</li>
     </ul>
     <li><strong>customers</strong></li>
     <ul>
       <li>customer_id serial not null primary key</li>
       <li>phone varchar(15) not null unique</li>
       <li>name varchar(40) not null</li>
       <li>foreign key (customer_id) REFERENCES customers(customer_id)</li>
     </ul>
       
     <li><strong>rentals</strong></li>
     <ul>
       <li>rental_id serial not null primary key</li>
       <li>customer_id int not null</li>
       <li>bike_id int not null</li>
       <li>date_rented date not null default now()</li>
       <li>date_returned date</li>
       <li>foreign key (bike_id) REFERENCES bikes(bike_id)</li>
       <li>foreign key (customer_id) REFERENCES customers(customer_id)</li>
     </ul>
   </ol>

Next, in the terminal, make sure that the script has execution permissions (`chmod +x bash-shop.sh`).

Then, in the terminal, run the script
```bash
./bash-shop.sh
```
