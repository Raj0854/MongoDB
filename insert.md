// create and use database
use raj:
// show databases
show dbs;
// create a collection
db.createCollection("employee_info");
// insert data at one 
db.employee_info.insertOne({Name:"Raj Gupta",Age:22,city;"mumbai"});
