# Pets Database
Develop SQL statements required to manipulate a database of pets<br>

[data types](https://www.w3schools.com/sql/sql_datatypes.asp),
[hsqldb](http://hsqldb.org/),
[sql](https://www.w3schools.com/sql/),
[uuid](https://www.uuidgenerator.net/)

## Pre-requirements
* Ensure the Eclipse IDE has Maven by looking for M2E from Help About ([details](https://www.vogella.com/tutorials/EclipseMaven/article.html))
* Install `DBViewer Plugin 1.2.2.v20101009` by ZIGEN from the Eclipse IDE marketplace
* Import into Eclipse as Git with smart import (accepting all defaults in wizard)
* Let the IDE finish building dependencies before proceeding (see bottom right of Eclipse)

## Steps
* Run the PetsDB app to start the database
* Develop Pets-based SQL statements
* Switch to DBViewer perspective to test
* Stop the PetsDB app to shutdown database
* Ensure SQL documented within this README
* Push update README back to forked GitHub

## Bonus
* Create another related table with SQL

## Database Schema

**Animal table**
 - Hunger INT
 - Id CHAR(36)
 - Name VARCHAR(100)
 - OwnerId CHAR(36)
 - Species CHAR(1)

**Owner table**
 - Id CHAR(36)
 - Name VARCHAR(100)
 - Town VARCHAR(100)
 
**To create the Owner table**<br>
CREATE TABLE Owners (Id CHAR(36), Name VARCHAR(100), Town VARCHAR(100), PRIMARY KEY (Id))

**To create the Animal table**<br>
CREATE TABLE Animals (Id CHAR(36), Hunger INT, Name VARCHAR(100), OwnerId CHAR(36), Species CHAR(1), PRIMARY KEY(Id), FOREIGN KEY (OwnerId) REFERENCES Owners(Id)) 

**To insert a new Owner row**<br>
INSERT INTO Owners (Id, Name, Town) VALUES ('291fb728-997c-47d6-bcc6-5fba93b1ad63', 'Annie Apple', 'Preston')

**To insert a new Cat row**<br>
INSERT INTO Animals (Id, Hunger, Name, OwnerId, Species) VALUES ('b5a8fd0c-8139-45f0-ad05-ecca48de5af3', 50, 'Hubert', '291fb728-997c-47d6-bcc6-5fba93b1ad63', 'C')

**To insert a new Dog row**<br>
INSERT INTO Animals (Id, Hunger, Name, OwnerId, Species) VALUES ('6f64be02-371b-4ccd-b434-46f86cc4ec82', 10, 'Fenton', '291fb728-997c-47d6-bcc6-5fba93b1ad63', 'D')

**To query an animal**<br>
SELECT * FROM Animals WHERE Species = 'C'

**To query all pets for an owner**<br>
SELECT animals.Name FROM Animals animals, Owners owners WHERE owners.Name = 'Annie Apple' AND animals.OwnerId = owners.id