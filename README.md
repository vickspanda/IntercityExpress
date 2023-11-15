# IntercityExpress PART I

**The PART I Project has been done by G10**  
**_Vikas Sharma (23112042)_**  
**_Rugved Ajit Patil (23112026)_**  
**_Onkar Deepak Gangurde (23112010)_**  

**The Distribution for the PART I is as Follows:**  
_ER Diagram was initially drawn by each member of the group and after the common discussion we concluded to the attached ER Diagram below:_  

_The Relational Schemas was designed by three of us on the same day when we finalised the ER Diagram_  

_And the creation of database was also performed by three of us individually on our personnel computers and after getting the errors we jot them down and discussed them on another group meet_  

_In our project, we have 12 tables, for them each of us selected four tables to get the sample data prepared for database_  

_For PART II of the Project, We have distributed the Sets as follows:_  
_Set A: Rugved Ajit Patil (23112026)_  
_Set B: Onkar Deepak Gangurde (23112010)_  
_Set C: Vikas Sharma (23112042)_  


**For IntercityExpress Project, the ER Diagram is as follows:**

Note: This ER Diagram is made using Lucidchart and paint.

![ER_diagram](https://github.com/vickspanda/IntercityExpress/assets/116336028/0a62ee86-0335-4cd6-9abf-25b6e7194bfa)

**For IntercityExpress Project, the Relational Schemas are as follows:**  

Note: Bold means Primary Key.  
     Itallic means Foreign Key.  

1.	train (**tid**, capacity, milage, _mid_)  
2.	standby (_station_id_, _tid_)  
3.	route ( **r_id**, r_name, distance, time_taken, operation_days, _start_station_, _end_station_, _driver_, _co_driver_)  
4.	schedule (**sid**, _r_id_,_ tid_, departure_time, arrival_time, date)  
5.	station (**station_id**, _sid_, s_name, actual_departure, actual_arrival)  
6.	staff (**staff_id**, st_name, contact no, address, rest_day)  
7.	maintenance (**mid**, _tid_, m_type, date)  
8.	travel_agent ( **ta_id**, ta_name, commission)  
9.	ticket (**ticket_id**, date, time, price,_ rid_)  
10.	booking (_tid_, _ticket_id_, _ta_id_, _p_id_, discount, final_price)  
11.	passenger (**p_id**, p_name, p_age)
12.	daily_services( _sid, r_id_)


To implement these Schemas. we need to follow the following commands in Mysql Command Line Client or Mysql can be accessed using Command Line Prompt after giving command "mysql -u root -p"  :

**Create the Database,**

_mysql> create database IntercityExpress;_

**Select the Database,**

_mysql> use intercityexpress;_


**Create table train,**

_mysql> create table train (tid varchar(10) primary key, capacity int, milage varchar(10), mid varchar(10));_

**Load train.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/train.csv'  
    -> into table train  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  
	
**Create table standby,**

_mysql> CREATE TABLE standby (  
    ->     station_id varchar(10),  
    ->     tid varchar(10),   
    -> );_  

**Load route.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/standby.csv'  
    -> into table standby  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**Create table route,**

_mysql> CREATE TABLE route (  
    ->     r_id varchar(10) primary key,  
    ->     r_name varchar(50),  
    ->     distance int,  
    ->     time_taken TIME,  
    ->     operation_days varchar(100),  
    ->     start_station varchar(20),  
    ->     end_station varchar(20),  
    ->     driver varchar(20),  
    ->     co_driver varchar(20)  
    -> );_  

**Load route.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/route.csv'  
    -> into table route  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**create table schedule,**   

_mysql> create table schedule(  
    -> sid varchar(50) primary key,  
    -> r_id varchar(50),  
    -> tid varchar(50),  
    -> departure_time time,  
    -> arrival_time time,  
    -> date DATE  
    -> );_  

 **Load schedule.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/schedule.csv'  
    -> into table schedule    
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**create table station,**  

_mysql> create table station(  
    -> station_id varchar(50) primary key,  
    -> sid varchar(50),  
    -> s_name varchar(50),  
    -> actual_departure time,  
    -> actual_arrival time);_  

**Load station.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/station.csv'  
    -> into table station  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  
	
**create table staff,**

_mysql> create table staff(  
    -> staff_id varchar(10) primary key,  
    -> st_name varchar(30),  
    -> contact_no bigint,  
    -> address varchar(200),  
    -> rest_day varchar(100)  
    -> );_  

**Load staff.csv file into table staff,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/staff.csv'  
    -> into table staff  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**create table maintainance,**

_mysql> create table maintainance(  
    -> mid varchar(10) primary key,  
    -> tid varchar(10),  
    -> m_type varchar(40),  
    -> date DATE  
    -> );_  


**Load staff.csv file into table maintenance,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/maintenance.csv'  
    -> into table maintenance  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  


**create table travel_agent,**

_mysql> create table travel_agent(  
    -> ta_id varchar(10) primary key,  
    -> ta_name varchar(30),  
    -> commission int  
    -> );_  

**Load travel_agent.csv into table travel_agent,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/travel_agent.csv'  
    -> into table travel_agent  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**create table ticket,**

_mysql> create table ticket(  
    -> ticket_id varchar(20) primary key,  
    -> date DATE,  
    -> time TIME,  
    -> price INT, 
    -> rid varchar(10)  
    -> );_  


**Load ticket.csv into table ticket,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/ticket.csv'  
    -> into table ticket  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**create table booking,**

_mysql> create table booking(  
    -> tid varchar(10),  
    -> ticket_id varchar(20),  
    -> ta_id varchar(10),  
    -> p_id varchar(10),  
    -> discount int,  
    -> final_price int  
    -> );_  


**Load booking.csv into table booking,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/booking.csv'  
    -> into table booking  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**Create table Passenger,**

_mysql> create table passenger(  
    -> p_id varchar(10) primary key,  
    -> p_name varchar(40),  
    -> p_age int  
    -> );_  

**Load passenger.csv into table passenger,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/passenger.csv'  
    -> into table passenger  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

 **Create table daily_service,**

_mysql> CREATE TABLE daily_service (  
    ->     sid varchar(10),  
    ->     r_id varchar(10),  
    ->     staff_id varchar(10),
    ->	   date DATE,
    -> );_  

**Load daily_service.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/daily_service.csv'  
    -> into table daily_service  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  


**Now adding Foreign Key Constraints to the all tables as per the relational schemas by following these commands,**

_**For table booking:**_  
_mysql> alter table booking add foreign key (t_id) references train(t_id);_  

_mysql> alter table booking add foreign key (ticket_id) references ticket(ticket_id);_  

_mysql> alter table booking add foreign key (ta_id) references travel_agent(ta_id);_  

_mysql> alter table booking add foreign key (pid) references passenger(pid);_  

_**For table daily_service:**_  
_mysql> alter table daily_service add foreign key (sid) references schedule(sid);_  

_mysql> alter table daily_service add foreign key (rid) references route(rid);_  

_mysql> alter table daily_service add foreign key (staff_id) references staff(staff_id);_  

_**For table maintenance:**_  
_mysql> alter table maintenance add foreign key (tid) references train(tid);_  

_**For table route:**_  
_mysql> alter table route add foreign key (driver) references staff(staff_id);_  

_mysql> alter table route add foreign key (co_driver) references staff(staff_id);_  

_mysql> alter table route add foreign key (start_station) references station(station_id);_  

_mysql> alter table route add foreign key (end_station) references station(station_id);_  

_**For table schedule:**_  
_mysql> alter table schedule add foreign key (rid) references route(rid);_  

_mysql> alter table schedule add foreign key (tid) references train(tid);_  

_**For table station:**_  
_mysql> alter table station add foreign key (sid) references schedule(sid);_  

_**For table ticket:**_  
_mysql> alter table ticket add foreign key (rid) references route(rid);_  

_**For table train:**_
_mysql> alter table train add foreign key (mid) references maintenance(mid);_  

_**For table standby:**_  
_mysql> alter table ticket add foreign key (station_id) references station(station_id);_  

_mysql> alter table ticket add foreign key (tid) references train(tid);_  

