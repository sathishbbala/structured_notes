
## When would you recommend YugabyteDB as a database of choice? 
Traditionally databases were scaled vertically, improving the power of the single node database machine by adding CPUs or Memory or storage. With a distributed database, the database is hosted on several nodes, in multiple fault domains, providing better database availability over hosting the database on a single node. Distributed databases provide better HA, scalability, and Geo-distribution.
YugabyteDB is a distributed SQL database that is open source and supports distributed ACID transactions. YugabyteDB offers different deployment options - open source without any product support, subscription based model with product support, and a managed services offering on the hyperscalers. 

1. High Availability
A distributed SQL database is a recommended choice for applications that cannot afford any planned or an unplanned outage, that is, both the RTO and RPO is near zero. Even a multi AZ RDS Database cluster does not suffice the RTO and RPO. Unplanned outages, like a zone failure, would mean promoting a read replica to a primary database and that will incur some downtime for the application and some data loss (as data changes are asynchronously propagated). Planned outages for patching or database upgrades will require cutting off application access to the database during the patching or the upgrade process. With a distributed SQL database, the database will be continuously available in both the above scenarios. 

2. Scalability
A distributed SQL database is a recommended choice for applications that require scaling temporarily when there is a predicted increase in workloads. Instead of vertical scaling and letting the infrastructure stay under utilized for most of the time, there is significant cost savings in horizontally scaling out the infrastructure during peak times and scaling in later. As an example, if the business runs a major promotion for 30 days and expects a 2-3x increase in traffic, then additional nodes can be added to handle the increased traffic. 

3. Geo-distribution
A distributed SQL database is a recommended choice for applications that needs to provide low latency access to its users from different regions. A YugabyteDB cluster can be deployed to have its nodes in different regions so the requests are served by the nodes closest to the users. This is made possible with the row level geo partitioning feature in the YugabyteDB database. 

4. Avoid Vendor lock-in
Many Enterprises prefer to use a cloud agnostic service so they are not locked in with a particular cloud service provider. With YugabyteDB, the database can be hosted on any of the cloud providers or be deployed on-premise. YugabyteDB can also be deployed in a way that the primary database is deployed on a hyper scaler and BC/DR deployed on a different hyper scaler.
