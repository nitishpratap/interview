Replication in MongoDB is a fundamental feature that ensures high availability, data redundancy, and fault tolerance. It involves maintaining multiple copies of data across multiple nodes (servers) in a distributed manner. MongoDB uses a replication mechanism known as "Replica Set" to provide replication functionality. Below is a complete documentation of MongoDB Replication and how to set up and manage Replica Sets:

**What is a Replica Set?**
A Replica Set is a group of MongoDB instances (nodes) that host copies of the same data. It consists of one primary node that handles all write operations and multiple secondary nodes that replicate data from the primary node. If the primary node fails, one of the secondaries will automatically be elected as the new primary, ensuring continuous data availability.

**Replica Set Components:**
1. **Primary Node:** The primary node is the main node that accepts all write operations and acts as the primary source of data for the Replica Set. There can only be one primary node at any given time.
2. **Secondary Nodes:** Secondary nodes replicate data from the primary node and can serve read operations. A Replica Set can have multiple secondary nodes to distribute read traffic and provide data redundancy.
3. **Arbiter Node:** An optional arbiter node is used to break ties during the primary election process. It does not store data but participates in the election process. It can be useful in environments with an even number of nodes.

**Advantages of Replica Sets:**
- High Availability: If the primary node fails, a secondary node automatically becomes the new primary, ensuring continuous data availability.
- Data Redundancy: Multiple copies of data are stored across different nodes, reducing the risk of data loss.
- Scalability: Additional secondary nodes can be added to distribute read traffic and increase read capacity.
- Fault Tolerance: The system remains operational even if some nodes fail.

**Setting Up a Replica Set:**
1. Start MongoDB instances on different servers (nodes).
2. Connect to one of the nodes and initiate the Replica Set configuration using `rs.initiate()`.

Example:
```javascript
// Connect to MongoDB instance on the primary node
mongo --host primary_node_ip

// Initiate the Replica Set configuration
rs.initiate(
  {
    _id: "myReplicaSet",
    members: [
      { _id: 0, host: "primary_node_ip:27017" },
      { _id: 1, host: "secondary_node1_ip:27017" },
      { _id: 2, host: "secondary_node2_ip:27017" }
    ]
  }
)
```

**Managing a Replica Set:**
- To check the Replica Set status, use `rs.status()`.
- To add a new node, use `rs.add()`.
- To remove a node, use `rs.remove()`.
- To promote a secondary node to primary, use `rs.stepDown()` on the current primary.
