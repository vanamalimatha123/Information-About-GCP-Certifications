# Best Practices for Using Datastore
This module covers best practices for using Datastore.

## Learning Objectives
- Bulk-load data into Datastore by using Dataflow.
- Understand best practices related to queries, built-in and composite
  indexes, inserting and deleting data (batch operations), and transactions 
  error handling.
  
## Datastore Concept and Indexes
- Datastore is the ideal solution for 
  - if you want to store your application's data, and the data is 
    - structured or semi-structured, but not relational
    - highly scalable and meets the needs of your application.
  - Datastore can scale from zero to millions of requests per second 
    without you changing configuration or adding notes to a cluster.
    
### Datastore = Firestore in Datastore mode
- Fully backward compatible with original Datastore but uses Firestore's 
  improved storage later
- The Datastore page is used to manage the database
- A project can have only a Firestore Native mode database or Datastore mode 
  database, but not both
-  Firestore's Native data model, real-time updates, and mobile and web client 
   library features cannot be used with Datastore mode.
- How to decide:
  - Choose Datastore mode when creating a new server application
    - Automatically scales to millions of writes per seconds
  - Choose Native mode for new mobile and web aps or when requiring 
    real-time and offline features
    - Automatically scales to millions of concurrent clients

### Datastore concepts
- Data objects are called *entities*
- Entities are made up of one or more properties
- Each entity has a *key* that uniquely identifies it, compose of:
  - Namespaces
  - Entity kind
  - Identifier (either a string or numeric ID)
  - Ancestor Path (Optional)
- Operations on one more entities are called *transactions* and are atomic
-  When you create an entity, you can specify another entity as its parent. 
   - An entity without a parent is a root entity
- An entity's child, the child's child, etc, are the entity's descendants
- The sequence of entities from the root entity to a specific entity forms the 
  ancestor path
  
### Datastore Indexes Types
- Built-in indexes
  - Automatically predefined indexes for each property of each entity kind
  - Are suitable for simple types of queries
- Composite indexes
  - Index multiple property values for indexed entity
  - Support complex queries
  - Are defined in an index configuration file
  -  If a property will never be needed for a query, exclude the property from
     indexes.
     -  Unnecessarily indexing a property will result in increased latency to 
        achieve consistency and increased storage costs for indexes.
     -  Excessive use of composite indexes also results in increased latency 
        and storage costs

### Create and delete your composite indexes
- Defined in a configuration file named *index.yaml*
- To Create a composite index:
  - Add index definition to index.yaml
  - Run `gcloud datastore indexes create`
- To delete a composite index:
  - Remove indexes you no longer need from index.yaml
  - run `gcloud datastore indexes cleanup`
  
- Datastore
  - Is designed to automatically scale to very large data set
  - Doesn't support join operations, inequality filtering on multiple properties
    or filtering on data based on results of a subquery
  - Doesn't require entities of the same kind to have a consistent property set
  
### Design Considerations & Sharding
- Use UTF-8 character for:
  - Namespace names
  - Kind names
  - Property names
  - Key names
- Avoid forward slash (/) in:
  - Kind names
  - Custom key names
- Use sharding to increase rate of writes
  - Datastore will shard entities automatically
  - You can shard manually if the number of writes exceeds Datastore limits
- A single entity of Datastore, should not be updated too rapidly
  - You should design your application so that it will not need to update an 
    entity more than once per second
- Shard counters to avoid contention with high writes
  - Reduce contention by building a sharded counter, breaking the counter up
    into N different counters in N entities
  - To increment, pick a shard at random and increment its counter
  - To retrieve the count, read all the sharded entities and sum their 
    individual counts
- Use replication to read a portion of the kye range
  - Use replication to read a portion of the key range at a higher rate
  - You can store N copies of the same entity, allowing an N times higher rates
    of reads

### Replication, Query Types, Transactions, and Handling Errors

#### Things to consider when designing your application's operations
- User batch operations for reads, write, and deletes
- Roll back failed transactions
  - Having a rollback in place will minimize retry latency for concurrent 
    requests of the same resources in a transaction
  - If an exception occurs during a roll back, it is not necessary to retry the 
    rollback operation
- Use asynchronous calls

#### Use query types based on your needs
- Keys-only `SELECT __Key__ FROM Task`
  - Retrieve only the key
  - Return results at lower latency and cost (free)
- Projection `SELECT priority, percent_completed FROM Task`
  - Retrieve specific properties from an entity
  - Retrieve only the properties included in the query filter
  - Return results at lower latency and cost (free)
- Ancestor `SELECT * FROM Task WHERE __key__ HAS ANCESTOR KEY(TaskList, 'default')`
  - Limit results to the specific entity and its descendants
- Entity `SELECT * FROM Task WHERE done = FALSE`
  - Retrieve an entity kind, zero or more filters, and ero or more sort orders

#### Improve your query latency by using cursors instead of offsets
- In general, you should avoid using offsets in your queries and instead use 
  cursors
- Integer offsets
  - Don't return skipped entities to your application
  - Still retrieve the entities internally
  - Cause your application to be billed for read operations
- Query cursors
  - Retrieve a query's results in convenient batches
  - Don't incur the overhead of a query
  
#### Numeric IDs as keys
For keys that use numeric IDs:
- Do not use a negative IDs
  - Negative numbers can interfere with sorting
- Do not use the value 0
- Avoid sequential numbering of keys.
- If you wish to manually assign numeric IDs to your entities, get a bock of IDs
  using the `allocateIds()` method
  - This will prevent Datastore from assigning one of your manual numeric IDs 
    to another entity
- Avoid monotonically increasing value, such as 1, 2, 3 or product 1, product 2

#### Transaction design considerations
- Atomic
  - All or none are applied
- Max duration: 270 sec
_ Idle expiration: 60 sec
- it can fail when:
  - Too many concurrent modifications are attempted on the same entity
  - A resource limit is exceeded
  - Datastore encounters an internal error
- Make your Datastore transaction indempotent whenever possible
  - so that if you repeat a transaction, the end result will be the same
  - An item potent operation is one that has no additional effect if it is 
    called more than once with the same input parameters. 
- When a Datastore request succeeds, the API will return a '200 OK' status code 
  with the requested data in the body of the response.
- Failures return a 4xx or 5xx status code with more specific information about
  the errors that caused the failure
- Requests that return an INTERNAL error should not be retried more than once.

## Summery
- Cloud Datastore is a fully managed, no SQL database service that you can use 
  to store structured or semi-structured application data.
- Data objects in Cloud Datastore are called entities. Each entity is of a 
  particular kind. You can specify ancestor path relationships between entities 
  to create entity groups.
- Ancestor queries of entity groups give you a strongly consistent view of the 
  data.
- By creating entity groups, you can ensure that all related entities can be 
  updated in a single transaction. Cloud Datastore automatically builds indexes
  for individual properties in an entity.
- To enable more complex queries with filters on multiple properties, you can 
  create composite indexes. 
- Cloud Datastore can scale seamlessly with zero down time, make sure to ramp 
  up traffic gradually.
- A general guideline is to use the 500-50-5 rule to ramp up traffic.
  - You want to start with a base write rate of 500 writes per second and 
    increase it by 50% every 5 minutes. Distribute your writes across a key
    range.
