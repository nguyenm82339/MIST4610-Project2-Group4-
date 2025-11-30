

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

Our data model contains **15 entities** (within the required 10–15 range):

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
- `Ingredients_has_MenuItems`


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

`Ingredients_has_MenuItems` entity serves as an associative table that defines the many-to-many relationship between menu items and the ingredients required to prepare them



 **Data Dictionary:**

 **Customer**

| Column Name | Data Type | Size | Format     | Description                         | Key   |
| ----------- | --------- | ---- | ---------- | ----------------------------------- | ------ |
| CustomerID  | INT       | NN   |            | Unique identifier for each customer | **PK** |
| Fname       | VARCHAR   | 45   |            | Customer’s first name               |        |
| Lname       | VARCHAR   | 45   |            | Customer’s last name                |        |
| Email       | VARCHAR   | 45   |            | Email address of the customer       |        |
| PhoneNumber | VARCHAR   | 10   | 9999999999 | Customer’s phone number             |        |


**Reservations**

| Column Name    | Data Type | Size | Format              | Description                       | Key              |
| -------------- | --------- | ---- | ------------------- | --------------------------------- | ----------------- |
| ReservationsID | INT       | NN   |                     | Identifier for each reservation   | **PK**            |
| CustomerID     | INT       | NN   |                     | Customer who made the reservation | **FK** |
| TableID        | INT       | NN   |                     | Table that was reserved           | **FK**    |
| Date           | DATE      |      | YYYY-MM-DD HH:MM:SS | Date and time of reservation      | 
| Time           | VARCHAR   | 45   |                     | Time of the reservation           |  

**Feedback**

| Column Name | Data Type | Size  | Format | Description                     | Key              |
| ----------- | --------- | ----- | ------ | ------------------------------- | ----------------- |
| FeedbackID  | INT       | NN    |        | Identifier for feedback entry   | **PK**            |
| CustomerID  | INT       | NN    |        | Customer who gave feedback      | **FK** 
| Comments    | VARCHAR   | 1000  |        | Opionions given by customers    |
| Rating      | DECIMAL   | (2,1) |        | Score given by customers        |

**Table**

| Column Name     | Data Type | Size | Format | Description                   | Key   |
| --------------- | --------- | ---- | ------ | ----------------------------- | ------ |
| TableID         | INT       | NN   |        | Unique table identifier       | **PK** |
| SeatingCapacity | INT       | 45   |        | Number of seats at this table |        |
| Location        | VARCHAR   | 45   |        | Area inside the restaurant    |        |


**Order**

| Column Name | Data Type | Size | Format | Description                   | Key              |
| ----------- | --------- | ---- | ------ | ----------------------------- | ----------------- |
| OrderID     | INT       | NN   |        | Identifier for each order     | **PK**            |
| CustomerID  | INT       | NN   |        | Customer who placed the order | **FK** |


**MenuItems**

| Column Name               | Data Type | Size | Format | Description                                        | Key                 |
| ------------------------- | --------- | ---- | ------ | -------------------------------------------------- | -------------------- |
| MenuItemID                | INT       | NN   |        | Identifier for each menu item                      | **PK**               |
| Name                      | VARCHAR   | 45   |        | Name of the food/beverage item                     |                      |
| Category                  | VARCHAR   | 45   |        | Menu category (Entrée, Appetizer, etc.)            |                      |
| Price                     | DECIMAL   | 10,2 |        | Price of the menu item                             |                      |


**Ingredients**

| Column Name   | Data Type | Size | Format | Description                    | Key   |
| ------------- | --------- | ---- | ------ | ------------------------------ | ------ |
| IngredientsID | INT       | NN   |        | Identifier for each ingredient | **PK** |
| Name          | VARCHAR   | 45   |        | Ingredient name                |        |


**Supplier**

| Column Name | Data Type | Size | Format     | Description             | Key   |
| ----------- | --------- | ---- | ---------- | ----------------------- | ------ |
| SupplierID  | INT       | NN   |            | Identifier for supplier | **PK** |
| Fname       | VARCHAR   | 45   |            | Supplier first name     |        |
| Lname       | VARCHAR   | 45   |            | Supplier last name      |        |
| Contact     | VARCHAR   | 45   |            | Contact name            |        |
| PhoneNumber | VARCHAR   | 10   | 9999999999 | Supplier phone number   |        |
| City        | VARCHAR   | 45   |            | City of supplier        |        |


**Inventory**

| Column Name   | Data Type | Size | Format | Description                   | Key                 |
| ------------- | --------- | ---- | ------ | ----------------------------- | -------------------- |
| InventoryID   | INT       | NN   |        | Identifier for inventory item | **PK**               |
| IngredientsID | INT       | NN   |        | Ingredient stocked            | **FK** |
| SupplierID    | INT       | NN   |        | Supplier who provides item    | **FK**    |


**Supplier_has_Inventory**

| Column Name           | Data Type | Size | Format | Description               | Key               |
| --------------------- | --------- | ---- | ------ | ------------------------- | ------------------ |
| Supplier_SupplierID   | INT       | NN   |        | Supplier identifier       | **FK**  |
| Inventory_InventoryID | INT       | NN   |        | Inventory item identifier | **FK** |


