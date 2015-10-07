1. What's the difference between a left and inner join?
  * __INNER JOIN__ gets all records from one table that have some related entry in a second table
  * __LEFT JOIN__ gets all records from the LEFT linked table but if you have selected some columns from the RIGHT table, if there is no related records, these columns will contain NULL
  * __RIGHT JOIN__ is like the above but gets all records in the RIGHT table
  * __FULL JOIN__ gets all records from both tables and puts NULL in the columns where related records do not exist in the opposite table
  
 > see [codeproject](http://www.codeproject.com/Articles/33052/Visual-Representation-of-SQL-Joins), [stackoverflow](http://stackoverflow.com/a/406333)
  
2. Why are transactions ACID?
  * __Atomicity__ requires that each transaction be "all or nothing"
  * __Consistency__ ensures that any transaction will bring the database from one valid state to another
  * __Isolation__ means that one transaction cannot read data from another transaction that is not yet completed
  * __Durability__ means that once a transaction has been committed, it will remain so, even in the event of power loss, crashes, or errors 
  
 > see [wiki](https://en.wikipedia.org/wiki/ACID), [stackoverflow](http://stackoverflow.com/a/3740307)
  
3. How is a database index implemented?
  
  Creating an index on a field in a table creates another data structure which holds the field value, and pointer to the record it relates to. This index structure is then sorted, allowing Binary Searches to be performed on it
  
 > see [stackoverflow](http://stackoverflow.com/a/1130), [sql.ru](http://www.sql.ru/articles/mssql/03013101indexes.shtml)
  
4. Transaction isolation levels
  * __READ UNCOMMITTED__ - no lock on table. You can read data in the table while writing on it. 
  * __READ COMMITTED__ - lock on committed data. You can read the data that was only commited. 
  * __REPEATABLE READ__ - lock on block of sql. This is the default isolation level for InnoDB
  * __SERIALIZABLE__ - lock on full table
  
  > see 
[stackoverflow](http://stackoverflow.com/questions/16162357/transaction-isolation-levels-relation-with-locks-on-table), [stackoverflow](http://stackoverflow.com/questions/4034976/difference-between-read-commit-and-repeatable-read), [mysql](https://dev.mysql.com/doc/refman/5.0/en/set-transaction.html)
  
5. 
