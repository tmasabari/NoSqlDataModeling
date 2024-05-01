### Metadata

- Title:AWS re:Invent 2022 - From RDBMS to NoSQL (PRT314)
- URL:https://www.youtube.com/watch?v=eEENrNKxCdw

# **Introduction/Agenda**

1. **Introduction**
   * Speaker: Rick Houlihan, Director of Developer Relations for Strategic Accounts at MongoDB.
   * Background: Former Worldwide Leader for NoSQL Services at AWS.
   * Passion: NoSQL technology, believes it’s the future.
2. **Focus of talk:** Understanding why to choose NoSQL technology.
   * Amazon’s choice: Amazon chose a NoSQL-first mentality, not out of preference, but due to compelling reasons.
3. **Amazon’s Decision Process**
   * Process: Discussed the process Amazon went through to decide on NoSQL.
   * Goal: To achieve ‘database freedom’.
   * Challenge: Relational databases were seen as ‘chains that bind us’.
4. **Data Modeling**
   * Importance: Understanding data modeling is crucial to understanding why NoSQL is chosen over relational databases.
   * Efficiency: Discusses efficiency, time complexity, and cost of infrastructure in data modeling.
5. **Modeling Relationships in NoSQL**
   * Breakdown: Plans to break down the math behind modeling relationships in NoSQL.
   * Challenge: How to transition an organization with potentially thousands of developers to a new technology.
6. **Amazon’s Transformation**
   * Project ‘Rolling Stone’: **Managed the deprecation of 3000 Oracle server instances and migration of thousands of application services at Amazon.**
   * Goal: Managed technology transformation at a global scale.
7. **Differences in Modeling Applications**
   * Focus: Differences between modeling an application in a NoSQL database versus a relational database.
   * Developer Guidance: Helps developers find the path to start projects in new technology.

