import mysql.connector as mycon

# Establish connection
con = mycon.connect(host='localhost', user='root', password="chetana123")
cur = con.cursor()

# Create database and tables if they don't exist
cur.execute("CREATE DATABASE IF NOT EXISTS car_showroom_management")
cur.execute("USE car_showroom_management")

# Creating tables
cur.execute("""
    CREATE TABLE IF NOT EXISTS car (
        car_id INT PRIMARY KEY,
        model VARCHAR(50),
        brand VARCHAR(50),
        price INT
    )
""")

cur.execute("""
    CREATE TABLE IF NOT EXISTS employee (
        emp_id INT PRIMARY KEY,
        car_id INT,
        name VARCHAR(50),
        position VARCHAR(50),
        salary INT,
        FOREIGN KEY (car_id) REFERENCES car(car_id)    
    )
""")

cur.execute("""
    CREATE TABLE IF NOT EXISTS customer (
        customer_id INT PRIMARY KEY,
        emp_id INT, 
        name VARCHAR(50),  
        contact_info VARCHAR(100),
        FOREIGN KEY (emp_id) REFERENCES employee(emp_id)    
    )
""")

cur.execute("""
    CREATE TABLE IF NOT EXISTS sales (
        sale_id INT PRIMARY KEY,
        car_id INT,
        customer_id INT,
        date_of_sale DATE,
        FOREIGN KEY (car_id) REFERENCES car(car_id),
        FOREIGN KEY (customer_id) REFERENCES customer(customer_id)
    )
""")

con.commit()

def add_record():
    table = input("Enter the table name (car, employee, customer, sales): ")
    if table == "car":
        car_id = int(input("Enter Car ID: "))
        model = input("Enter Model: ")
        brand = input("Enter Brand: ")
        price = int(input("Enter Price: "))
        query = "INSERT INTO car (car_id, model, brand, price) VALUES (%s, %s, %s, %s)"
        values = (car_id, model, brand, price)
    elif table == "employee":
        emp_id = int(input("Enter Employee ID: "))
        car_id = int(input("Enter Car ID: "))
        name = input("Enter Name: ")
        position = input("Enter Position: ")
        salary = int(input("Enter Salary: "))
        query = "INSERT INTO employee (emp_id, car_id, name, position, salary) VALUES (%s, %s, %s, %s, %s)"
        values = (emp_id, car_id, name, position, salary)
    elif table == "customer":
        customer_id = int(input("Enter Customer ID: "))
        emp_id = int(input("Enter Employee ID: "))
        name = input("Enter Name: ")
        contact_info = input("Enter Contact Info: ")
        query = "INSERT INTO customer (customer_id, emp_id, name, contact_info) VALUES (%s, %s,%s, %s)"
        values = (customer_id, emp_id, name, contact_info)
    elif table == "sales":
        sale_id = int(input("Enter Sale ID: "))
        car_id = int(input("Enter Car ID: "))
        customer_id = int(input("Enter Customer ID: "))
        date_of_sale = input("Enter Date of Sale (YYYY-MM-DD): ")
        query = "INSERT INTO sales (sale_id, car_id, customer_id, date_of_sale) VALUES (%s, %s, %s, %s)"
        values = (sale_id, car_id, customer_id, date_of_sale)
    else:
        print("Invalid table name.")
        return
    cur.execute(query, values)
    con.commit()
    print("## Data Saved ##")

def display_record():
    table = input("Enter the table name (car, employee, customer, sales): ")
    query = "SELECT * FROM {}".format(table)
    cur.execute(query)
    result = cur.fetchall()
    headers = [desc[0].upper() for desc in cur.description]
    print(f"{'   '.join(headers)}")
    for row in result:
        print(f"{'     '.join(str(item) for item in row)}")

def delete_record():
    table = input("Enter the table name (car, employee, customer, sales): ")
    column = input("Enter the column name of the primary key: ")
    id = input("Enter the ID of the record to delete: ")
    query = "DELETE FROM {} WHERE {} = %s".format(table, column)
    cur.execute(query, (id,))
    con.commit()
    print("## Record Deleted ##")

def update_record():
    table = input("Enter the table name (car, employee, customer, sales): ")
    column = input("Enter the column name of the primary key: ")
    id = input("Enter the ID of the record to update: ")
    update_col = input("Enter the column name to update: ")
    new_value = input("Enter the new value: ")
    query = "UPDATE {} SET {} = %s WHERE {} = %s".format(table, update_col, column)
    cur.execute(query, (new_value, id))
    con.commit()
    print("## Record Updated ##")

choice = None
while choice != 0:
    print("1. ADD RECORD")
    print("2. DISPLAY RECORD")
    print("3. DELETE RECORD")
    print("4. UPDATE RECORD")
    print("0. EXIT")
    choice = int(input("Enter Choice: "))
    
    if choice == 1:
        add_record()
    elif choice == 2:
        display_record()
    elif choice == 3:
        delete_record()
    elif choice == 4:
        update_record()
    elif choice == 0:
        con.close()
        print("## Bye!! ##")
    else:
        print("## INVALID CHOICE ##")