**Payments**

| Column Name   | Data Type | Size | Format | Description                       | Key           |
| ------------- | --------- | ---- | ------ | --------------------------------- | -------------- |
| PaymentID     | INT       | NN   |        | Identifier for payment            | **PK**         |
| Order_OrderID | INT       | NN   |        | Order associated with the payment | **FK** |

**OrderDetails**

| Column Name          | Data Type | Size | Format | Description                       | Key               |
| -------------------- | --------- | ---- | ------ | --------------------------------- | ------------------ |
| OrderDetailsID       | INT       | NN   |        | Identifier for order detail entry | **PK**             |
| Order_OrderID        | INT       | NN   |        | Order being referenced            | **FK**     |
| MenuItems_MenuItemID | INT       | NN   |        | Menu item purchased               | **FK** |

**Employee**

| Column Name | Data Type | Size | Format     | Description                         | Key   |
| ----------- | --------- | ---- | ---------- | ----------------------------------- | ------ |
| EmployeeID  | INT       | NN   |            | Unique identifier for each employee | **PK** |
| Fname       | VARCHAR   | 45   |            | First name of employee              |        |
| Lname       | VARCHAR   | 45   |            | Last name of employee               |        |
| Role        | VARCHAR   | 45   |            | Job position in the restaurant      |        |
| Salary      | INT       | NN   |            | Salary value (annual or hourly)     |        |
| hire_date   | DATE      |      | YYYY-MM-DD | Hire date of employee               |        |

**Shifts**

| Column Name | Data Type | Size | Format | Description                | Key              |
| ----------- | --------- | ---- | ------ | -------------------------- | ----------------- |
| ShiftsID    | INT       | NN   |        | Identifier for each shift  | **PK**            |
| EmployeeID  | INT       | NN   |        | Employee working the shift | **FK** |

**Ingredients_has_MenuItems**

| Column Name | Data Type | Size | Format | Description                | Key              |
| ----------- | --------- | ---- | ------ | -------------------------- | ----------------- |
| Ingredients_IngredientsID    | INT       | NN   |        | Identifys the ingreidents  | **FK**            |
| MenuItems_MenuItemID  | INT       | NN   |        | Identifys the menu item | **FK** |


# Queries

<img width="631" height="306" alt="image" src="https://github.com/user-attachments/assets/f0066b5f-518b-4ff5-bac3-a31e9e8b9a83" />


Query 1: This query shows us how many reservations each “spot” in the restaurant gets and also adds a final row that shows the grand total of reservations for all the locations. This will allow managers to quickly figure out which locations within the restaurant need to be improved, whether with better lighting or decoration to attract more customers there. Managers can also continue maintaining the most popular areas the way they are not to deteriorate current customers to those spots.

<img width="628" height="431" alt="Screenshot 2025-11-30 at 4 45 09 PM" src="https://github.com/user-attachments/assets/a3e367a6-0ed4-4f72-ad94-98a20d17bcb1" />


Query 2: This query shows whether or not a customer has placed an order; or whether they only reserved a table and are not “active” yet. This can help management figure out the average amount of customers that “flake” or reserve tables but then never convert to actually placing an order which then cannibalizes the sales of the restaurant. More reservations mean nothing unless they convert to actual sales. 

<img width="625" height="513" alt="Screenshot 2025-11-30 at 4 45 49 PM" src="https://github.com/user-attachments/assets/ac2528cd-0577-4c2f-9900-56390dabe868" />


Query 3: This query indicates how many reservations are happening for the restaurant each day of the week as well as compares it to the average reservation per calendar day. It labels days that meet or exceed the average as a Busy Day, while all else is Less Busy Day. This can help management with staffing on days that have more traffic coming through to the restaurant as well as indicating days that management should be promoting more or encouraging sales promotions.

<img width="624" height="369" alt="Screenshot 2025-11-30 at 4 46 11 PM" src="https://github.com/user-attachments/assets/017eb60e-c2f1-43a2-b9ce-61ab200f0715" />


Query 4: This query shows us how many reservations each customer places versus the number of orders they placed at the restaurant. Management can use this to see which customers have extremely low conversion rates and book but don’t spend that much versus customers that spend a lot at the restaurant and can be seen as loyal customers to target with advertising and promotions.

<img width="618" height="501" alt="Screenshot 2025-11-30 at 4 46 33 PM" src="https://github.com/user-attachments/assets/ee1fcffb-3d68-4859-bcbd-35d7cd3c2361" />


Query 5:  This query allows us to collect the different positions among the firms with their respective number of employees, average salary, minimum salary, and maximum salary. There is also an additional column that indicates whether the salary is above or below average. Furthermore the average years employed for each role is provided as well. Management can use this when deciding raises and emotions as well as salary negotiations when hiring new employees.

<img width="619" height="335" alt="Screenshot 2025-11-30 at 4 46 58 PM" src="https://github.com/user-attachments/assets/14f5b1fb-eff0-43f3-9a9a-56245eabfa99" />



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


