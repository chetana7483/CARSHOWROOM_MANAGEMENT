Car Showroom Management System
Overview
This Python project manages a car showroom database using MySQL. It allows adding, updating, deleting, and displaying records for cars, employees, customers, and sales.

Features
Add Record: Insert data into tables (car, employee, customer, sales).
Display Record: View all records in a selected table.
Delete Record: Remove a specific record by its primary key.
Update Record: Modify a specific column in a record.
Auto-Backend Storage: Data is automatically saved in the MySQL database.
Setup Instructions
Prerequisites:

MySQL installed.
Python libraries: mysql-connector-python.
Database Configuration:

Update MySQL credentials in the script:
con = mycon.connect(host='localhost', user='root', password="your_password")
Run the Program:

Execute the script. The required database and tables are created automatically if they don’t exist.
Usage
Choose an option from the menu:
1 to add records.
2 to display all records in a table.
3 to delete a record.
4 to update a record.
0 to exit.
Follow the prompts to input data.
Tables
Car: car_id, model, brand, price.
Employee: emp_id, car_id, name, position, salary.
Customer: customer_id, emp_id, name, contact_info.
Sales: sale_id, car_id, customer_id, date_of_sale.
License
Open for personal and educational use. Extend as needed!
