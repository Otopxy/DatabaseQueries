# DatabaseQueries
Otopxy@gmail.com:~/environment/TemitopeOlajide $ psql -h traineedb.cgq0reqixqsd.us-east-1.rds.amazonaws.com -d postgres -U traineeUser
Password for user traineeUser: 
psql (10.15 (Ubuntu 10.15-0ubuntu0.18.04.1), server 12.4)
WARNING: psql major version 10, server major version 12.
         Some psql features might not work.
SSL connection (protocol: TLSv1.2, cipher: ECDHE-RSA-AES256-GCM-SHA384, bits: 256, compression: off)
Type "help" for help.

postgres=> \dt
                 List of relations
 Schema |        Name         | Type  |    Owner    
--------+---------------------+-------+-------------
 public | teamchukwuemeka2021 | table | traineeUser
 public | teammanifest2022    | table | traineeUser
 public | teamtemitope2021    | table | traineeUser
 public | teamtheresande2021  | table | traineeUser
(4 rows)

postgres=> SELECT * FROM teamtemitope2021;
 id | name  | age | department  | role |  status   | created_dt 
----+-------+-----+-------------+------+-----------+------------
  1 | Sarah |   5 | Accounting  | PM   | Activated | 2020-01-01
  2 | Tim   |  10 | Engineering | QA   | Pending   | 2020-02-01
  3 | Joe   |  17 | Management  | PM   | Activated | 2020-02-01
  4 | Tolu  |  25 | Management  | Dev  | Pending   | 2020-02-01
  5 | Rob   |   5 | Engineering | QA   | Activated | 2020-03-01
  6 | Ade   |  10 | Management  | QA   | Pending   | 2020-04-01
  7 | Tom   |  17 | Security    | QA   | Activated | 2020-05-01
  8 | Jide  |  26 | Accounting  | Dev  | Activated | 2020-06-01
(8 rows)

postgres=> SELECT COUNT(*)
postgres-> FROM orders;
ERROR:  relation "orders" does not exist
LINE 2: FROM orders;
             ^
postgres=> SELECT COUNT(*) FROM teamtemitope2021;
 count 
-------
     8
(1 row)

postgres=> SELECT * FROM teamtemitope2021;
 id | name  | age | department  | role |  status   | created_dt 
----+-------+-----+-------------+------+-----------+------------
  1 | Sarah |   5 | Accounting  | PM   | Activated | 2020-01-01
  2 | Tim   |  10 | Engineering | QA   | Pending   | 2020-02-01
  3 | Joe   |  17 | Management  | PM   | Activated | 2020-02-01
  4 | Tolu  |  25 | Management  | Dev  | Pending   | 2020-02-01
  5 | Rob   |   5 | Engineering | QA   | Activated | 2020-03-01
  6 | Ade   |  10 | Management  | QA   | Pending   | 2020-04-01
  7 | Tom   |  17 | Security    | QA   | Activated | 2020-05-01
  8 | Jide  |  26 | Accounting  | Dev  | Activated | 2020-06-01
(8 rows)

postgres=> \dt
                    List of relations
 Schema |           Name            | Type  |    Owner    
--------+---------------------------+-------+-------------
 public | teambright2021            | table | traineeUser
 public | teamchukwuemeka2021       | table | traineeUser
 public | teammanifest2022          | table | traineeUser
 public | teamoluwasanmiawelewa2021 | table | traineeUser
 public | teamtemitope2021          | table | traineeUser
 public | teamtheresande2021        | table | traineeUser
(6 rows)

postgres=> SELECT * FROM teamtemitope2021;
 id | name  | age | department  | role |  status   | created_dt 
----+-------+-----+-------------+------+-----------+------------
  1 | Sarah |   5 | Accounting  | PM   | Activated | 2020-01-01
  2 | Tim   |  10 | Engineering | QA   | Pending   | 2020-02-01
  3 | Joe   |  17 | Management  | PM   | Activated | 2020-02-01
  4 | Tolu  |  25 | Management  | Dev  | Pending   | 2020-02-01
  5 | Rob   |   5 | Engineering | QA   | Activated | 2020-03-01
  6 | Ade   |  10 | Management  | QA   | Pending   | 2020-04-01
  7 | Tom   |  17 | Security    | QA   | Activated | 2020-05-01
  8 | Jide  |  26 | Accounting  | Dev  | Activated | 2020-06-01
