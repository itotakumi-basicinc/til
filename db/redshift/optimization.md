
## Basic System of Redshift for optimization

Redshift doesn’t use an index system like B-trees. Instead, it relies on DISTKEY and SORTKEY.
Because Redshift is a distributed system, it determines which node stores the data based on the DISTKEY. This allows queries to scan only one or two nodes, improving performance.

Redshift also uses zone maps to skip unnecessary data blocks.
So even if you don’t use a DISTKEY, your queries can still perform well as long as the SORTKEY is closely related to the DISTKEY.
