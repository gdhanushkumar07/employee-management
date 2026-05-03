# Employee Management System

A simple and responsive Employee Management Web Application built using **Vue.js**, **Axios**, and **MockAPI**.  
This project demonstrates full CRUD (**Create, Read, Update, Delete**) operations with a clean Bootstrap UI.

---

## 🚀 Features

- Add new employee records
- View all employees in a table
- Update employee details
- Delete employee records
- Responsive UI using Bootstrap
- Real-time API interaction using Axios

---

## 🛠️ Tech Stack

- **Frontend:** Vue.js
- **HTTP Client:** Axios
- **Backend (Mock):** MockAPI
- **Styling:** Bootstrap

---

## 📂 Project Structure

```
src/
 ├── components/
 │    ├── AddEmployee.vue        # Create Employee
 │    ├── EmployeeList.vue       # Read Employees
 │    ├── UpdateEmployee.vue     # Update Employee
 │    └── DeleteEmployee.vue     # Delete Employee
 ├── App.vue                     # Main App Component
 └── main.js                     # Entry Point
```

---

## ⚙️ Installation & Setup

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/gdhanushkumar07/employee-management
cd employee-management
```

### 2️⃣ Install Dependencies

```bash
npm install
```

### 3️⃣ Install Required Packages

```bash
npm install axios bootstrap
```

### ▶️ Run the Application

```bash
npm run serve
```

Open in browser:  
`http://localhost:8080`

---

## 🌐 API Configuration

This project uses **MockAPI** as the backend.

**Example endpoint:**

```
https://69e856172f51b534be5fead9.mockapi.io/api/employees
```

**Employee Fields:**

- ID (auto‑generated)
- Name
- Designation
- Department
- Salary

---

## 🔄 CRUD Operations

| Operation | Method | Description             |
| --------- | ------ | ----------------------- |
| Create    | POST   | Add new employee        |
| Read      | GET    | Fetch all employees     |
| Update    | PUT    | Modify employee details |
| Delete    | DELETE | Remove employee         |

---

## 🎯 Key Concepts Used

- Vue Components (reusable structure)
- Two‑way Data Binding (`v-model`)
- Directives (`v-for`, `v-if`)
- Lifecycle Hook (`mounted()`)
- Axios for API calls
- Async operations handling

---

## 📸 Output

- Functional CRUD application
- Responsive layout
- Real-time updates from API

---