(8 rows)

postgres=> SELECT COUNT(*) FROM teamtemitope2021;
 count 
-------
     8
(1 row)

postgres=> SELECT COUNT(*) FROM teamtemitope2021 WHERE department = 'Accounting';
 count 
-------
     2
(1 row)

postgres=> SELECT COUNT(*) FROM teamtemitope2021 WHERE status = 'Pending';
 count 
-------
     3
(1 row)

postgres=> SELECT COUNT(*) FROM teamtemitope2021 WHERE status = 'Activate';
 count 
-------
     0
(1 row)

postgres=> SELECT COUNT(*) FROM teamtemitope2021 WHERE status = 'Activated';
 count 
-------
     5
(1 row)

postgres=> SELECT COUNT(*) FROM teamtemitope2021 WHERE age is BETWEEN 18 AND 26;
ERROR:  syntax error at or near "BETWEEN"
LINE 1: ...ELECT COUNT(*) FROM teamtemitope2021 WHERE age is BETWEEN 18...
                                                             ^
postgres=> SELECT COUNT(*) FROM teamtemitope2021 WHERE age BETWEEN 18 AND 26;
 count 
-------
     2
(1 row)

postgres=> SELECT COUNT(*) FROM teamtemitope2021 WHERE created_dt is 2020-02-01;
ERROR:  syntax error at or near "2020"
LINE 1: ...OUNT(*) FROM teamtemitope2021 WHERE created_dt is 2020-02-01...
                                                             ^
postgres=> SELECT COUNT(*) FROM teamtemitope2021 WHERE created_dt = '2020-02-01';
 count 
-------
     3
(1 row)

postgres=> SELECT COUNT(*) FROM teamtemitope2021 WHERE created_dt BETWEEN '2020-04-01' AND '2020-05-01';
 count 
-------
     2
(1 row)

postgres=> SELECT COUNT(*) FROM teamtemitope2021 WHERE created_dt BETWEEN '2020-04-01' AND '2020-06-01';
 count 
-------
     3
(1 row)

postgres=> ACTIVATE teamtemitope2021 WHERE status = 'Pending';
ERROR:  syntax error at or near "ACTIVATE"
LINE 1: ACTIVATE teamtemitope2021 WHERE status = 'Pending';
        ^
postgres=> UPDATE teamtemitope SET status = 'Activated' WHERE status = 'Pending';
ERROR:  relation "teamtemitope" does not exist
LINE 1: UPDATE teamtemitope SET status = 'Activated' WHERE status = ...
               ^
postgres=> UPDATE teamtemitope2021  SET status = 'Activated' WHERE status = 'Pending';                                                                          
UPDATE 3
postgres=> UPDATE teamtemitope2021 SET name = 'Timothy' WHERE name = 'Tim';
UPDATE 1
postgres=> SELECT COUNT(DISTINCT Department) FROM teamtemitope2021;
 count 
-------
     4
(1 row)

postgres=> SELECT COUNT (id), department FROM teamtemitope2021, GROUP BY department;
ERROR:  syntax error at or near "GROUP"
LINE 1: ...ECT COUNT (id), department FROM teamtemitope2021, GROUP BY d...
                                                             ^
postgres=> SELECT COUNT id, department FROM teamtemitope2021, GROUP BY department;                                                                              
ERROR:  syntax error at or near "GROUP"
LINE 1: ...ELECT COUNT id, department FROM teamtemitope2021, GROUP BY d...
                                                             ^
postgres=> SELECT department, COUNT(*) FROM teamtemitope2021 GROUP BY department;                                                                               
 department  | count 
-------------+-------
 Accounting  |     2
 Security    |     1
 Engineering |     2
 Management  |     3
(4 rows)
