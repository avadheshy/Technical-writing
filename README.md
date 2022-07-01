# Introduction to database
## 1. ACID
ACID is the property of the transaction. A transaction is a set of logically related operations. It is important to ensure that the database remains consistent before and after the transaction. To ensure the consistency of the database, certain properties are followed by all the transactions occurring in the system. These properties are called ACID Properties of a transaction. These are as follows:
### 1.1 Atomicity
This property ensures that either the transaction occurs completely or it does not occur at all.
In other words, it ensures that no transaction occurs partially. That is why it is also referred to as all or nothing rule. It is the responsibility of the Transaction Control Manager to ensure the atomicity of the transactions.
### 1.2 Consistency
This property ensures that integrity constraints are maintained. In other words, it ensures that the database remains consistent before and after the transaction. It is the responsibility of DBMS and application programmer to ensure consistency of the database.
### 1.3 Isolation
This property ensures that multiple transactions can occur simultaneously without causing any inconsistency.
During execution, each transaction feels as if it is getting executed alone in the system.
A transaction does not realize that there are other transactions as well getting executed parallely.
Changes made by a transaction becomes visible to other transactions only after they are written in the memory.
The resultant state of the system after executing all the transactions is same as the state that would be achieved if the transactions were executed serially one after the other.
It is the responsibility of concurrency control manager to ensure isolation for all the transactions.
### 1.4 Durability 
This property ensures that all the changes made by a transaction after its successful execution are written successfully to the disk.
It also ensures that these changes exist permanently and are never lost even if there occurs a failure of any kind. It is the responsibility of recovery manager to ensure durability in the database.
## 2. CAP Theorem
The three letters in CAP refer to three desirable properties of distributed systems with replicated data: consistency (among replicated copies), availability (of the system for read and write operations) and partition tolerance (in the face of the nodes in the system being partitioned by a network fault). 
The theorem states that networked shared-data systems can only strongly support two of the following three properties: 
### 2.1 Consistency 
Consistency means that the nodes will have the same copies of a replicated data item visible for various transactions. A guarantee that every node in a distributed cluster returns the same, most recent and a successful write. Consistency refers to every client having the same view of the data. There are various types of consistency models. Consistency in CAP refers to sequential consistency, a very strong form of consistency. 
 
### 2.2 Availability:
Availability means that each read or write request for a data item will either be processed successfully or will receive a message that the operation cannot be completed. Every non-failing node returns a response for all the read and write requests in a reasonable amount of time. The key word here is “every”. In simple terms, every node (on either side of a network partition) must be able to respond in a reasonable amount of time. 
 
### 2.3 Partition Tolerance: 
Partition tolerance means that the system can continue operating even if the network connecting the nodes has a fault that results in two or more partitions, where the nodes in each partition can only communicate among each other. That means, the system continues to function and upholds its consistency guarantees in spite of network partitions. Network partitions are a fact of life. Distributed systems guaranteeing partition tolerance can gracefully recover from partitions once the partition heals. 
## 3. Joins 
A JOIN clause is used to combine rows from two or more tables, based on a related column between them. There are four type of join in database:
### 3.1 INNER JOIN
The INNER JOIN keyword selects records that have matching values in both tables.
Example:
```
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```
The INNER JOIN keyword selects all rows from both tables as long as there is a match between the columns.
### 3.2  LEFT JOIN
The LEFT JOIN keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.
Example:
```
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
```
The LEFT JOIN keyword returns all records from the left table, even if there are no matches in the right table.
### 3.3   RIGHT JOIN
The RIGHT JOIN keyword returns all records from the right table (table2), and the matching records from the left table (table1). The result is 0 records from the left side, if there is no match.
Example:
```
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
```
 The RIGHT JOIN keyword returns all records from the right table, even if there are no matches in the left table.
### 3.4 FULL OUTER JOIN
The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or right (table2) table records.
Example:
```
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
```

## 4. Aggregations, Filters in queries 
### 4.1 Aggregations
Aggregation is a design strategy in which the relationship is modelled between a collection of entities and another relationship.
Simply  it is used when we need Express a relationship among other relationships.When using data in the form of numerical values, the following operations can be used to perform DBMS aggregation:

#### 4.1.1 Average (AVG):
 This function provides the mean or average of the data values.
