# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

### Name : SIVAHARIBALAN K
### Reg. No.: 212224220103
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

<img width="908" height="687" alt="image" src="https://github.com/user-attachments/assets/76fb0969-7bdc-4853-ba3b-65dca62ce2fc" />


### Entities and Attributes

Member: Member_ID, Name, Membership_Type, Start_Date

Trainer: Trainer_ID, Trainer_Name

Programme: Programme_ID, Programme_Name, Programme_Slot

Payment: Payment_ID, Membership, Date, Member_ID

Session: Session_ID, Session_Slot, Session_Date, Trainer_ID, Member_ID

Attendance: Attendance_ID, Time, Status, Percentage, Member_ID

### Relationships and Constraints

makes (Member → Payment) (Cardinality: 1:N, Participation: Partial)
A member can make multiple payments; each payment belongs to one member.

joins (Member → Programme) (Cardinality: N:M, Participation: Partial)
A member can join many programmes; a programme may include many members.

conducts (Trainer → Programme) (Cardinality: 1:N, Participation: Partial)
Each trainer conducts multiple programmes, but every programme is handled by one trainer.

Class (Member/Trainer → Session) (Cardinality: N:M, Participation: Partial)
Sessions are attended by multiple members and managed by multiple trainers.

---

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

<img width="1307" height="794" alt="image" src="https://github.com/user-attachments/assets/5a7f2190-bb2f-47c5-8bca-23350605f08f" />

### Entities and Attributes
Member: Member_ID, Name, Address, Email, Phone

Book: Book_ID, Title, Author

Loan: Loan_ID, Loan_Date, Return_Date, Fine, Member_ID, Book_ID

Event: Event_ID, Event_Name, Event_Type, Event_Date

Room: Room_ID, Room_Name, Type, Capacity

Event_Registration: Registration_ID, Date_of_Registration, Event_ID, Member_ID

### Relationships and Constraints

Receive (Member → Loan) (Cardinality: 1:N, Participation: Partial)
A member can receive many loans; each loan is issued to one member.

Held_In (Event → Room) (Cardinality: M:N, Participation: Partial)
An event can be held in multiple rooms; each room can host multiple events.

Registers (Member → Event) (Cardinality: N:M, Participation: Partial)
A member can register for multiple events; an event can have many members.

Event_Speaker (SpeakerAuthor → Event) (Cardinality: M:N, Participation: Partial)
Speakers or authors can join multiple events; each event can feature many speakers.

---

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

<img width="1305" height="818" alt="image" src="https://github.com/user-attachments/assets/2a6027cf-9b50-484d-b505-0ed37a548a01" />

### Entities and Attributes

Customer: Customer_ID, Name

Reservation: Reservation_ID, Date, Time, No_of_Guests, Customer_ID, Table_ID

Table: Table_ID, Capacity

Dish: Dish_ID, Name, Price, Category_ID

Category: Category_ID, Name


### Relationships and Constraints

TO (Customer → Reservation) (Cardinality: 1:N, Participation: Partial)
Each customer can make many reservations, and each reservation belongs to one customer.

FOR (Reservation → Table) (Cardinality: 1:N, Participation: Partial)
A reservation may include one or more tables; each table may be reserved multiple times.

SELECT (Category → Dish) (Cardinality: 1:N, Participation: Total)
A category can contain many dishes; each dish belongs to one category.

TOTAL (Reservation → Bill) (Cardinality: 1:1, Participation: Total for Bill)
Every reservation generates one bill.

---

### Result

The combined ER diagram effectively represents entities and relationships of the restaurant, fitness club, and library systems. It clearly captures interactions like reservations, sessions, and book lending, ensuring smooth data flow and efficient system management.
