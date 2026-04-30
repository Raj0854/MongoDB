```yml
// create and use database
use raj:
// show databases
show dbs;
// create a collection
db.createCollection("employee_info");
// insert data at one 
db.employee_info.insertOne({Name:"Raj Gupta",Age:22,city;"mumbai"});
// insert data at many 
db.employee_info.insertMany([
  {Name:"Dinesh Kartik",Age:35,city:"Bengluru", salary:18000,dept:"management"},
  {Name:"Rohit sharma",Age:42,city:"mumbai", salary:25000,dept:"IT"}
])
// show data
db.employee_info.find();