Sum: This provides a total value after the data values have been added.
#### 4.1.2 Count: 
This provides the number of records.
#### 4.1.3 Maximum (Max): 
This function provides the maximum value of a given set of data.
#### 4.1.4  Minimum (Min): 
This provides the minimum value of a given set of data.
#### 4.1.5 Standard deviation (std dev): 
This provides the dispersion or variation of the sets of data. Let’s take a simple example of a database of student marks. If the standard deviation is high, it means the average is obtained by lower number of students than usual, and the lowest and highest marks are higher.
### 4.2 Filters in queries
When you query table information, you can filter records with the WHERE clause to extract only those records that fulfill a specific expression. Any row that doesn’t meet the conditions (the expression evaluates to false or NULL) is discarded. The WHERE clause follows the FROM clause.
Example :
```
SELECT column1, column2, ...
FROM table_name
WHERE expression;
```
Here Where expression is used to filter out the result based on the conditions. In this, there will be equality operator(==,<>),logical operator(>,>=,<,<=) and logical operators (AND, OR, NOT, BETWEEN,  IN, LIKE, ISNULL) can be used.
## 5. Normalization
Normalization is the process of minimizing redundancy from a relation or set of relations. Redundancy in relation may cause insertion, deletion, and update anomalies. So, it helps to minimize the redundancy in relations. Normal forms are used to eliminate or reduce redundancy in database tables.
### 5.1 First Normal Form 
A given relation is called in First Normal Form (1NF) if each cell of the table contains only an atomic value. OR. A given relation is called in First Normal Form (1NF) if the attribute of every tuple is either single valued or a null value.
### 5.2 Second Normal Form-
A given relation is called in Second Normal Form (2NF) if and only if-
* Relation already exists in 1NF.
* No partial dependency exists in the relation.
### 5.3 Third Normal Form-
A given relation is called in Third Normal Form (3NF) if and only if-
* Relation already exists in 2NF.
* No transitive dependency exists for non-prime attributes.
### 5.4 Boyce-Codd Normal Form-
A given relation is called in BCNF if and only if-

* Relation already exists in 3NF.
* For each non-trivial functional dependency A → B, A is a super key of the relation.

## 6. Indexes
An index is a set of keys made up of single or multiple columns in a table or view. They are stored in a structure (B-tree) that helps SQL Server users quickly and efficiently find the rows or rows associated with the key values.There are mainly two types of indexes in SQL Server:
### 6.1 Clustered
Clustered indexes use key values for sorting and storing data rows in tables or view. They are included in the index definition. It always stores the index value in a B-tree structure where the actual data is stored in the leaf node. Since the data rows are stored in one direction, each table can only have a single clustered index.
### 6.2 Non-Clustered
The structure of non-clustered indexes is similar to the clustered index except that the actual data is not contained in the leaf nodes. A non-clustered index has the non-clustered index key values, and each key-value entry contains a reference to the actual data. Depending on how the table data is stored, it could point to a data value in the clustered index or a heap structure. If a row locator is a pointer to the row, it is a heap structure. If a row locator is the clustered index key, it is a clustered table.

## 7. Transactions
It is a set of operations that are all logically related. It is a single logical unit of work formed by a set of operations.The main operations in a transaction are:
* Read operation reads the data from the database and then stores it in the buffer in main memory.
* Write operation writes the updated data value back to the database from the buffer.
  
