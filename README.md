
# 📚 Library Management System

A **Library Management System** designed to automate book lending and member operations for a city library in Belagavi. This system allows library administrators to manage books, CDs, and DVDs while providing a seamless borrowing experience for members.

### 🎯 Objectives:
✔️ Efficient information organization for library resources  
✔️ Easy user registration and borrowing tracking  
✔️ Automated fine calculation for overdue items  
✔️ User-friendly search functionality  

---

## 🛠 Features

🔹 **Member Functions:**  
- Search books by title, author, or category  
- View availability and borrow books/CDs/DVDs  
- Check due dates & return items  
- Avoid fines by returning items on time  

🔹 **Automated Fine System:**  
- ₹10 per day for overdue books  
- ₹20 per day for overdue CDs  
- ₹30 per day for overdue DVDs  

---

## 🗄 Database Design

### 📌 **Entities & Relationships**
- **BOOK (book_id, name, author, category, copies_available)**  
- **CD (cd_id, name, category, copies_available)**  
- **DVD (dvd_id, name, category, copies_available)**  
- **MEMBER (m_id, name, gender, phone_no)**  
- **B_INFO (book_id, m_id, issue_date, due_date, return_date)**  
- **CD_INFO (cd_id, m_id, issue_date, due_date, return_date)**  
- **DVD_INFO (dvd_id, m_id, issue_date, due_date, return_date)**  

### 📌 **E-R Diagram**
Refer from above DB report 

---

## 🚀 Installation & Setup

### 📌 Clone the Repository
```bash
git clone https://github.com/akhileshj2004/sqlLibrarysystem.git
```

### 📌 Set Up the Database
```sql
CREATE DATABASE LibraryDB;
USE LibraryDB;

CREATE TABLE BOOK (
    book_id INT PRIMARY KEY,
    name VARCHAR(255),
    author VARCHAR(255),
    category VARCHAR(100),
    copies_available INT
);
-- Repeat for other tables...
```

## 📊 SQL Queries

### 📌 Retrieve members and their borrowed books:
```sql
SELECT m.name, b.name, bi.issue_date, bi.due_date, bi.return_date
FROM MEMBER m
JOIN B_INFO bi ON m.m_id = bi.m_id
JOIN BOOK b ON b.book_id = bi.book_id;
```

### 📌 Retrieve books borrowed by male members:
```sql
SELECT m.name, b.name
FROM MEMBER m
JOIN B_INFO bi ON m.m_id = bi.m_id
JOIN BOOK b ON b.book_id = bi.book_id
WHERE m.gender = 'M';
```

### 📌 Find books that have been borrowed more than once:
```sql
SELECT book_name FROM BOOK
WHERE book_id IN (
    SELECT book_id FROM B_INFO GROUP BY book_id HAVING COUNT(*) > 1
);
```

*(More queries can be added as needed)*

---

## 👥 Contributors

- **Abhilash B**  
- **Aditi J**  
- **Akhilesh J**  

---

📢 _For any queries or contributions, feel free to open an issue or create a pull request!_ 🎉
```
