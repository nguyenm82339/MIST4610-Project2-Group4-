

# MIST4610-Project2-Group4-

# Team 4 MIST 4610 Group Project 2

## Team Name:
29704 Group 4



## Team Members:

1. Smit Shah [@smit9shah](https://github.com/smit9shah)
2. Nicholas Nichols [@nnichols915](https://github.com/nnichols915)
3. Martin Nguyen [@nguyenm82339](https://github.com/nguyenm82339)
4. Riley Collman [@rcollman44](https://github.com/rcollman44)
5. Sidd Navar [sn18206-oss](https://github.com/sn18206-oss)


**Project 2 repository:**  
<https://github.com/nguyenm82339/MIST4610-Project2-Group4->

### Scenario Description

Our project models a full-service casual sit-down restaurant that serves guests primarily through in-person dining and reservations.

This restaurant database helps manage everyday operations, including customers, reservations, orders, payments, employees, inventory, and suppliers. It keeps track of customer visits, from booking a table to placing and completing an order. The system records each order and the menu items inside it, along with the ingredients needed to prepare those items. Inventory levels and supplier relationships are also managed to support smooth kitchen operations. Employee schedules are organized through shift tracking, and payment records make it easy to review revenue and transaction details. Customers can leave feedback about their dining experience to help the restaurant monitor service quality. Overall, the database is designed to keep restaurant operations organized and efficient, focusing on improving workflow and the guest experience rather than advanced business functions like marketing or payroll.


---

## Data Model

Our data model contains **13 entities** (within the required 10–15 range):

- `Customer`
- `Reservations`
- `Tables`
- `Orders`
- `OrderDetails`
- `MenuItems`
- `Ingredients`
- `Inventory`
- `Supplier`
- `Supplier_has_Inventory` 
- `Employee`
- `Shifts`
- `Payments`
- `Feedback`


   **Data Model Image:**

  <img width="979" height="607" alt="image" src="https://github.com/user-attachments/assets/31d50a7e-235e-4646-a16f-79a79fed96ff" />



## Description

`Customer`: Stores customer details, including contact information and reservation/ordering history.

`Reservations:` Records customer reservations, including date, time, party size, and assigned table.

`Tables:` Defines restaurant tables, their capacity, and location; each table may have multiple reservations over time.

`Orders` Tracks customer orders, linking each order to a customer and containing details about the dining transaction.

`OrderDetails:` Line-item details for each order, listing menu items, quantities, and item-level pricing.

`MenuItems:` Contains menu item information such as name, price, and category (entrée, appetizer, drink, etc.).

`Ingredients:` Lists ingredients used in menu items; each ingredient may be used in multiple menu items.

`Inventory:` Stores inventory quantities, restock levels, and associated ingredient details.

`Supplier:` Contains vendor information for companies supplying restaurant inventory items.

`Supplier_has_Inventory:` Links suppliers to the inventory items they provide, allowing many suppliers per item and many items per supplier.

`Employee` Stores employee information, such as name, role (server, chef, manager), salary, and hire date.

`Shifts:` Logs employee shift assignments, including date, time, and duration.

`Payments:` Records payments for orders, supporting multiple payment methods per order.

`Feedback:` Captures customer feedback about their visit, including ratings and comments related to orders or employees.


 **Data Dictionary:**

| Column Name | Data Type | Size | Format     | Description                         | Key?   |
| ----------- | --------- | ---- | ---------- | ----------------------------------- | ------ |
| CustomerID  | INT       | NN   |            | Unique identifier for each customer | **PK** |
| Fname       | VARCHAR   | 45   |            | Customer’s first name               |        |
| Lname       | VARCHAR   | 45   |            | Customer’s last name                |        |
| Email       | VARCHAR   | 45   |            | Email address of the customer       |        |
| PhoneNumber | VARCHAR   | 10   | 9999999999 | Customer’s phone number             |        |


**Reservations**

| Column Name    | Data Type | Size | Format              | Description                       | Key?              |
| -------------- | --------- | ---- | ------------------- | --------------------------------- | ----------------- |
| ReservationsID | INT       | NN   |                     | Identifier for each reservation   | **PK**            |
| CustomerID     | INT       | NN   |                     | Customer who made the reservation | **FK – Customer** |
| TableID        | INT       | NN   |                     | Table that was reserved           | **FK – Table**    |
| Date           | DATE      |      | YYYY-MM-DD HH:MM:SS | Date and time of reservation      |                   |

**Feedback**

| Column Name | Data Type | Size  | Format | Description                     | Key?              |
| ----------- | --------- | ----- | ------ | ------------------------------- | ----------------- |
| FeedbackID  | INT       | NN    |        | Identifier for feedback entry   | **PK**            |
| CustomerID  | INT       | NN    |        | Customer who gave feedback      | **FK – Customer** |
| Comments    | VARCHAR   | 1000  |        | Written comments from customers |                   |
| Rating      | DECIMAL   | (2,1) |        | Score given by customer         |                   |

**Table**

| Column Name     | Data Type | Size | Format | Description                   | Key?   |
| --------------- | --------- | ---- | ------ | ----------------------------- | ------ |
| TableID         | INT       | NN   |        | Unique table identifier       | **PK** |
| SeatingCapacity | INT       | 45   |        | Number of seats at this table |        |
| Location        | VARCHAR   | 45   |        | Area inside the restaurant    |        |


**Order**

| Column Name | Data Type | Size | Format | Description                   | Key?              |
| ----------- | --------- | ---- | ------ | ----------------------------- | ----------------- |
| OrderID     | INT       | NN   |        | Identifier for each order     | **PK**            |
| CustomerID  | INT       | NN   |        | Customer who placed the order | **FK – Customer** |


**MenuItems**

| Column Name               | Data Type | Size | Format | Description                                        | Key?                 |
| ------------------------- | --------- | ---- | ------ | -------------------------------------------------- | -------------------- |
| MenuItemID                | INT       | NN   |        | Identifier for each menu item                      | **PK**               |
| Name                      | VARCHAR   | 45   |        | Name of the food/beverage item                     |                      |
| Category                  | VARCHAR   | 45   |        | Menu category (Entrée, Appetizer, etc.)            |                      |
| Price                     | DECIMAL   | 10,2 |        | Price of the menu item                             |                      |
| IngredientID              | VARCHAR   | 45   |        | Ingredient reference (unused or mis-modeled field) |                      |
| Ingredients_IngredientsID | INT       | NN   |        | Ingredient used in the item                        | **FK – Ingredients** |


**Ingredients**

| Column Name   | Data Type | Size | Format | Description                    | Key?   |
| ------------- | --------- | ---- | ------ | ------------------------------ | ------ |
| IngredientsID | INT       | NN   |        | Identifier for each ingredient | **PK** |
| Name          | VARCHAR   | 45   |        | Ingredient name                |        |


**Supplier**

| Column Name | Data Type | Size | Format     | Description             | Key?   |
| ----------- | --------- | ---- | ---------- | ----------------------- | ------ |
| SupplierID  | INT       | NN   |            | Identifier for supplier | **PK** |
| Fname       | VARCHAR   | 45   |            | Supplier first name     |        |
| Lname       | VARCHAR   | 45   |            | Supplier last name      |        |
| Contact     | VARCHAR   | 45   |            | Contact name            |        |
| PhoneNumber | VARCHAR   | 10   | 9999999999 | Supplier phone number   |        |
| City        | VARCHAR   | 45   |            | City of supplier        |        |


**Inventory**

| Column Name   | Data Type | Size | Format | Description                   | Key?                 |
| ------------- | --------- | ---- | ------ | ----------------------------- | -------------------- |
| InventoryID   | INT       | NN   |        | Identifier for inventory item | **PK**               |
| IngredientsID | INT       | NN   |        | Ingredient stocked            | **FK – Ingredients** |
| SupplierID    | INT       | NN   |        | Supplier who provides item    | **FK – Supplier**    |


**Supplier_has_Inventory**

| Column Name           | Data Type | Size | Format | Description               | Key?               |
| --------------------- | --------- | ---- | ------ | ------------------------- | ------------------ |
| Supplier_SupplierID   | INT       | NN   |        | Supplier identifier       | **FK – Supplier**  |
| Inventory_InventoryID | INT       | NN   |        | Inventory item identifier | **FK – Inventory** |


**Payments**

| Column Name   | Data Type | Size | Format | Description                       | Key?           |
| ------------- | --------- | ---- | ------ | --------------------------------- | -------------- |
| PaymentID     | INT       | NN   |        | Identifier for payment            | **PK**         |
| Order_OrderID | INT       | NN   |        | Order associated with the payment | **FK – Order** |

**OrderDetails**

| Column Name          | Data Type | Size | Format | Description                       | Key?               |
| -------------------- | --------- | ---- | ------ | --------------------------------- | ------------------ |
| OrderDetailsID       | INT       | NN   |        | Identifier for order detail entry | **PK**             |
| Order_OrderID        | INT       | NN   |        | Order being referenced            | **FK – Order**     |
| MenuItems_MenuItemID | INT       | NN   |        | Menu item purchased               | **FK – MenuItems** |

**Employee**

| Column Name | Data Type | Size | Format     | Description                         | Key?   |
| ----------- | --------- | ---- | ---------- | ----------------------------------- | ------ |
| EmployeeID  | INT       | NN   |            | Unique identifier for each employee | **PK** |
| Fname       | VARCHAR   | 45   |            | First name of employee              |        |
| Lname       | VARCHAR   | 45   |            | Last name of employee               |        |
| Role        | VARCHAR   | 45   |            | Job position in the restaurant      |        |
| Salary      | INT       | NN   |            | Salary value (annual or hourly)     |        |
| hire_date   | DATE      |      | YYYY-MM-DD | Hire date of employee               |        |

**Shifts**

| Column Name | Data Type | Size | Format | Description                | Key?              |
| ----------- | --------- | ---- | ------ | -------------------------- | ----------------- |
| ShiftsID    | INT       | NN   |        | Identifier for each shift  | **PK**            |
| EmployeeID  | INT       | NN   |        | Employee working the shift | **FK – Employee** |





# Power BI Visualizations 
<img width="738" height="387" alt="image" src="https://github.com/user-attachments/assets/f9c1898b-47c3-4065-93d0-54ff723f061d" />

Purpose: This visual highlights the total spending by each customer. 

Relevance: Managers can identify high-value customers and guide loyalty strategies around them.

<img width="525" height="387" alt="image" src="https://github.com/user-attachments/assets/a35a0fe7-9c7d-4e6a-b668-00b1aa69f194" />

Purpose: This visualization compares the average base salary across different employee positions within the organization.

Relevance: Managers use this to evaluate compensation structure, identify pay imbalances, and support budgeting + staffing decisions.

<img width="722" height="402" alt="image" src="https://github.com/user-attachments/assets/95addbf9-f8e8-42fc-bab8-1cbfe7c752df" />

Purpose: This chart shows the total quantity of each ingredient currently in stock.

Relevance: Managers require this information to monitor inventory levels, preventing shortages and optimizing purchasing decisions. 