A transaction goes through many different states throughout its life cycle.
![](https://www.gatevidyalay.com/wp-content/uploads/2018/05/Transaction-States-in-DBMS.png)

These states are called as transaction states.
### 7.1  Active State
* This is the first state in the life cycle of a transaction.
* A transaction is called in an active state as long as its instructions are getting executed.
* All the changes made by the transaction now are stored in the buffer in main memory.

### 7.2 Partially Committed State
* After the last instruction of transaction has executed, it enters into a partially committed state.
* After entering this state, the transaction is considered to be partially committed.
* It is not considered fully committed because all the changes made by the transaction are still stored in the buffer in main memory.
  
### 7.3 Committed State
* After all the changes made by the transaction have been successfully stored into the database, it enters into a committed state.
* Now, the transaction is considered to be fully committed.
### 7.4  Failed State
* When a transaction is getting executed in the active state or partially committed state and some failure occurs due to which it becomes impossible to continue the execution, it enters into a failed state.
### 7.5 Aborted State
* After the transaction has failed and entered into a failed state, all the changes made by it have to be undone.
* To undo the changes made by the transaction, it becomes necessary to roll back the transaction.
* After the transaction has rolled back completely, it enters into an aborted state. 
### 7.6 Terminated State
* This is the last state in the life cycle of a transaction.
* After entering the committed state or aborted state, the transaction finally enters into a terminated state where its life cycle finally comes to an end.
## 8. Locking mechanism
Locking mechanisms are a way for databases to produce sequential data output without the sequential steps. The locks provide a method for securing the data that is being used so no anomalies can occur like lost data or additional data that can be added because of the loss of a transaction.
There are three types of locking 
### 8.1 Binary Locks
A binary lock has two states or values associated with each data item. These values are Locked(1) and  Unlocked(0).If a data item is locked, then it cannot be accessed by other transactions.But, if a data item is in the unlocked state, then, it can be accessed by any transaction and on access the lock value is set to locked state. In binary locks,at a particular point in time, only one transaction can hold a lock on the data item.Noother transaction will be able to access the same data concurrently. Hence, Binary locks are very simple to apply but are not used practically.
### 8.2 Shared / Exclusive Locks
In shared locks, multiple users are allowed to access the same data item with a read lock which is shared by them. But, in case when a transaction needs to write a data item, then an exclusive lock is applied on that data item. So here:
#### 8.2.1 Shared Locks
Shared locks are applied to a data item when the transaction requests a read operation on the data item. A shared lock will allow multiple transactions to only read the data item concurrently.

As these locks are applied on read operation, they will not compromise on the consistency of the database.
#### 8.2.2 Exclusive Locks
Exclusive locks on the other hand are applied on the transactions which request a write operation on the data item.

The transaction which is modifying the data item requests an exclusive lock on the data item and hence any other transaction which needs access to the data item has to wait until the lock applied by the previous transaction has been released by it.
But when exclusive locks are applied there are situations when a transaction enters into a wait state indefinitely. Such a state where a transaction cannot come out of the wait state is known as a deadlock.
### 8.3 Two Phase Locking
The Two Phase Locking Techniques guarantee Serializability in DBMS. A transaction is said to follow Two Phase Locking Protocol if all locking operations in the transaction precede the first unlock operation.
In this, locks are applied in two phases:
#### 8.3.1 Growing Phase
This phase is also known as the first phase or the expanding phase. It is in this phase that the transaction acquires all the locks needed by it but it cannot release any locks here.
#### 8.3.2 Shrinking Phase
This phase is also known as the second phase or the contracting phase. Here a transaction is not allowed to acquire any new locks but it can release the existing locks it holds. The Two Phase Locking Protocol helps solve problems of lost update, inconsistent analysis or dirty read too.

## 9. Database Isolation Levels
### 9.1 Isolation 
It determines the visibility of transactions of other systems. A lower level allows every user to access the same data. Therefore, it involves high risk of data privacy and security of the system. However, a higher isolation level reduces the type of concurrency over the data but requires more resources and is slower than lower isolation levels.

The isolation protocols help safeguards the data from unwanted transactions. They maintain the integrity of every data by defining how and when the changes made by one operation are visible to others.
### 9.2 Levels of isolation
There are four levels of isolations which are explained below −
#### 9.2.1 Read Uncommitted
It is the lowest level of isolation. At this level; the dirty reads are allowed, which means one can read the uncommitted changes made by another.
##### 9.2.2 Read committed
 It allows no dirty reads, and clearly states that any uncommitted data is committed now it is read.
#### 9.2.3 Repeatable Read 
This is the most restricted level of isolation. The transaction holds read locks on all the rows it references and write locks over all the rows it updates/inserts/deletes. So, there is no chance of non-repeatable reads.
#### 9.2.4 Serializable 
The highest level of civilization. It determines that all concurrent transactions be executed serially.
## 10. Triggers
A trigger is a stored procedure in database which automatically invokes whenever a special event in the database occurs. For example, a trigger can be invoked when a row is inserted into a specified table or when certain table columns are being updated.
### 10.1 BEFORE and AFTER of Trigger:
* BEFORE triggers run the trigger action before the triggering statement is run.
* AFTER triggers run the trigger action after the triggering statement is run.

## references
* https://csveda.com/locking-techniques-in-dbms/
* https://databasemanagement.fandom.com/wiki/Locking_Mechanisms
* https://www.tutorialspoint.com/what-are-different-transaction-isolation-levels-in-dbms
* https://prepinsta.com/dbms/aggregation/
