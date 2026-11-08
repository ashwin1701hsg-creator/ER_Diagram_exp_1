# NAME : ASHWIN H
# REG  : 212225230025
# ER Diagram Workshop – Submission Template

## Objective

To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose

To gain hands-on experience in designing ER diagrams that represent database structures, including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

### Business Context

FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

### Requirements

- Members register with name, membership type, and start date.
- Each member can join multiple programs (Yoga, Zumba, Weight Training).
- Trainers are assigned to programs; a program may have multiple trainers.
- Members may book personal training sessions with trainers.
- Attendance is recorded for each session.
- Payments are tracked for memberships and sessions.

### ER Diagram

Paste or attach your ER diagram here.
![alt text](<exp 1 A image.png>)
![alt text](<exp 1 A img.jpeg>)
### 1. Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| MEMBER | Mem_id (PK), Name, Gender, Phone, Address | Member details |
| MEMBERSHIP | Id (PK), Type, Fee, Start_Date, Last_Date, Mem_id (FK) | Membership details |
| PAYMENT | Payment_Id (PK), Amount, Method, Status, Mem_id (FK) | Payment details |
| PROGRAM | Program_id (PK), Name, Type, Description, Duration | Fitness programs |
| TRAINER | Trainer_id (PK), Name, Specialization, Experience | Trainer details |
| SESSION | Session_id (PK), Date, Time, Duration, Location, Trainer_id (FK) | Training sessions |
| ATTENDANCE | Attendance_id (PK), Mem_id (FK), Session_id (FK), In_Time, Out_Time, Status | Attendance details |

### 2. Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| MEMBER – MEMBERSHIP | 1:N | Partial | Registers |
| MEMBER – PROGRAM | M:N | Partial | Joins programs |
| PROGRAM – TRAINER | M:N | Partial | Trainers conduct programs |
| MEMBER – SESSION | M:N | Partial | Books sessions |
| TRAINER – SESSION | 1:N | Total on session side | Conducts sessions |
| SESSION – ATTENDANCE | 1:N | Partial | Records attendance |
| MEMBER – ATTENDANCE | 1:N | Partial | Has attendance |
| MEMBER – PAYMENT | 1:N | Partial | Makes payments |

### 3. Assumptions

- Each member has a unique Member ID.
- Each trainer has a unique Trainer ID.
- Members can join multiple fitness programs.
- A program can have multiple trainers.
- Attendance is recorded for every member attending a session.
- Payments are recorded for memberships and training sessions.

---

# Scenario B: City Library Event & Book Lending System

### Business Context

The Central Library wants to manage book lending and cultural events.

### Requirements

- Members borrow books, with loan and return dates tracked.
- Each book has title, author, and category.
- The library organizes events; members can register.
- Each event has one or more speakers/authors.
- Rooms are booked for events and study.
- Overdue fines apply for late returns.

### ER Diagram

Paste or attach your ER diagram here.
![alt text](<exp 1 B image.png>) 
![alt text](<exp 1 B img.jpeg>)
### 1. Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| MEMBER | Member_id (PK), Name, Email, Phone, City, State, Pin_code | Member details |
| LIBRARY_EVENT | Event_id (PK), Event_Name, Event_Date, Event_Type, Time | Event details |
| SPEAKER | Speaker_id (PK), Name, Expertise | Speaker details |
| LOAN | Loan_id (PK), Member_id (FK), Book_id (FK), Loan_Date, Due_Date, Return_Date, Fine_Amount | Loan details |
| BOOK | Book_id (PK), Author, Category, Title | Book details |
| ROOM | Room_id (PK), Room_Name, Capacity | Room details |
| ROOM_BOOKING | ID (PK), Room_id (FK), Member_id (FK), Event_id (FK), Purpose, Date, Start_Time | Room booking details |

### 2. Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| MEMBER – LIBRARY_EVENT | M:N | Partial | Registers for events |
| LIBRARY_EVENT – SPEAKER | M:N | Total on event side | Has speakers |
| MEMBER – LOAN | 1:N | Partial | Borrows books |
| BOOK – LOAN | 1:N | Partial | Book loan records |
| LIBRARY_EVENT – ROOM | N:1 | Total on event side | Event booked in a room |
| ROOM – ROOM_BOOKING | 1:N | Partial | Has room bookings |
| MEMBER – ROOM_BOOKING | 1:N | Partial | Makes bookings |
| LIBRARY_EVENT – ROOM_BOOKING | 1:1 | Partial | Event booking |

### 3. Assumptions

- Each member has a unique Member ID.
- Each book has a unique Book ID.
- A member can borrow multiple books.
- A book can have multiple loan records over time.
- Members can register for multiple library events.
- Fines are charged for overdue books.
- Rooms are booked according to availability.

---

# Scenario C: Restaurant Table Reservation & Ordering

### Business Context

A popular restaurant wants to manage reservations, orders, and billing.

### Requirements

- Customers can reserve tables or walk in.
- Each reservation includes date, time, and number of guests.
- Customers place food orders linked to reservations.
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).
- Bills are generated per reservation, including food and service charges.
- Waiters are assigned to serve reservations.

### ER Diagram

Paste or attach your ER diagram here.
![alt text](<exp 1 C image.png>)
![alt text](<exp 1 C.jpeg>)
### 1. Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| CUSTOMER | Id (PK), Name, Email, Phone, Address, City, State, Pin_code | Customer details |
| RESERVATION | Id (PK), Customer_id (FK), Table_id (FK), Date, Time, Status, No_of_People | Reservation details |
| TABLE | Table_id (PK), Capacity, Status, Location | Table details |
| STAFF | Staff_id (PK), Name, Phone, Email, Role, Shift | Staff details |
| ORDER | Id (PK), Reservation_id (FK), Date, Status, Total_Amount | Order details |
| ORDER_ITEM | Id (PK), Order_id (FK), Item_id (FK), Quantity, Sub_Total, Price | Items in order |
| MENU | Item_id (PK), Item_Name, Category, Price, Description | Menu items |
| BILL | Bill_Id (PK), Reservation_id (FK), Date, Status, Total_Amount, Payment_Mode, Service_Charge | Bill details |

### 2. Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| CUSTOMER – RESERVATION | 1:N | Partial | Customer makes reservations |
| RESERVATION – TABLE | N:1 | Total on reservation side | Reservation is assigned a table |
| RESERVATION – ORDER | 1:N | Partial | Reservation has orders |
| ORDER – ORDER_ITEM | 1:N | Total on order side | Order contains items |
| ORDER_ITEM – MENU | N:1 | Total on order item side | Items refer to menu |
| RESERVATION – BILL | 1:1 | Partial | Reservation generates bill |
| STAFF – RESERVATION | 1:N | Partial | Staff serves reservations |

### 3. Assumptions

- Each customer has a unique Customer ID.
- Each table has a unique Table ID.
- Each reservation is assigned to one table.
- A customer can make multiple reservations.
- Each order contains one or more menu items.
- Each reservation generates one bill.
- Each reservation is handled by an assigned staff member.
- Walk-in customers can place orders without advance reservations.

---

# Instructions for Students

1. Complete all three scenarios (A, B, C).
2. Identify entities, relationships, and attributes for each scenario.
3. Draw ER diagrams using draw.io / diagrams.net or hand-draw and scan them.
4. Fill in all tables and assumptions for each scenario.
5. Export the completed Markdown (with diagrams) as a single PDF.
