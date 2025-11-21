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

-   `GET /warehouses` - Retrieves all warehouses in the system with their locations and capacity information
-   `POST /warehouses/new_warehouse` - Creates a new warehouse with name, capacity, and location details (city, state, country)
-   `GET /warehouses/warehouse/{id}` - Fetches details of a specific warehouse by its ID including all associated information
-   `PUT /warehouses/update/{id}` - Updates warehouse information such as name, capacity, or location for the specified warehouse ID
-   `DELETE /warehouses/delete/{id}` - Permanently deletes a warehouse and removes all item associations from the system
-   `GET /warehouses/warehouseItems/{id}` - Returns a list of all items currently stored in the specified warehouse
-   `POST /warehouses/addItemToWarehouse/{id}` - Creates a new item and immediately associates it with the specified warehouse
-   `PUT /warehouses/deleteItemInWarehouse/{warehouseId}/{itemId}` - Removes an item from a warehouse's inventory without deleting the item from the system
-   `PUT /warehouses/transferItemFromWarehouseToWarehouse/{presentWarehouseId}/{itemId}/{newWarehouseId}` - Transfers an item from one warehouse to another, removing it from the source and adding it to the destination

### **Item Endpoints**

-   `GET /items` - Retrieves all items in the inventory system across all warehouses
-   `POST /items/item` - Creates a new item with details like name, SKU, description, quantity, and storage location
-   `GET /items/item/{id}` - Fetches detailed information about a specific item by its ID
-   `PUT /items/update-item/{id}` - Updates item information such as name, SKU, description, quantity, or storage location
-   `DELETE /items/delete/{id}` - Permanently deletes an item from the system and removes it from all associated warehouses
-   `GET /items/warehousesForItem/{id}` - Returns a list of all warehouses that currently stock the specified item
-   `PUT /items/addItemToAnWarehouse/{itemId}/{warehouseId}` - Associates an existing item with an existing warehouse, creating a many-to-many relationship

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
