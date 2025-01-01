
# Online Shopping Platform with Secure Transactions

This project implements an **Online Shopping Platform** with functionalities for user registration, login, product browsing, shopping cart management, and order placement. The system emphasizes security measures like password encryption, SQL injection prevention, and transaction management to ensure data integrity.

---

## **Features**
1. **User Management**:
   - Registration with secure password hashing (`password_hash`).
   - Login with parameterized queries to prevent SQL injection.
   - Session management for user authentication and authorization.

2. **Product Management**:
   - Categories and products display with real-time search functionality.
   - Add, update, and delete products in the shopping cart.
   - Checkout functionality with order summary.

3. **Admin Features**:
   - Manage categories, products, and order histories.
   - Real-time stock updates and product price change history.

4. **Security**:
   - Password hashing with SHA-256 and `password_hash`.
   - SQL injection prevention using parameterized queries.
   - Transaction management to ensure atomicity in database operations.

---

## **Database Schema**
### **Key Tables**:
1. **Employees**: Stores employee credentials and activity logs.
2. **Customers**: Stores customer details.
3. **Products**: Information about products, categories, and stock.
4. **Orders**: Order details with status and timestamps.
5. **Order Items**: Items included in each order.
6. **Product History**: Tracks product price and stock changes.
7. **Shopping Cart**: Manages items added by customers before checkout.

### **Relational Schema**:
- Detailed schema includes primary keys, foreign keys, and triggers to maintain referential integrity.

---

## **Functional Highlights**
1. **Customer Journey**:
   - Browse products by category or search keywords.
   - Add items to the shopping cart, modify quantities, or remove items.
   - Place orders and view order history.

2. **Admin Operations**:
   - Add, update, and delete products and categories.
   - Manage employee accounts with temporary password generation.

3. **Transactions**:
   - Atomic operations for sensitive actions like password updates and order placements.
   - Rollback mechanisms to handle failures gracefully.

---

## **Security Implementations**
1. **Password Encryption**:
   - Passwords are securely hashed using `password_hash` with `PASSWORD_DEFAULT` for storing in the database.
   - Example:
     ```php
     $hashedPassword = password_hash($newPassword, PASSWORD_DEFAULT);
     ```

2. **SQL Injection Prevention**:
   - All database interactions use parameterized queries.
   - Example:
     ```php
     $statement = $dbh->prepare("SELECT * FROM customer WHERE username = :username");
     $statement->bindParam(":username", $username);
     ```

3. **Transaction Management**:
   - Ensures atomicity for critical database operations like order placement and password updates.
   - Example:
     ```php
     $dbh->beginTransaction();
     $dbh->commit();
     ```

4. **Session Management**:
   - Secures user sessions to persist data across pages.
   - Example:
     ```php
     $_SESSION["username"] = $username;
     ```

---

## **Technical Implementation**
1. **Programming Language**: PHP
2. **Database**: MySQL
3. **Libraries and Tools**:
   - PDO (PHP Data Objects) for secure database interactions.
   - Password hashing with PHP's built-in functions.
4. **Frontend**:
   - Simple HTML and CSS for user interaction.

---

## **Usage Instructions**
1. **Set Up the Database**:
   - Import the SQL schema from `createtable.sql`.
   - Insert initial data using `Insertdata.sql`.

2. **Run the Application**:
   - Host the PHP files on a local or remote web server.
   - Configure the database connection in `config.php`.

3. **Testing**:
   - Use the provided sample customers and employees for login.
   - Perform actions like adding to the cart, updating stock, and checking order history.

---

## **Future Enhancements**
1. Implement **real-time notifications** for stock updates and order confirmations.
2. Expand the system to include **role-based access control**.
3. Use **AJAX** for seamless page updates without reloads.
4. Integrate with a payment gateway for online transactions.

---

## **Contributors**
- **Puja Ammineni**
