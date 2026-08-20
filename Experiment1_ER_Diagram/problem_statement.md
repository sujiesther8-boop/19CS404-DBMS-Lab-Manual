# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="971" height="736" alt="Screenshot 2026-08-20 184337" src="https://github.com/user-attachments/assets/43911b5d-403e-4482-9b34-8219b01d4861" />


### Entities and Attributes
<img width="1002" height="480" alt="Screenshot 2026-08-20 185018" src="https://github.com/user-attachments/assets/d3324117-b7ee-4c6a-babf-906a30bd5965" />

### Relationships and Constraints
<img width="988" height="447" alt="Screenshot 2026-08-20 185030" src="https://github.com/user-attachments/assets/a65c2756-4801-43a3-a0fc-ee99af8c792a" />


### Assumptions
A member can join multiple programs.
Trainers can be assigned to multiple programs.
Personal training sessions always involve one trainer and one member.-

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="960" height="757" alt="Screenshot 2026-08-20 184402" src="https://github.com/user-attachments/assets/c9cabf65-de8a-46bd-947c-69675c47d048" />

### Entities and Attributes
<img width="888" height="435" alt="Screenshot 2026-08-20 185045" src="https://github.com/user-attachments/assets/dd39e5ad-78c2-4e63-bb0b-47cb6e6a508c" />

### Relationships and Constraints
<img width="882" height="580" alt="Screenshot 2026-08-20 185053" src="https://github.com/user-attachments/assets/3e88e140-9173-4386-952b-e6eec827ec5d" />

### Assumptions
The authentication system maintains unique Login_IDs and corresponding usernames/passwords for authorized users.
A book is assumed to have one primary author and one publisher in this model.
A reader's basic details such as name, email, phone number, and address are stored in the system.
Staff members can manage or keep track of readers, books, and reports.

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="996" height="791" alt="Screenshot 2026-08-20 184424" src="https://github.com/user-attachments/assets/4de51327-31e9-4f0a-b75c-67e2f5f599d8" />


### Entities and Attributes
<img width="937" height="407" alt="Screenshot 2026-08-20 185102" src="https://github.com/user-attachments/assets/ce83cc36-2e54-46fe-8bf0-bbe3cd691d77" />


### Relationships and Constraints
<img width="890" height="547" alt="Screenshot 2026-08-20 185111" src="https://github.com/user-attachments/assets/6d502fe3-3e3a-4f3d-9a88-53192f69cbaa" />


### Assumptions
Each customer is uniquely identified by Customer_ID.
A customer can make multiple reservations, while each reservation belongs to one customer.
Each reservation has a unique Res_ID and stores the reservation date, time, type, and number of guests.
A restaurant can have multiple tables, with each table identified by a unique Table_ID.
A table can be reserved for different reservations at different times, but it should not be double-booked for the same time slot.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
