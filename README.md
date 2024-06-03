Project : Gym Management System

Description :  In this project, I have used the Gym Present in EDC Block of Sukkur IBA University. This gym management system firstly asks the username and password as per the if else logic.
User Name : root         	Password : root
If the correct password is entered, the login window will dispose and a new Frame (Main Page ) will be opened that will give the choice to open a table from the tables:
1)	Members : Members Enrolled
2)	MemberShips : MemberShips Available
3)	Trainers : Trainer Information

Click Either button, The new Frame will be opened with respect to the table connected but it will not dispose the Main Page.
 Each Frame consists of the Table and data related the database table. Buttons to add, edit, delete and search data are available.
 In each Frame, Header is set with IBA and logo  and respective heading.
Every Frame consists of the components and their respective labels in accordance with their repective Tables.
All the necessary things like GUI, Event-handling and Databases are included.

Database Description:
1)	Database used : MySQL.
2)	Database Type : Relational Database
3)	Database Name : GymManagement 
4)	Number of Tables : 3
5)	Table Names : Trainer, member , membershipplan
6)	Trainer fields : TrainerID , TrainerName, TrainerAge, TrainerShift, TrainerSalary 
7)	Member fields : MemID, MemName, MemAge,MemberShipID,FeesStatus,TrainerID,Shift
8)	Membershipplan fields : MemberShipID, MemberShipName, Cardio, Bodybuilding, PersonalTrainer, MemberShipFees
9)	Relations : Each member is assigned a trainer with the help of trainer ID as the foreign key. This means that there is a number of members connected that workout under a trainer. Each Trainer is connected to a membership through membershipID as the foreign key. This means that Each membership is subscriber by a certain number of members. You can not delete record from membership and trainer table if they are connected with any member. 


MySQL Code :
Note : I had studied Relational Database Management system in class 11th . So due to that I am Familiar to many of the RDBMS concepts. However, I had forgetten a little bit syntax as I do not have proper command over SQL. Due to that reason I have took some help from ChatGPT in assisting my database SQL code. Especially in making relational tables. However I still have created tables, their fields and Keys myself.


Code : 
For Database :  CREATE DATABASE GymManagement
CREATE TABLE Trainer (
    TrainerID INT PRIMARY KEY,
    TrainerName VARCHAR(30),
    TrainerAge INT,
    TrainerShift ENUM('Morning', 'Afternoon', 'Evening', 'Night'),
    TrainerSalary DOUBLE
);

CREATE TABLE MemberShipPlan (
    MemberShipID INT PRIMARY KEY,
    MemberShipName VARCHAR(50),
    Cardio BOOLEAN,
    Bodybuilding BOOLEAN,
    PersonalTrainer BOOLEAN,
    MemberShipFees DOUBLE
);

CREATE TABLE Member (
    MemID INT PRIMARY KEY,
    MemName VARCHAR(50),
    MemAge INT,
    MembershipID INT,
    FeesStatus BOOLEAN,
    TrainerID INT,
    Shift ENUM('Morning', 'Afternoon', 'Evening', 'Night'),
    FOREIGN KEY (TrainerID) REFERENCES Trainer(TrainerID),
    FOREIGN KEY (MembershipID) REFERENCES MemberShipPlan(MemberShipID)
);
Trainer's Shift
DELIMITER $$
CREATE TRIGGER SetMemberShift
BEFORE INSERT ON Member
FOR EACH ROW
BEGIN
    DECLARE trainer_shift ENUM('Morning', 'Afternoon', 'Evening', 'Night');
    SELECT TrainerShift INTO trainer_shift FROM Trainer WHERE TrainerID = NEW.TrainerID;
    SET NEW.Shift = trainer_shift;
END $$
DELIMITER ;

Classes and interfaces :

•	Main class
•	Login class
•	Trainer class
•	Member Class
•	MemberShip Class
•	JFrame as inheritance
•	ActionListener as interface

Packages Used : 
•	javax.swing.*;
•	javax.swing.table.DefaultTableModel;
•	java.awt.*;
•	java.awt.event.ActionEvent;
•	java.awt.event.ActionListener;
•	java.io.File;
•	java.sql.*;
•	java.util.Vector;



 