- ([01:34](https://www.youtube.com/watch?v=eEENrNKxCdw&t=94s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/1df3364a-71e3-4d03-aea0-34a7e16a22d9.jpeg)

8. **Amazon’s Background**
   * Misconception: Amazon was not born in the cloud, it was established in 1995, before the cloud existed.
   * Amazon’s IT: **Amazon was a traditional IT organization, with many monolithic applications and services.**
9. **Amazon’s Transition**
   * Challenge: Transitioning from monolithic applications to a NoSQL backend was a significant process.
   * Scale: **By 2018, Amazon had 3000 Oracle server instances** and was the largest Oracle license in the world.
10. **Project ‘Rolling Stone’**

* Mission: The initial goal of Project ‘Rolling Stone’ **was to replace Oracle, not necessarily the relational database.**
* Scale: At the time, **Amazon had 10,000 application services and 25,000 to 30,000 developers globally.**

11. **Cost of Relational Database**

* Issue: **The cost of the relational database was a significant line item for Amazon.**
  * High infrastructure TCO
* Decision: The mission was to get off Oracle and find a better way to do things.

12. **Breaking Up Monoliths**

* Strategy: The initial idea was **to break up monoliths and move microservices into siloed deployments of RDS.**
* Investigation: Something changed along the way when Verner started investigating things.

- ([04:52](https://www.youtube.com/watch?v=eEENrNKxCdw&t=292s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/9c21e279-d0f1-4467-9d91-0fdc4e7477ec.jpeg)

13. **Data Processing History**

* Data pressure: The system’s ability to process data at a reasonable cost and time.
* Technology trigger: When data pressure breaks, new technology is invented.

- ([06:25](https://www.youtube.com/watch?v=eEENrNKxCdw&t=385s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/612a617c-e630-44fa-a09d-c79fda79c929.jpeg)

14. **Database Evolution**

* Early databases: Ledger accounting system, machine-readable punch card, and punch card sorting machine.
* Relational database: Introduced by Edgar Cod around 1980, it was initially believed to be unsuitable for transactional applications.

15. **Moore’s Law**

* Impact: Balanced the checkbook for relational databases, making their inefficiencies less noticeable.
* Breakdown: Since 2014, top 500 supercomputing clusters have not been able to meet Moore’s Law performance predictions.

16. **Financial Equation**

* Moore’s Law: The industry’s willingness to spend to double the transistor density in the CPU every two years.
* Broken Moore’s Law: There’s no ROI for server processing manufacturers to go down to five nanometer fab.

17. **Cost Problem**

* Storage cost: Continues to fall, making databases that don’t require complex JOINs more cost-effective.
* Over normalization: Common practice today, it burns CPU cycles and increases infrastructure cost.
* 

- ([09:11](https://www.youtube.com/watch?v=eEENrNKxCdw&t=551s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/2ab0549e-2f49-4474-97ef-e8f860e969a4.jpeg)

- ([11:16](https://www.youtube.com/watch?v=eEENrNKxCdw&t=676s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/475d996b-0988-4fff-ac60-415444e4fec6.jpeg)

18. **When NoSQL**

* Efficiency: **Increasing the efficiency of the CPU for common queries can dramatically improve the cost profile of the infrastructure.**
* OLAP workload: Previously better suited for a relational database, now there’s a shift towards NoSQL.

19. **NoSQL Databases**

* NoSQL databases are not really NoSQL, they’re no RDBMS.
* Many NoSQL databases have SQL read APIs that handle analytics queries.

20. **OLAP Workloads**

* OLAP workloads do not run at high velocity.
* **Users running OLAP queries typically do not care if the query comes back in a hundred milliseconds or 10 milliseconds.**

21. **Transactional Applications**

* **Transactional applications run at a very high frequency and run the same queries all the time.**
* Increasing the efficiency of the CPU for common queries can dramatically improve the cost profile of the infrastructure.

22. **Over Normalization**

* Over normalization is a common practice today.
* Every time you JOIN a table in an SQL database, you’re burning CPU cycles and paying for infrastructure you don’t need.

23. **When NoSQL**

* There used to be a line between OLAP workload and NoSQL databases.
* OLAP workload that requires ad hoc queries was better suited for a relational database. Now, there’s a shift towards NoSQL.

- ([12:24](https://www.youtube.com/watch?v=eEENrNKxCdw&t=744s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/2457e053-aca6-41b5-a8e5-255600ac7e47.jpeg)

- ([13:16](https://www.youtube.com/watch?v=eEENrNKxCdw&t=796s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/098688f0-6c7f-4a08-abd7-ef1c0ce808ae.jpeg)

# Relational Data

25. **Relational Data**

* Every bit of data that we store is relational.
* Non-relational data is the data on the hard drive before you format it, the static in the air between the radio channels, and the noise between the stars.
* The records associated with a customer or the history of an order are examples of relational data.

- ([13:33](https://www.youtube.com/watch?v=eEENrNKxCdw&t=813s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/8adf97a9-119f-430a-9cbc-8af111c15476.jpeg)

25. **Access Patterns**

* Access patterns are what drives cost in the relational database.
* 70% of the access patterns across all services were for a single row of data on a single table.
* Another 20% were for a range of rows on a single table.
* OLAP access patterns are very write heavy, not read heavy.

26. **Infrastructure**

* When mapping workloads into a NoSQL database with a relational data model, it became apparent that 50% of the infrastructure was there just to support the other 10% of those access patterns.

27. **OLAP Access Patterns**

* OLAP access patterns are very write heavy, not read heavy.
* Writes are always affecting a row or a range of rows or updates, they’re inserts updates.

28. **Infrastructure**

* 50% of the infrastructure was there just to support the other 10% of those access patterns.
* When JOINing tables in the application layer, the cost becomes apparent.

- ([14:07](https://www.youtube.com/watch?v=eEENrNKxCdw&t=847s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/a19e515b-8128-409e-9e7f-b5a116cb6496.jpeg)

# SQL Vs NoSQL patterns

29. **Data Model**

* Storing data in multiple places is not efficient.
* A normalized relational model for a simple product catalog includes products, books, albums, and videos with one-to-one, one-to-many, and many-to-many relationships.

30. **Access Patterns**

* Access patterns are all product centric.
  * Eventually, what's gonna end up happening here, if you think about the access patterns, they're all product centric. Get me the information for this product. Get me a product by ID, get me the product by category. Get me products by, you know, price that have these, you know, attributes, whatever, everything's product centric.
* A cache might be put in front of the database to cache the product query, adding another layer of complexity.
  * So you know, the reality is you'll probably end up putting a cache in front of this database to cache the product query so you don't have to compute the result off of these tables every single time. And, but what's that do for you?
  * That just adds another layer of complexity, right? And then I have to worry about **cache validation and all that kind of stuff, or invalidation**, whatnot.

- ([15:30](https://www.youtube.com/watch?v=eEENrNKxCdw&t=930s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/23ae6325-0660-41dc-bf7c-6afafdb44dc9.jpeg)

31. **Efficiency**

* If the CPUs hopping all over these tables to assemble the view, it’s not efficient.
* Collapsing all rows into an embedded document structure might be a better approach for product centric access patterns.

32. **Updates**

* **Product information updates are infrequent.**
  * 99% of my access pattern is gonna be reads by product ID or type or whatnot. I want the JOIN data, okay? Every now and then, product information updates.
  *  **So what, my write's gonna be a little expensive, but that's the infrequent pattern.** 
* **Optimizing for the high frequency pattern, not the low frequency pattern, is preferred.**

33. **Data Model Limitations**

* Oversimplifying the data model can be **problematic if individual data/rows update frequently.**
  * If you think like order history, orders have items, they have shipments and invoices and payments and whatnot, and all that stuff might get updated independently of each other.
  * I don't wanna read the whole document every time I need to update a single item within it. This was one of the big problems we found at Amazon was he can't oversimplify the data model like this in all cases.
* In some cases, such as a product catalog, simplifying the data model works really well.

- ([17:01](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1021s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/12e9582f-3910-4754-8e1e-ba77038a861a.jpeg)

34. **Efficiency**

* CPUs hopping all over tables to assemble the view is not efficient.
* Collapsing all rows into an embedded document structure might be a better approach for product centric access patterns.

35. **Access Patterns**

* 99% of the access pattern is reads by product ID or type.
* The infrequent pattern is product information updates, which makes writes a bit expensive.

36. **Pre-JOIN Data**

* Pre-JOIN data is preferred in this case.
* This works well in some use cases but can be problematic if individual rows update frequently.

37. **Data Model**

* Oversimplifying the data model can be problematic, especially if individual rows update frequently.
* In some cases, such as a product catalog, simplifying the data model works really well.

38. **Time Complexity**

* Time complexity becomes apparent when looking at JOINs.
* One-to-one JOIN is not too bad, one-to-many JOINs start to get worse, and many-to-many JOINs are even more complex.

39. **CPU Efficiency**

* CPUs have gotten so efficient over the years that the time complexity of queries hasn’t been a big deal.
* However, as CPUs age, the time complexity starts to hurt.

40. **Current Reality**

* These days, the preference is to avoid complex JOINs and time-consuming queries.

# Time Complexity

- ([18:03](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1083s))
- Time complexity down below one-to-one JOIN, not too bad, okay? One-to-many JOINs starts to get a little worse.

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/c36436f9-8133-4f59-a624-a85b9825522f.jpeg)

- ([18:11](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1091s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/5cc392ad-9bdc-4bf5-9242-c276d6bae829.jpeg)

- ([18:28](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1108s))
- Time complexity down below one-to-one JOIN, not too bad, okay? One-to-many JOINs starts to get a little worse.
- And so think what those time complexity of those queries looks like. It's tremendous.
- We never notice it because the CPUs have gotten so efficient over the years, it hasn't been a big deal, and CPU efficiency has just continually increased over and over and over again.

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/5c9ae2d8-5040-49be-aeb9-9a5fa144cb31.jpeg)

# Model Joins in NoSQL

41. 
42. **Model JOINs**

* Model JOINs and aspects of NoSQL can be interesting.
* A basic document structure that describes a product is taken as an example.
* The product has attributes that describe it inside the data object.

43. **Data Objects**

* Data objects are the stuff that describes the product but are not cared about from a querying perspective.
* Data always needs objects and needs to be related to each other.

44. **Access Patterns**

* There are many access patterns besides getting a product by ID.

# MultiKey indexing - Critical concept

* **In a document database like MongoDB that supports multi-key indexing, relationships between the documents can be expressed as an array of pointers within the document itself.**

47. **Adjacency List**

* An adjacency list or a graph is created using a target array that tells what all a thing is related to.
* The target array rows are **like the rows from the mapping table in the relational model or the edges in the graph database.**

46. **Time Complexity**

* The time complexity of going through these base documents is O(log(N)).
* These are key-value access patterns and all these access patterns are O(log(N)).

47. **Adding Additional Objects**

* It gets more interesting when additional objects like directors, actors, song documents, etc., are added that describe everything that these things are related to.

# Key-value access patterns

- ([19:12](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1152s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/f30d3f08-16e1-4537-b3bf-4af286b5fb80.jpeg)

- ([20:35](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1235s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/d42b2833-7ed1-4da5-93db-130038d43a23.jpeg)

- ([21:31](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1291s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/26bc8e7a-0116-4b56-9f92-394bc18e6d52.jpeg)

# Index Joins in NoSQL

48. **Target Arrays**

* Every document has target arrays that tell what they’re related to.
* When you index the target array in a multikey index, it essentially becomes a lookup index on that target array.

49. **JOINs**

* If you think about what the relational database does at its core, **when things are configured properly for high velocity reads, it's gonna take two indexes, one on table A, one on table B,** and it's gonna merge them, On a shared attribute.
* If all documents are put in a single container and indexed on a shared attribute, they’re already JOINed, **eliminating the need to merge indexes.**
  * So now when I want to get all the books by an author, I can select by Target ID is Mary Shelly. I get every book that she wrote, I'll get every person she's related to,
  * anything in this adjacency list that has a relationship to this person will show up by selecting where the target ID is the author.
* Similarly, selecting my song Id brings back all the albums that the song appeared on, all the musicians that performed at the studio that recorded it. Whatever I need to retrieve, I can have any number of access patterns now on a large number of dimensions and the neatest thing about this, I haven't de-normalized any of the real data.

- ([21:59](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1319s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/a96dd88b-971d-4ce4-b1d5-5c7124cfaf78.jpeg)

- ([22:46](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1366s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/42b079be-55ea-48b3-ba8a-b0fd7cfb9327.jpeg)

- ([23:11](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1391s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/e4bb41d7-2054-47a6-a2c9-037d67cfa83c.jpeg)

- ([23:37](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1417s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/015860e9-50df-42ff-bb1e-5282ada34051.jpeg)

# Solution

50. **Access Patterns**

* You can have any number of access patterns on a large number of dimensions.
* **The data is not de-normalized, only the pointers are.**
* There are no mapping tables anymore (for many to many relationships), and the multikey index keeps track of all data duplication.
  * The mapping table kind of gets de-normalized across the objects here. But the **multi key index keeps track of all of that data duplication that would be required if I didn't have that feature,** right?

51. **Efficiency**

* One of the key features of the document database is the ability to **express relationships extremely efficiently using these data structures.**

52. **Time Complexity**

* Basically all those documents return in that query. And it's one round trip to the database.
* The time complexity of the JOIN in this particular query is O(log(N)), which translates to a massive amount of infrastructure reduction.

53. **Optimization**

* **Developers spend a lot of time optimizing their code to reduce time complexity**.
* **If you’re not optimizing the data model and not worried about your access patterns, you’re building a wobbly tower of technology.**
  * You're not building an application because if you're handing off to an ORM, it's gonna do really ugly things. Okay?

54. **Solution**

1. **It’s best to pay attention to your access patterns,**
1. **create pre-JOIN data structures,**
1. **leverage multikey indexing, and**
1. **reduce the time complexity of your high-velocity queries.**

55. **Access Patterns at Amazon**

* 90% of the access patterns at Amazon are for a **single table, a single row, or a range of rows on that table. They're working with small bits and pieces of data**
* The 10% that JOIN everything are the ones where the infrastructure cost is felt.
* So if I can **reduce the time complexity of those JOIN**s and **maintain the cost efficiency of updating small items,** then I'm gonna have a win-win all the way around.

56. **Document Database**

* **The document database is a vastly superior solution** because it reduces the time complexity of JOINs and maintains the cost efficiency of updating small items.
* MongoDB does all these updates across all these partitions on the table for you.

# NoSQL adoption

57. **Developer Relations**

* There are two sides to developer relations: advocacy and enablement.
* Advocacy involves talking about the technology, while enablement is about teaching how to solve problems with it.

- ([25:35](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1535s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/3fc8687c-9948-449c-b65d-43e9c5a4f16b.jpeg)

58. **Technology Transformation**

* **Success in a technology transformation is about getting to the early majority in the technology adoption curve.**
* The early majority indicates that the ecosystem knows what they’re doing.

59. **Data Pressure**

* **Data pressure is a technology trigger in the space.**
* Many people face the **problem of expensive relational databases and think NoSQL will solve that problem.**

60. **Misuse of NoSQL**

* Misuse of NoSQL occurs when **people try to use it the same way they use old technology,** leading to a miserable experience.
* **There is a lot of misinformation about how NoSQL works, and people often mistakenly try to use relational models in a NoSQL database.**

61. **Early Adopter Phase (2022)**

* We're still in that early adopter phase, right? Why? Because there is **so much misinformation out there about how NoSQL works** and people actually think that it's real.
  * there's blog posts and there's all kinds of things to talk about using relational models in an NoSQL database. **It breaks everything. It makes it worse than the relational database. Do not use relational models in NOSQL DB.**
* Understanding how NoSQL works leads to a better experience.

62. **Amazon’s Approach**

* Amazon prioritized getting their 25,000 developers up to speed as quickly as possible.
* They used a process of evangelizing and using the technology, conducting workshops and hackathons.

- ([26:25](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1585s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/f72370ea-3e19-4596-bff8-579e1c627e45.jpeg)

# Amazon shopping cart example

63. **Amazon Shopping Cart Team**

* The Amazon Shopping Cart team was one of the first teams to try the new technology.
* They initially found it unworkable due to the cost of operations on the shopping cart data.

64. **Shopping Cart Use Case**

* The shopping cart is a complex use case with various operations on the data.
  * It's an interesting use case because, you know, people add items to the shopping cart
  * . They delete items a shopping cart, right?
  * They may keep a shopping cart in the system for God knows how many weeks or months or whatever, and
  * then come in and make an order and delete 40 items out of the cart.
* Items in the shopping cart have their own lifecycle and are updated at different frequencies.
  * Inside of Amazon, they might get shipped outta different fulfillment centers, right?
  * They're updated at different frequencies, right?
  * If you, when you check out, you'll see in the cart there's two different might deliver on this day or this day.
  * It's like there's all kinds of operations occurring on the data that's in the shopping cart. And this was a real clue because those little items inside the shopping cart, each one of those things in DynamoDB, it was about each one of these is about a kilobyte.

65. **DynamoDB Cost**

* DynamoDB charges based on the size of the item, which increases with each added item.
  * DynamoDB is kind of merciless when it comes to cost. And the WCU is minimum of is, it was one kilobyte. And so if they added one item to the cart, it was a kilobyte
* This led to high costs, especially for users who keep many items in their cart for extended periods.
  * Now you get someone who has 12 items in the cart and then sits there and does that for three weeks, right? It becomes extremely expensive.

- ([29:30](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1770s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/8f148eea-bd0b-49f0-b95c-3e18db22e114.jpeg)

## Cost optimized Solution

67. **Solution**

* The solution was to create a partition key (the shopping cart ID) and a sort key (the ASIN or SKU of the item) in DynamoDB.
* This made every update to the cart an addition of an item into that partition, keeping the cost constant at one kilobyte.
  * If you think of the partition, it's kind like an index,
  * We basically loaded these objects into partitions and as we added and removed items, the WCU cost was constant. One kilobyte never more.
  * They cut their cost by 80% when they ran their workload simulations, right?
  * So all of a sudden it became an effective technology, right? So the key was that the team needed to learn how to use it, right?

67. **Design Reviews**

* The team started conducting design reviews with various teams to teach them how to use the technology.
* These reviews helped teams understand how to model their data correctly for their workloads.

- ([29:52](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1792s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/8220be29-4cfb-4d50-968c-a991bdbe3115.jpeg)

68. **MongoDB Day**

* The speaker runs events called MongoDB Day (formerly DynamoDB Day), which are all about NoSQL.
* These events involve advocacy sessions, deep dives into the technology, and exploration of data modeling.

69. **Tailored Engagements**

* The speaker executes tailored engagements throughout the year with strategic accounts.
* These engagements involve understanding what the customers want to know about the technology and showing them how it works. The speaker emphasizes that he is not there to sell anything, but to educate.
  * We'll do the half day engagements where we'll talk about the technology, dive deep on aggregation framework, the dive into the developer platform, whatnot. But the real meat for our customers is this exploration of data modeling, right?

- ([30:43](https://www.youtube.com/watch?v=eEENrNKxCdw&t=1843s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/8d685745-9182-451e-be78-939e2c248c0b.jpeg)

# Thinking in documents

70. **Grace Hopper Quote**

* Rick Houlihan cites a quote by Grace Hopper: “One accurate measurement is worth a thousand expert opinions.” This quote is the cornerstone of his career.

71. **Schema Bench**

* His team has a tool called Schema Bench, which allows customers to configure different schema options and run their access patterns. It gathers P95 latency, average, mean, total throughput, etc.

72. **NoSQL vs Relational Database**

* He argues that you can never configure a relational database to run faster or with higher throughput than NoSQL for the same workload.
  * I can guarantee you you'll never be able to configure a relational database that has the word JOIN in that query and have it run faster or better or with higher throughput than I can the exact same workload with the exact same result in NoSQL
  * If it's higher time complexity to run that query, it's just gonna take longer. It's gonna take more infrastructure, okay?

73. **Thinking in Documents**

* when we want to start working with NoSQL, it's about thinking in documents and I even **wide, colum store, document database,** whatever, you can all, call it all, it's all documents, because everything supports a JSON type, nested data structures are just part of the business.
* When working with NoSQL, it’s about thinking in documents, objects, or items. It’s important to understand the access patterns.

- ([33:22](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2002s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/218358ba-c514-4629-b323-867b102aff0c.jpeg)

74. **Methodology**

* **The methodology followed is the same for any NoSQL database.** It’s about understanding the workload and the relationships.
  * It doesn't matter if I'm DynamoDB, MongoDB, whatnot.
  * I've got a lot more API feature functions with a MongoDB. I've got a lot more indexing options and flexibility. But the core data models are the same.
  * **the bottom line is I need to understand the workload.**

75. **Design Patterns**

* There are many design patterns to apply based on the entity relationship diagrams. His team goes through the access patterns of their customers and decides what the documents should look like and what design patterns to apply.

76. **Choosing Simplicity or Performance**

* There is always a choice between simplicity or performance. It’s important to understand what you’re modeling for.

77. **Understanding the Nature of the Workload**

* It’s important to understand the nature of the workload you’re trying to model. If it’s a high velocity pattern, then you need to optimize for common patterns while accommodating corner case patterns.
* If the workload doesn't really have any velocity and doesn't have any size, no need to spend much time in optimizing the data model, the thing that runs a couple times a day, fine, just use large embedded documents. Don't worry about how much those updates cost. It's not a big deal.
* But if it's, you know, runs thousands of times a second, you know, then I care, okay then I'm gonna wanna make sure that those patterns are highly optimized. You know, for the particular use case that we're talking to. Once I understand the workload, it's about relationships, right? It's all about relationships.

Relationships and patterns

* **The logical entity relationship diagram is still important for using a NoSQL database.**
* It is gonna define how we set up or structure the documents that we're using and what kind of patterns we're gonna apply, right?
* There's a whole bunch of design patterns on MongoDB University

- ([34:52](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2092s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/9c3f3d0e-14e8-49af-aaa1-ccde85527c97.jpeg)

# Flexible methodology - choosing simplicity or performance

- This is the mantra of NoSQL data modeling, right? Optimize for the high frequency patterns, okay? Again, the ones that run thousands of times a second, those are the ones we care.
- While accommodating those corner case patterns, the ones that are those operational analytics maybe that run once an hour, once a day, whatever. We don't really care about the efficiency of those queries, we just need to make sure we can support them.
- ([35:41](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2141s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/45f2cb26-b64f-4bcd-a815-2b81827d5159.jpeg)

78. **Use Case**

* **A common use case for NoSQL databases these days is in large enterprises** when people want a single view of the customer or data and eventually want to create a new system of record for some of these backend systems.

- ([37:11](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2231s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/62d5e4f3-04ab-4ac6-a14e-98d6faeaab37.jpeg)

# Mongo insurance portal use case


79. **Insurance Company Use Case**

* He presents a use case of an insurance company built through acquisition with many backend systems.
* The company wants to merge all data from these systems into an online portal for a better user experience.
  * to avoid miserable customer experience, customer logs in the online portal, takes 45-60 seconds to go hit all these backend systems and get all the data and figure out who they are and everything. What they really want is they wanna merge all that data from those legacy systems into an online portal that gives 'em a much better user experience,
* This portal will be a read-only copy of the data.
  * just updates coming in from the backend that are, you know, being applied in batches throughout the day, but maybe eventually it'll be the future base of the customer portal, right?

80. **Offloading Mainframes**

* Offloading a lot of the read velocity from the backend mainframes can breathe life into those systems by **giving them more overhead to handle additional writes.** This works both ways **to help the mainframe as well as the customer.**
* But the idea here is kind of read only cache offload those mainframes.
* 

- ([37:53](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2273s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/8c0c782c-e641-43bb-9878-0863229a6d00.jpeg)

## Workload analysis

81. **Understanding the Workload**

* The first step in the process is to understand the workload and identify the access patterns.
* **If you don’t know what your access patterns are, you should be writing user stories, not code. User stories define your access patterns.**
* And if you don't have any of those, then why are we writing code? Okay? So **code includes the query, the query is the access pattern,** right? So as soon as I write a line of code that contains a query, I've defined an access pattern, we can start talking about the data model. So let's do it and let's do it up front

82. **Access Patterns**

* In this case, there are four patterns to care about:
  * changes coming into the Mongo insurance portal from the backend systems,
  * loading user profile,
  * loading the overview of the account, and
  * loading the details of the artifact.

83. **Velocity of Queries**

* Streaming updates peak at 2000 transactions per second.
* These are **critical writes** coming from the backend systems.
* Users log in at a pretty good rate throughout the day, with 12 reads per second on various access patterns. The one that’s really hammering them is the streaming updates.

84. **Small Streaming Updates**

* The streaming updates are to small rows of data in the relational databases which back all those services today. These small streaming updates are critical.

- ([39:27](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2367s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/c9f67ca8-d0ac-4a0a-b2c2-8cae24091b4d.jpeg)

## Usage pattern analysis

85. **Portal Use Case**

* The use case is a portal with a standard navigation pane on the left,
* some summary data about open messages or claims, and
* detailed information in the center.
* As users navigate through various objects, they’ll open up details of those various artifacts.

- ([39:57](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2397s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/9cb2716d-12be-4af5-be93-94e39adfdc4c.jpeg)

- ([40:19](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2419s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/e9b90ad5-5f6f-46e0-a5e8-d3b475bfd5e8.jpeg)

## Domain model analysis


86. **Understanding the Data Model**

* The next step is to understand the data model. In this case, it’s a *straightforward hierarchical data model* where customers have policies, claims, invoices, documents, and messages. There are no many-to-many relationships here.
* . I see these types of hierarchical schema, these are very easily represented in NoSQL databases.

- ([40:37](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2437s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/86d6cd91-284b-42ab-9779-92799532a00d.jpeg)


87. **Applying the Patterns**

* The process of applying the patterns is a trade-off between simplicity and performance. If updates are coming in at 2000 transactions per second, it’s important to ensure these updates are happening efficiently.
  * if I have one large document for all the user data, then eventually that's gonna create a very large document with lots of arrays of embedded sub documents.
  * And as each one of those policies, updates or message comes in on a claim, **I'm gonna be reading the entire customer document to write that message right back into it.** This is the **most common mistake that you see in NoSQL databases.**

88. **Document Sizes**

* **It’s better to keep document sizes pretty close to the row size, especially when there are high velocity updates coming in randomly across the schema.** Small documents, in the four to 10 kilobyte range, are preferred.
* if you're using the 16 megabyte document in MongoDB, let's talk cuz there's something wrong and you're probably paying a lot of money to do something that is really bad, right? Even over a couple hundred kilobytes, anything I like to see small documents, right? Really small documents like in the four to 10 kilobyte range.

- ([41:16](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2476s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/2bf445cb-af42-41ac-baac-7c62989fdeed.jpeg)

- ([42:26](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2546s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/df157a92-5ba5-47a7-8a4a-d570fead4192.jpeg)


# Extended Reference Pattern

89. **Extended Reference Pattern**

* The extended reference pattern is used where a reference of one document from one document is kept in another.
* This allows for efficient querying of documents that are related to each other to support those patterns much better.
  * The model I showed you earlier, we created **target arrays of pointers,** right?
  * Those pointers were essentially references between the documents.
  * **We index those references, essentially we execute the JOIN without having to have incur the time complexity.**

90. **De-normalizing immutable Data**

* ***De-normalizing mutable data is not preferred. However, if it’s immutable data and it makes it easier to model, then it’s acceptable since storage is cheap.***

91. **$lookup Operator**

* The $lookup operator, which is a JOIN operator, is provided but **should only be used when necessary.** It’s **for those infrequent patterns,** like needing an **hourly report** across multiple collections.
* I need to run that report a thousand times a second.you're not gonna need $lookup and so, and you don't wanna run that, right?

92. **One Read is Faster Than Many**

* Always remember that one read is faster than many. The overhead of establishing the cursor on a table is where most of the system’s overhead comes in.
* **If you can query one index instead of five, you’re reducing the system’s overhead by orders of magnitude.**
  * I just put all those objects on multiple tables and index on, you know, order ID, right? And I can have ships, invoices and payments and I'll query everything at the same time, right
* 90% of the overhead a system incurs in processing a request is handling it, **(marshaling the data and pushing it up is nothing).** **Opening a cursor on a table is expensive, returning a couple extra rows or a couple extra documents from that collection is negligible overhead.**

- **([43:08](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2588s))**

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/eb32e315-6f7c-46e2-9dfe-70659631ff81.jpeg)

# Underbar ID and Key overloading

93. **Hierarchical Document Structure**

* The document structure is again, a hierarchical structure.

94. **Pushing Data into a Single Collection**

* Pushing data into a single collection or table and querying a single index can dramatically improve throughput, latency, and other factors.

95. **Key Overloading**

* A technique called key overloading is demonstrated. This technique is used a lot in DynamoDB and applies just as well to MongoDB.

96. **Underbar ID**

* One of the biggest mistakes seen in document databases like MongoDB is not using Underbar ID. **Underbar ID is the default index on every collection in MongoDB and cannot be turned off.** Every write is going to touch that index.
* They'll let the database automatically assign a value to it because that's the primary key, right? And it identifies the uniqueness of the document. But then you'll never have an access pattern says get this document by ID, right?

97. **Write Only Index**

* ***If Underbar ID is not being queried, then it’s a dead index, a write-only index. It’s a wasted resource on the server.***

98. **Using Underbar ID in Multiple Ways**

* In this case, Underbar ID is used in multiple ways.
  * I'm gonna use more human readable data here, and then I'm gonna prefix the keys of the rest of the hierarchy to create a path that I can query down, right?
  * To get the subsets of documents that are interesting to me, right? If I want the whole history of a customer, I say, starts with C1, brings back everything the customer has.
  * I want just the policy data select by C1 Underbar, P1, where it begins with C1, Underbar, P1. It brings back all of the data that is associated to the policy if it's, you know, so on and so forth.
  * I want messages for a given policy, starts with C1, P1, M1 brings back the messages sub, you know, subset or sub document from this array of documents.

99. **Creating a Path on Underbar ID**

* A path is created on Underbar ID using key prefixing **so that groups of these documents can be selected using a starts with condition on that key.**
  * I can pull the whole hierarchy easily with, starts with C1 and get everything and so on and so forth down the path.
* This essentially allows **almost every access pattern to be supported with one index, the default index on this particular collection.** This makes the data structure as efficient as possible.

- ([47:47](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2867s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/e2bb3bc6-1f8e-4612-98de-10ac1e07bee1.jpeg)

# Outlier Pattern

100. **Outlier Pattern**

* This pattern is used when data objects grow over time and sometimes become too large, such as messages.
* **If the data needs to overflow across multiple documents to prevent the write cost from becoming too high, this pattern is used.**

101. **Building an Array of Messages**

* If you think about what happens when messages come in, if I have a document that, you know, some customers might be really chatty and others not so much
* When messages come in, an array of messages is built in the messages document.
* At some point, that array becomes large enough that it becomes painful and too expensive to update.

- ([48:18](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2898s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/0d95829d-64d9-4a84-8c1f-1e39083a0f95.jpeg)

102. **Breaking Up the Document**

* When the array becomes too large, the document might need to be broken up.
* If the average customer talks 60 messages or less and the **whales are talking more than that, then the whales are going to get multiple message buckets.**

103. **Creating a Pattern for Outliers**

* A pattern is created where those outliers essentially have more than one message document and they end up with C1_P1_M1, C1_P1_M2. This pattern helps manage large amounts of data more efficiently.
* it's gonna **gimme the most current document depending on which way the index is sorted**.
* And you know, as there's always a way to get the list of those current messages, but **each message update is only gonna cost me a minimum unit of cost.**

- ([49:12](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2952s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/8fa0a429-18bf-4dc8-b517-ffd49c785ba0.jpeg)

- ([49:21](https://www.youtube.com/watch?v=eEENrNKxCdw&t=2961s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/8d9738ac-1e44-46c5-a506-d31f20fab925.jpeg)

# Document Databases Cost

104. **Understanding Document Databases Cost**

* One of the most critical things to understand in document databases and NoSQL databases in general is the minimum unit of cost. It’s important to know how much it costs to write into the database and what minimum size of document is needed to avoid extra cost.

105. **Comparison of DynamoDB and MongoDB sot**

* In the shopping cart scenario with DynamoDB, it’s merciless with **one kilobyte equating to one WCU and no data compression.** MongoDB, on the other hand, has four kilobyte blocks in the storage engine for wired tiger and **offers compression**. With mixed binary text data, the **minimum unit of cost is about 16 kilobytes.**

106. **Efficiency of Writes and Document Size**

* **Depending on the access pattern, there might be reasons to use really small documents.** The goal is to ensure that writes are as efficient as possible. In MongoDB, documents in the range of 16 kilobytes are considered.

107. **Compression Ratios and IOPs**

* **With full text data, better compression ratios might be achieved.**
* However, when building documents, crossing a certain line will cost two IOPs.
* If the access pattern needs it, that’s fine. If not, it’s a waste of space and capacity.

# Conclusion

108. **NoSQL and Non-Relational Data**

* **NoSQL does not mean non-relational data.**
* **The ERD still matters** and **data still needs to be modeled.**
* The relational database is done and cannot escape time complexity.

109. **Scaling of Relational Databases**

* Some people say the relational databases scale just fine. They can be made to “fly” by adding time complexity, distributed cross commits, Paxos, etc. Reducing queries to O(log(N)) will reduce the amount of infrastructure needed.
  * Anything will fly. Okay? Seriously give enough velocity, a brick will fly. Hey, that's how they fixed the space shuttle, right?

110. **Database Infrastructure Costs**

* Database infrastructure is the number one cost in the enterprise today because the relational database is a waste.
* NoSQL is a great fit for most OLTP workloads and also for OAP these days with SQL read APIs.
