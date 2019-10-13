# Advanced Databases - CMU

Link: [https://15721.courses.cs.cmu.edu/spring2018/slides/01-intro.pdf](https://15721.courses.cs.cmu.edu/spring2018/slides/01-intro.pdf)

## History of databases

1. Old database issues are still relevant todaya
2. SQL vs NoSQL debate is reminiscent of Relational vs CODASYL debate
3. Many of the ideas in today's db systems are not new

## General Electric - IDS
1960s - IDS (Integrated Data Store)
Developed internally at GE

One of the first DBMS:
- Network data model
- Tuple at a time queries

COBOL people got together and proposed a standard on how programs should access DBs. Lead by **Charles Bachman**.
Charles Bachman helped build **IDMS**.

## International Business Machine IMS
1960s - Information Management System

Early db system developed to heep track of purchase orders for apollo missions.
- Heirarchial data model.
- Programmer defined phusical storage format

You can select how to save the data - do you want to save as an array (and do range queries on it) or add as hashmaps (to do search operations).
- Tuple at a time interface

Problems it had: too much duplication and independence

## International Business Machines - Relational Model
1970s - Ted Codd was a mathematician working at IBM research. He saw developers rewriting IMS and CODASYL programs everytime the db schema or layout changed.

DB abstraction to avoid the issues:
- Store DB in simple data structures
- Access data through high level language
- Physical storage left up to the implementation

1970s - Early implementation of Relational Database model:
- System R - IBM research
- INGRES - UC Berkley
- Oracle - Larry Ellison

## Object oriented databases - OODBMS
1980s - to remove relational-object impedance mismatch by tightly coupling object with DBs.
They wanted to store as JSON etc.
Complex things become really complex for complex queries.
**WHAT GOES AROUND COMES AROUND**

## 1990s Boring Days
No major database advancements
Made:
- Microsoft SQL Server
- MySQL
- PostgreSQL
- SQLite

## 2000s - Internet boom
All big players were heavyweight and expensive.
Open-source databases were missing important features.
Many companies wrote their own custom middleware to scale out databeses across single node DBMS instances

### Data warehouses
Rise of special purpose OLAP DBMS:
- Distributes / Shared-Nothing
- Relational / SQL
- Usually closed source

### NoSQL
Focus on High availability and High Scalability
Example
- Apache HCASE
- MongoDB
- NoSQL
- RavenDB
- riak
- Cassandra
- Couchbase
- Redis

No ACID transactions

### 2010s - NewSQL
Provide same perf for OLTP workloads as NoSQL without giving up ACID:
- SAP Hana
- H Store
- db shards

## 2010s - Hybrid systems
Hybrid Transactional Analytical Processing
Executing fast OLTP like a NoSQL system while also executing complex OLAP queries like a data warehouse system

