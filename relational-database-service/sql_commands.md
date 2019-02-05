## SQL Commands Used in the Live AWS Environment:

### Inside the primary database

CREATE DATABASE ratings;
USE ratings;
SELECT DATABASE();
SHOW TABLES;

CREATE TABLE ratings (author VARCHAR(20), rating TINYINT, timerated DATETIME);

SHOW TABLES;

DESCRIBE ratings;

INSERT INTO ratings ( author, rating, timerated )
   VALUES
   ( "Tia Williams", 10, "2018-06-26 10:06:47"),
   ( "Adrian Cantril", 10, "2018-06-23 10:06:27");

### Inside the Read Replica

SHOW DATABASES;
USE ratings;
SELECT DATABASE();
#### This command should fail:
INSERT INTO ratings ( author, rating, timerated )
   VALUES
   ( "Craig", 10, "2018-06-26 10:06:47"),
   ( "Mark", 10, "2018-06-23 10:06:27");


### Inside the (previously) Read Replica after it has been promoted to a standalone RDS instance. 

INSERT INTO ratings ( author, rating, timerated )
   VALUES
   ( "Craig", 10, "2018-06-26 10:06:47"),
   ( "Mark", 10, "2018-06-23 10:06:27");
SELECT * FROM ratings LIMIT 2;
