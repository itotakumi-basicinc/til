## Basic Optimization System of Redshift

Redshift doesn’t use an index system like B-trees. Instead, it relies on **DISTKEY** and **SORTKEY**.

### Main Reasons Why Your Query Might Be Slow

1. **Table Scan**  
   - Similar to traditional databases.

2. **Data Transfer Between Nodes**  
   - Because Redshift is a distributed system, it often needs to transfer and aggregate data across nodes when performing operations such as joins.  
   - This data movement can significantly slow down query performance.

### How to Achieve Resilience

#### SORTKEY for Efficient Scanning

Redshift uses a **zone map** system together with the **SORTKEY**.  
Although it doesn’t use traditional index systems, the combination of sorting and zone maps works in a similar way.  
Data within each node is sorted according to the SORTKEY, allowing the zone map to quickly identify where to start reading records when executing a query.

#### DISTKEY for Minimizing Data Transfer

As Redshift operates in a distributed environment, **data transfer between nodes** is sometimes necessary when performing joins.  
This means that data frequently used together should ideally reside on the same node.  
The **DISTKEY** determines how data is distributed across nodes, helping reduce unnecessary data movement and improving query performance.
