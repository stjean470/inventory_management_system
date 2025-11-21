# Inventory Management System

A full-stack inventory management application built with **Spring Boot**
and **React** that allows users to manage warehouses and items across
multiple locations.

## 🚀 Features

### **Warehouse Management**

-   Create, read, update, and delete warehouses
-   Track warehouse capacity and location (city, state, country) or location(city, country) for countries outside the US
-   View all items stored in each warehouse

### **Item Management**

-   Create, read, update, and delete inventory items
-   Track item details: name, SKU, description, quantity, and storage
    location
-   View which warehouses contain specific items

### **Item-Warehouse Operations**

-   Add items to warehouses
-   Transfer items between warehouses
-   Remove items from warehouses
-   Prevent duplicate item assignments

## 🛠 Tech Stack

### **Backend**

-   Java 17+
-   Spring Boot -- RESTful API
-   Spring Data JPA
-   PostgreSQL
-   Maven

### **Frontend**

-   React
-   Vite
-   React Router
-   Axios
-   Bootstrap
-   React Bootstrap
-   React Icons

## 📦 Prerequisites

-   **JDK 17+**
-   **Node.js 16+**
-   **PostgreSQL 12+**
-   **Maven 3.6+**

## 🗄 Database Setup

### Create the PostgreSQL database:

``` sql
CREATE DATABASE inventoryDb;
```

### Update `application.properties`:

``` properties
spring.datasource.url=jdbc:postgresql://localhost:5432/inventoryDb
spring.datasource.username=your_username
spring.datasource.password=your_password
```

## ▶️ Installation & Running

### **Backend Setup**

``` bash
cd InventoryManagementSystem_Backend
mvn clean install
mvn spring-boot:run
```

Backend runs at: **http://localhost:8080**

### **Frontend Setup**

``` bash
cd InventoryManagementSystem_Client
npm install
npm run dev
```

Frontend runs at: **http://localhost:3000**

## 📡 API Endpoints

### **Warehouse Endpoints**

-   `GET /warehouses`
-   `POST /warehouses/new_warehouse`
-   `GET /warehouses/warehouse/{id}`
-   `PUT /warehouses/update/{id}`
-   `DELETE /warehouses/delete/{id}`
-   `GET /warehouses/warehouseItems/{id}`
-   `POST /warehouses/addItemToWarehouse/{id}`
-   `PUT /warehouses/deleteItemInWarehouse/{warehouseId}/{itemId}`
-   `PUT /warehouses/transferItemFromWarehouseToWarehouse/{presentWarehouseId}/{itemId}/{newWarehouseId}`

### **Item Endpoints**

-   `GET /items`
-   `POST /items/item`
-   `GET /items/item/{id}`
-   `PUT /items/update-item/{id}`
-   `DELETE /items/delete/{id}`
-   `GET /items/warehousesForItem/{id}`
-   `PUT /items/addItemToAnWarehouse/{itemId}/{warehouseId}`

## 📁 Project Structure

    ├── InventoryManagementSystem_Backend/
    │   ├── src/main/java/com/skillstorm/inventory_management_system/
    │   │   ├── controllers/          # REST controllers
    │   │   ├── models/               # Entity classes
    │   │   ├── repositories/         # JPA repositories
    │   │   ├── services/             # Business logic
    │   │   └── exceptions/           # Custom exceptions
    │   └── src/main/resources/
    │       ├── application.properties
    │       └── schema.sql
    │
    └── InventoryManagementSystem_Client/
        ├── components/
        │   ├── item/                 # Item components
        │   └── warehouse/            # Warehouse components
        ├── services/
        │   └── apiFunctions.js       # API layer
        ├── util/                     # Utility files (countries, states)
        └── App.jsx                   # Main application

## 🔎 Key Features Explained

### **Many-to-Many Relationship**

-   An item can be stored in multiple warehouses
-   A warehouse can contain multiple items

### **Location Management**

-   **US warehouses** → City, State, Country
-   **International warehouses** → City, Country

### **Item Transfer Logic**

- You can create an Item and allocate item to multiple Warehouses
- If item is in warehouse, transfer won't happen(throws exception)

## 🤝 Contributing

Contributions are welcome! Feel free to submit a Pull Request.
