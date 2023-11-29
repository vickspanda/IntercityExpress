# Intercity Express  

**This Repository contains both PART I and PART II of the Intercity Express Assignment**  
**_Name: Vikas Sharma_**  
**_Roll No.: 23112042_**  
**_Group No.: G10_**    

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

![er diagram](https://github.com/vickspanda/IntercityExpress/assets/116336028/2facb5fa-1866-4371-b757-6326681e6fff)


**For IntercityExpress Project, the Relational Schemas are as follows:**  

Note: Bold means Primary Key.  
     Itallic means Foreign Key.  

1.	train (**t_id**, capacity, milage)
2.	stand_by(_station_id_, _t_id_)
3.	route (**r_id**, r_name, distance, time_taken, operation_days, arrival_time, departure_time)
4.	connects (_r_id_, _start_station_, _end_station_)
5.	schedule (**s_id**,_ r_id_, _t_id_, actual_departure_time, actual_arrival_time, date, _driver_, _co_driver_)
6.	station (**station_id**, s_name)
7.	staff (**staff_id**, st_name, contact_no, address, rest_days)
8.	maintainance (**mt_id**, m_type)
9.	goes_through (_t_id_, _mt_id_, date)
10.	travel Agent (**ta_id**, ta_name, commission)
11.	ticket (**ticket_id**, date, time, price, _r_id_)
12.	booking (_ticket_id_, _ta_id_, _p_id_, discount, final_price)
13.	passenger(**p_id**, p_name, p_age)



To implement these Schemas. we need to follow the following commands in Mysql Command Line Client or Mysql can be accessed using Command Line Prompt after giving command "mysql -u root -p"  :

**Create the Database,**

_mysql> create database IntercityExpress;_

**Select the Database,**

_mysql> use intercityexpress;_


**Create table booking,**

_mysql> create table booking(_  
    _-> ticket_id varchar(10),_  
    _-> ta_id varchar(10),_  
    _-> p_id varchar(10),_  
    _-> discount int,_  
   _-> final_price);_  

**Load booking.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/booking.csv'  
    -> into table booking  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  
	
**Create table goes_through,**

_mysql> create table goes_through(  
    -> tid varchar(10),  
    -> mt_id varchar(10),  
    -> date DATE);_  

**Load goes_through.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/goes_through.csv'  
    -> into table goes_through  
    -> fields terminated  by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**Create table passenger,**

_mysql> create table passenger(  
    -> p_id varchar(10) primary key,  
    -> p_name varchar(50),  
    -> p_age int);_  

**Load passenger.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/passenger.csv'  
    -> into table passenger  
    -> fields terminated  by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**create table route,**   

_mysql> create table route(  
    -> r_id varchar(10) primary key,  
    -> r_name varchar(50),  
    -> distance int,  
    -> time_taken TIME,  
    -> operation_days varchar(50),  
    -> departure_time TIME,  
    -> arrival_time TIME);;_  

 **Load route.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/route.csv'  
    -> into table route  
    -> fields terminated  by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**create table schedule,**  

_mysql> create table schedule(  
    -> s_id varchar(10) primary key,  
    -> r_id varchar(10),  
    -> t_id varchar(10),  
    -> actual_departure_time TIME,  
    -> actual_arrival_time TIME,  
    -> date DATE,  
    -> driver varchar(10),  
    -> codriver varchar(10));_  

**Load schedule.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/schedule.csv'  
    -> into table schedule  
    -> fields terminated  by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  
	
**create table staff,**

_mysql> create table staff(  
    -> staff_id varchar(10) primary key,  
    -> staff_name varchar(50),  
    -> contact_no int,  
    -> address varchar(50),  
    -> rest_days varchar(50));_  

**Load staff.csv file into table staff,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/staff.csv'  
    -> into table staff  
    -> fields terminated  by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**create table stand_by,**

_mysql> create table stand_by(  
    -> station_id varchar(10),  
    -> t_id varchar(10));_  


**Load stand_by.csv file into table stand_by,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/standby.csv'  
    -> into table stand_by  
    -> fields terminated  by ','  
    -> lines terminated by '\r\n'  
    -> ignore 1 lines;_  


**create table station,**

_mysql> create table station(  
    -> station_id varchar(10) primary key,  
    -> s_name varchar(50));_  

**Load station.csv into table station,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/station.csv'  
    -> into table station  
    -> fields terminated  by ','  
    -> lines terminated by '\r\n'  
    -> ignore 1 lines;_  

**create table ticket,**

_mysql> create table ticket(  
    -> ticket_id varchar(10) primary key,  
    -> date DATE,  
    -> time TIME,  
    -> price int,  
    -> r_id varchar(10));_  


**Load ticket.csv into table ticket,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/ticket.csv'  
    -> into table ticket  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  

**create table train,**

_mysql> create table train(  
    -> t_id varchar(10) primary key,  
    -> capacity int,  
    -> milage int);_  


**Load train.csv into table train,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/train.csv'  
    -> into table train  
    -> fields terminated  by ','  
    -> lines terminated by '\r\n'  
    -> ignore 1 lines;_  

**Create table travel_agent,**

_mysql> create table travel_agent(  
    -> ta_id  varchar(10) primary  key,  
    -> ta_name  varchar(50),  
    -> commission int);_  

**Load travel_agent.csv into table travel_agent,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/travel_agent.csv'  
    -> into table travel_agent  
    -> fields terminated  by ','  
    -> lines terminated by '\r\n'  
    -> ignore 1 lines;;_  

 **Create table connect,**

_mysql> create table connect(  
    -> r_id varchar(10),  
    -> start_station varchar(10),  
    -> end_station varchar(10));_  

**Load connects.csv file,**

_mysql> load data infile 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/connects.csv'  
    -> into table connect  
    -> fields terminated by ','  
    -> lines terminated by '\n'  
    -> ignore 1 lines;_  


**Now adding Foreign Key Constraints to the all tables as per the relational schemas by following these commands,**

_**For table booking:**_  
_mysql> alter table booking add foreign key (ticket_id) references ticket(ticket_id);_  

_mysql> alter table booking add foreign key (ta_id) references travel_agent(ta_id);_  

_mysql> alter table booking add foreign key (p_id) references passenger(p_id);_    

_**For table goes_through:**_  
_mysql> alter table goes_through add foreign key (t_id) references train(t_id);_  

_mysql> alter table goes_through add foreign key (mt_id) references maintenance(mt_id); _  

_**For table connect:**_  
_mysql> alter table connect add foreign key (r_id) references route(r_id);_  

_mysql> alter table connect add foreign key (start_station) references station(station_id);_  

_mysql> alter table connect add foreign key (end_station) references station(station_id); _  

_**For table schedule:**_  
_mysql> alter table schedule add foreign key (r_id) references route(r_id);_  

_mysql> alter table schedule add foreign key (t_id) references train(t_id);_  

_mysql> alter table schedule add foreign key (driver) references staff(staff_id);_  

_mysql> alter table schedule add foreign key (codriver) references staff(staff_id);_   

_**For table stand_by:**_  
_mysql> alter table stand_by add foreign key (station_id) references station(station_id);_  

_mysql> alter table stand_by add foreign key (t_id) references train(t_id);_  

_**For table ticket:**_  
_mysql> alter table ticket add foreign key (r_id) references route(r_id);_  


# IntercityExpress PART II

_I have Completed the PART II of the Assignment by solving Set C of the Assignment_  

**_For Question No. 1 of Set C:_**  
_mysql> SELECT *  
    -> FROM Train  
    -> WHERE tid NOT IN (  
    -> SELECT DISTINCT T.tid  
    -> FROM Train T  
    -> LEFT JOIN Schedule S ON T.tid = S.tid  
    -> WHERE S.date = '2023-10-10'  
    -> );_  
    
**_For Question No. 2 of Set C:_**  
_mysql> SELECT T.*, COUNT(*) AS MonthlySeatsSold  
    -> FROM Train T  
    -> INNER JOIN Schedule S ON T.tid = S.tid  
    -> INNER JOIN Route R ON S.rid = R.rid  
    -> INNER JOIN Booking B ON S.sid = B.sid  
    -> WHERE R.start_station = 'Dharwad' AND R.end_station = 'Bengaluru'  
    -> AND B.date BETWEEN '2023-10-01' AND '2023-10-31'  
    -> GROUP BY T.tid  
    -> ORDER BY MonthlySeatsSold ASC;_  

**_For Question No. 3 of Set C:_**  
_mysql> SELECT R.*, COUNT(*) AS NumBookings  
    -> FROM Route R  
    -> INNER JOIN Schedule S ON R.rid = S.rid  
    -> INNER JOIN Train T ON S.tid = T.tid  
    -> INNER JOIN Booking B  ON T.tid = B.tid  
    -> WHERE T.tid IN (  
    -> SELECT tid  
    -> FROM Train  
    -> WHERE T.tid = B.tid  
    -> )  
    -> GROUP BY R.rid  
    -> ORDER BY NumBookings DESC  
    -> LIMIT 1;_  

**_For Question No. 4 of Set C:_**  
_mysql> SELECT P.*  
    -> FROM passenger P  
    -> WHERE P.pid IN (  
    -> SELECT B.pid  
    -> FROM booking B  
    -> INNER JOIN schedule S ON B.sid = S.sid  
    -> INNER JOIN train T ON S.tid = T.tid  
    -> WHERE T.tid = B.tid  
    -> GROUP BY B.pid  
    -> HAVING COUNT(*) >= 3  
    -> );_  

**_End of the Assignment_**
