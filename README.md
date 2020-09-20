Creating a Ba graph with Neo4j
----------------------------------------------------------------------------------
 **Ba construction** is one of the special and complex constructions in Chinese, There is no construction in other country's language
that is coincidence with a Ba construction. Depending on the syntax features of Ba construction, it can be divided into several different meanings.
The **Neo4j** is the most popular way of building contexts. This project created a Ba graph using the Neo4j to represent Ba constructions and to solve the complex semantic issues related to Ba construction.


DATA MODEL
-----------------------------------------------------------------------------------
[![Screen-Shot-2020-09-09-at-10-14-24-PM.png](https://i.postimg.cc/hP6VVTLR/Screen-Shot-2020-09-09-at-10-14-24-PM.png)](https://postimg.cc/ZCP9S9sw)

Setup Database
-----------------------------------------------------------------------------------
Install [Neo4j 4.1](https://neo4j.com/download/) on your desktop, input Username and Password

```
Username = bagraph_database
PASSWORD = sera1234
```

Code for Neo4j Driver
-----------------------------------------------------------------------------------
```
pip install neo4j-driver==4.1.0
pip install neo4j==4.1.0
from neo4j import GraphDatabase
driver = GraphDatabase.driver("bolt://localhost:7687", auth=("neo4j", "password"))
session = driver.session();
```

Import CSV
------------------------------------------------------------------------------------
This project provides some csv files which are related to Ba construction. The data is composed of extracted syntax features using Jieba.
```
LOAD CSV FROM "file:///import/把nv作.csv" AS row
MERGE (v:动词 {value: row[2]})
MERGE (n:名词 {value: row[1]})
MERGE (c:其它 {value: row[3]})
```

Graph Run!
------------------------------------------------------------------------------------
```
CALL db.schema.visualization
```
CALL 
[![bagraph.png](https://i.postimg.cc/DZ1tv3LY/bagraph.png)](https://postimg.cc/Kkv9fV9n)

