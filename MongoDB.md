### Metadata

- Title:Data Modeling with MongoDB
- URL:https://www.youtube.com/watch?v=3GHZd0zv170

Here’s a summary of the key points:

1. **Data Modeling Considerations** : The talk discusses key considerations in data modeling with MongoDB, including linking, embedding, and when to use each or both. It also reviews some design patterns and applies them to a use case.

# RDBMS approach

* **Tabular vs MongoDB** : The speaker compares the tabular approach to data modeling with MongoDB. In a tabular database, you define the schema first and then develop the application. However, this approach can lead to concerns such as performance drops when the data model evolves and requires restructuring.

- ([01:45](https://www.youtube.com/watch?v=3GHZd0zv170&t=105s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/faff9700-8c5a-4d98-8997-1090e5d43733.jpeg)

- ([02:20](https://www.youtube.com/watch?v=3GHZd0zv170&t=140s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/1d6155fb-fd2e-4947-b2dd-b302a86c8494.jpeg)

# MongoDB approach

* **MongoDB Approach** : In MongoDB, you first develop the application, then define the data model based on the application’s needs. This approach allows for continuous improvement of both the application and the data model without any downtime.
* **Data Dictates Storage** : The MongoDB approach allows the way you use your data to dictate how it is stored, providing many design options. **The design is centered around the usage pattern, and the data model evolution is easy, flexible, and can evolve without any downtime.**

- ([03:24](https://www.youtube.com/watch?v=3GHZd0zv170&t=204s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/abf0712f-88fd-41b2-b735-d744dff46375.jpeg)

- ([03:55](https://www.youtube.com/watch?v=3GHZd0zv170&t=235s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/0b92ae66-75c6-4278-a6c6-3a3306d7dd61.jpeg)

* **Methodology** : There is a methodology developed over the years for this flexible approach to data modeling with MongoDB. The data model is defined at the application level, and design is part of each phase of the application’s lifetime. The things that affect your data model and its changes are the data that your application needs and the application’s read and write usage of the data.

- ([05:08](https://www.youtube.com/watch?v=3GHZd0zv170&t=308s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/4308fbc6-44d7-4018-89ea-6a71529d7434.jpeg)

# Step by Step iteration

## Evaluate the Application Workload

The first step in the methodology is to evaluate the application workload.

* This involves consulting a business domain expert,
* considering the current and potential application workload, and analyzing production logs and stats.
* This step helps to understand the **data size, rank operations by importance, and identify database queries and indexes.**

- ([07:22](https://www.youtube.com/watch?v=3GHZd0zv170&t=442s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/ce03ddec-0ad0-48fc-a847-427b0ae3c1b6.jpeg)


## **Map Entities and Relationships** : **Linking vs Embedding**

* The next step is to map out the entities and their relationships. This can result in a collection relationship diagram **where decisions are made on whether data will be linked or embedded.**
* **Linking vs Embedding** : The speaker explains the concepts of linking and embedding in MongoDB.

  * Linking means looking up additional information in another collection,
  * while embedding means putting pieces of data together in one document.
  * The decision to link or embed depends on how often the embedded information gets accessed, whether the data is queried using the embedded information, and how often the embedded information changes.

- ([09:12](https://www.youtube.com/watch?v=3GHZd0zv170&t=552s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/9edf7ada-f7f3-42ce-a681-87322af020a8.jpeg)

### One to One linking vs embedding

- put the author unique id value link it in the book document and i can also link the book information in the author document
- if each author only wrote one book i can also just embed this information i can say hey this is the book this is the author depending on how my data is being used and what i'm looking for
- I might be able to just put those pieces of data together embedded one into the other
- ([09:50](https://www.youtube.com/watch?v=3GHZd0zv170&t=590s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/9006e6d4-86be-41f8-ab22-2e5c31e75be4.jpeg)

- ([10:26](https://www.youtube.com/watch?v=3GHZd0zv170&t=626s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/191cdd66-a942-47a1-a987-941bafab75b7.jpeg)

### 1-N One to many

- in this case our author wrote multiple books but we don't want to list all the information about every single book when we are just interested in the author again *this all depends on how you query your data s*o in this case i can just link the one-to-many relationship in the following way i just create an array and a parent document where the array contains the unique ids for every book i'll have other information about the author
- instead of having an array you can just say hey this book was written by this author i'm just going to put its unique id there and for every book that was written by that author it's going to throw in the unique id the one side of the relationship into their linked because i don't have the entire information about the author i just have the unique id
- ([10:55](https://www.youtube.com/watch?v=3GHZd0zv170&t=655s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/663e4b3a-fc15-43f5-87d3-040ab16279f9.jpeg)

- ([11:25](https://www.youtube.com/watch?v=3GHZd0zv170&t=685s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/4e8a42d7-758f-46ed-9afc-a5c688748a4c.jpeg)

### N-N Many to Many

- you just put a arrays on either side if you want to get more information go to that unique id that is listed in the array
- ([11:56](https://www.youtube.com/watch?v=3GHZd0zv170&t=716s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/75625f53-650a-4870-8079-f8676a1ee52b.jpeg)

* These are the general main examples. There could be other options. Everything is very specific and unique to your specific application and approach
* how can we map out those entities and their relationships into collections and documents given all the options

### Blog use case

* if our queries are exclusively by articles then the easiest and quickest solution is just to **embed everything**
  * when i'm querying an article i want to know everything about it
  * the author the tags the categories the comments the users
* If I can both query by articles and by users then i need to change my approach a little bit
  * i can embed and link so some of the data can be embedded some of it can be linked in this case
  * it would make sense to get the users into their own collection because i am able to query by users and just link users to articles
  * so if i want to just get the user information i can do that easily by just querying a single collection if i want to get the articles information i can do that by querying the articles collection
* depending on how your app is used you can have different approaches to the design

- ([13:05](https://www.youtube.com/watch?v=3GHZd0zv170&t=785s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/f9a45c59-f030-4197-9357-16dc19c90139.jpeg)

### Decision making

you need to answer a few questions

1. how often does the embedded information get accessed
2. is the data queried using the embedded information
3. does the embedded information change often

- ([13:35](https://www.youtube.com/watch?v=3GHZd0zv170&t=815s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/5a2c3438-1f29-47d2-8625-35bdc67a05df.jpeg)

## Finalize the data model

* **Finalize the Data Model** : The final step is to finalize the data model for each collection. This involves identifying and applying relevant design patterns.
* The result is a list of collections with documents and fields, data size, database queries and indexes, current operations, assumptions, and growth projections.

- ([14:10](https://www.youtube.com/watch?v=3GHZd0zv170&t=850s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/098af97e-6a3f-4f5a-a567-1a5a2b8206b4.jpeg)

# Design Patterns

## Schema versioning pattern

* This pattern applies the iterative approach to schema changes and data model evolution.
* Absolutely, the **Schema Versioning Pattern** is a powerful design pattern that allows for flexibility and adaptability in your data model. It supports the iterative approach to application development by allowing schema changes over time without disrupting the application’s functionality. Here’s a summary of the process:
* **Initial Schema** : You start with a basic schema. For example, a document containing an ID, name, and contact information (mobile and work phone).

- ([14:42](https://www.youtube.com/watch?v=3GHZd0zv170&t=882s))
- ([15:18](https://www.youtube.com/watch?v=3GHZd0zv170&t=918s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/ddfec793-52ca-4ba6-a169-f78ad338ae72.jpeg)

### Handling Multiple Schemas

1. **Schema Evolution** : As the world changes and new forms of contact emerge (email, Twitter, LinkedIn, etc.), you decide to change your schema. You might choose to store these various contact methods in an array.
2. **Handling Multiple Schemas** : To handle both the old and new schemas, you add a field for the schema version. This allows your application to quickly determine which schema version a document is using and handle it appropriately.


- ([15:50](https://www.youtube.com/watch?v=3GHZd0zv170&t=950s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/feee2f89-ef8e-4106-989e-c9a045cb170b.jpeg)

### Data migration

1. **Data Migration** : Over time, you might decide to update all your data to the new schema.
   1. This can be done through a batch updater on the backend or
   2. by updating each time you query the data and find it’s in the old schema version.
2. **Deprecation of Old Schema** : Once all your data is in the new format, you can deprecate the handling of the old schema version.
3. **Result** :
   1. Your application can now handle documents with varying numbers of contact methods, from two to fifteen or more, with ease.
   2. This is because you’ve built **your application and data to be flexible and adaptable, thanks to the Schema Versioning Pattern.**

This pattern is particularly useful in today’s fast-paced world where data structures and requirements can change rapidly. It ensures that your application remains robust and adaptable to change.

- ([16:21](https://www.youtube.com/watch?v=3GHZd0zv170&t=981s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/3d100051-afe5-457a-9a72-687a269629d1.jpeg)

- ([16:54](https://www.youtube.com/watch?v=3GHZd0zv170&t=1014s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/9e814081-9e8f-4fbb-8197-6e798c20d31e.jpeg)

## The bucket pattern

([17:22](https://www.youtube.com/watch?v=3GHZd0zv170&t=1042s)) Indeed, the **Bucket Pattern** is a powerful design pattern that can significantly enhance performance, especially in scenarios involving Internet of Things (IoT) devices.

**Scenario:** You have a very smart building  that has a bunch of sensors all over the place. **I never usually want to look at a specific single thermostat reading in a document** when you have things like sensors and iots **i probably want to run some statistical analysis** on that and figure out what's the average temperature this month in all of my rooms or what's the water usage for this month

 Here’s a summary of how it works:

### **Tabular vs Document Approach** :

1. In a tabular approach, each sensor reading would create a new document.
   1. let's say i have a thermostat and i want to get a measurement on every room every hour so with a tabular approach i would just have to create a new row in my table for every single entry every single thermostat reading
   2. **it doesn't utilize the nature of documents**
2. However, the document approach allows you to c**reate a new document per time unit per sensor, grouping them from the start in the time intervals that you’re interested in.**

- ([18:04](https://www.youtube.com/watch?v=3GHZd0zv170&t=1084s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/07c26b76-aad7-4d32-9a22-8f2059d5678a.jpeg)


### **Bucketing Measurements**

Instead of looking at every single document for computations, you can bucket your measurements per intervals that make sense to your application.

1. For example, if you measure temperature once a day, one document would give you all the measurements from the start date to the end day.
2. To do those kind of computations, I would have to look at every single document see
   1. what date it was
   2. what time stamp it has and
   3. all of that stuff
   4. instead i can just bucket my measurements per intervals that make sense to me

### **Benefits of the Bucket Pattern** :

1. The bucket pattern benefits from the document model’s flexibility.
2. It’s great for storing small related data items and can be helpful in **scenarios like bank transactions**.
   1. another example where the bucket pattern can be really helpful is bank transactions you can store them related by account
3. One of the best parts about it is that **it reduces the index sizes by a large magnitude** because you have fewer documents now.
4. This leads to an **increase in the speed of retrieval of related data**.

- ([20:06](https://www.youtube.com/watch?v=3GHZd0zv170&t=1206s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/568276ba-9217-4edf-a324-50a356af22fa.jpeg)

### **Implementation**

let's say we have this thermostat sensor and right now the sensor value is five this is sensor number five and the reading is 22 and the date is 20 20 05 11. so how do we record this reading into our collection we start with using the updateOne command

* **You can use the `updateOne` command with the `upsert: true` option.**
* This means that if the query used to find the document that needs updating is not satisfied **valcount $lt 200**, a new document will be created. Otherwise, you can continue to populate the document that you’re finding.
* You can push to the array of all the measurements, the reading, the timestamp, and keep track of how many readings you have so that when you reach 200 readings, you can create a new document.
* **that's built-in functionality and built-in logic that you can just start using right away**

- ([20:38](https://www.youtube.com/watch?v=3GHZd0zv170&t=1238s)) ([21:49](https://www.youtube.com/watch?v=3GHZd0zv170&t=1309s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/507928fd-bdd5-4982-b76b-9ab9dee3be45.jpeg)

## The Computed Pattern

The **Computed Pattern** is another powerful design pattern that can significantly enhance performance, especially in scenarios involving data computations. Here’s a summary of how it works:

### **Compute on Write**

1. **Instead of computing the average rating for every read operation**, which involves going into every single document, counting the documents, adding up all the ratings, and then dividing one by the other,
2. **you can improve your writes**. When writing to the document, you can also update some general information about all of your ratings. You can increase the sum of all the ratings and the rating count. This way, every single read just looks at those two numbers and knows the answer.

**Implementation** : Every time somebody leaves a rating or a review, the review gets added to the review array, and the total count of all added ratings increases, and the rating count increases. You can just look at those two values to get the average rating.

- ([22:20](https://www.youtube.com/watch?v=3GHZd0zv170&t=1340s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/f159199a-aa97-43c5-8a44-295585aef6e1.jpeg)

- ([22:55](https://www.youtube.com/watch?v=3GHZd0zv170&t=1375s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/3cdc3fab-9920-4187-af59-8609ca7fa7bc.jpeg)

### Benefits of the Computed Pattern

* **Never recompute what you an precompute.** I have to recompute everything and that is also a lot of cpu work
* The computed pattern helps optimize for reads being as performant as possible since **reads are often more common than writes.**
* Compute on write is also less work than compute on read. You do it in one single operation, and it happens once instead of many times over and over again when you read.
* So all you have to do is when updating the database, update some summary records as well.
* You can also **think of it as a caching pattern.** You’re essentially caching already recorded data or some information about your already recorded data.

- ([23:57](https://www.youtube.com/watch?v=3GHZd0zv170&t=1437s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/e780c325-2174-449c-81be-989188e45f67.jpeg)


### **Computed Pattern with the Bucket Pattern**

In addition to counting how many values we have and increasing that by one every time, we can also have a field that records the total, the sum of all the values together. So if you want to find the average temperature or the average value for the sensor, you can just divide the total by the number of values, and you have your average value for these 200 sensor readings.

These patterns are just a few among many more useful and wonderful patterns that can significantly enhance the performance of your application.

- ([24:24](https://www.youtube.com/watch?v=3GHZd0zv170&t=1464s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/4236c9ba-1f9e-40ee-a1af-86c06f1edfdd.jpeg)

# Sample use case - Online Shoppint Application

Designing an online shopping application like “Mart” involves several steps:

## Evaluate the application workload

**Gather Business Domain Expertise** : 

* Understand the business requirements, **current and predictive scenarios, production logs, and stats.**
* For Mart, this includes understanding the scale of operations (1000 stores, 50 employees per store, 10 million items, 100 million user accounts), the user behavior (account creation, item lookup, cart operations), and the need for analytics.

- ([26:55](https://www.youtube.com/watch?v=3GHZd0zv170&t=1615s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/b1bfdf99-f2aa-4543-88c6-50dba6e99a3c.jpeg) 

## Identify Key operations and indexes

1. **Identify Key Operations** : Identify the most important queries for the application.
   1. For Mart, these are when a user views a specific item and when a user adds an item to the cart.
   2. These operations need to be fast and reliable.
2. **Potential Indexes** : Determine what potential indexes will be used
   1. to make it easy for users to find items. This could be by category, item name, or price.
3. **Assumptions and Projections** : Make assumptions about the data storage and growth.
   1. For Mart, the data will be stored for a maximum of five years, and
   2. the number of items sold and the number of users will double each year.

- ([27:09](https://www.youtube.com/watch?v=3GHZd0zv170&t=1629s)) ([28:40](https://www.youtube.com/watch?v=3GHZd0zv170&t=1720s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/89bba8a3-966e-4b70-9c09-54c130fa5da9.jpeg)

## ER diagram

**Map Entities and Relationships** :

1. Identify the list of entities and map out their relationships.
2. For Mart, the entities include carts, categories, items, reviews, staff, stores, users, and views of items.


- ([28:55](https://www.youtube.com/watch?v=3GHZd0zv170&t=1735s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/17053f29-82b8-4bf0-a56a-080ef70b04f3.jpeg)


## **Decide on Data Embedding and Linking** 

Decide on what data to embed and what to link.

### Embed Everything? (bad to start)

* the simplest and fastest and easiest solution is to well embed everything
* every user would have carts and every user would view items so i would make that a user's collection
* i'll have an items collection that contains reviews and categories and
* finally i'll have the stores collection that deals with the staff and everything else will be linked so embed as much as i can


- ([29:16](https://www.youtube.com/watch?v=3GHZd0zv170&t=1756s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/34795b17-1a90-4756-970d-1d1a1c146637.jpeg)

### Applying bucket pattern for older data (carts and views)

* we assumed that we're only going to keep our data for five years
  * so let's do that if we want to clear our log of views every five years
    * maybe we want to bucket them somehow and then just make it easier to clear that
  * same with carts you don't want to keep them for longer than five years
* let's separate them **i don't want to go through every user look at the old carts and see** well is me is it time for me to archive this and get rid of it or should i hold on to it yet it hasn't been five years

- ([30:23](https://www.youtube.com/watch?v=3GHZd0zv170&t=1823s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/97625242-b4e9-4d3a-acd1-94c6f47c9378.jpeg)


## **Finalize Data Model for Each Collection** 

Finalize the data model for each collection using various patterns

* first i applied the Schema Versioning pattern, (must and everywhere)
* Subset Pattern,
* Computed Pattern - i have the ratings for items using the computed pattern,
* Bucket Pattern for reviews, and
* Extended Reference Pattern.

These patterns help optimize the data model for your specific use case.

Remember, there is not one pattern solution for your data model. **You can mix and match different patterns**, embed and link data as per your specific use case. The goal is to create a robust, scalable, and efficient data model for your application.

- ([30:53](https://www.youtube.com/watch?v=3GHZd0zv170&t=1853s)) ([31:27](https://www.youtube.com/watch?v=3GHZd0zv170&t=1887s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/e04b1ad9-5dd5-4ee6-b305-c530a7a59ce7.jpeg)

# Data model approaches

**Data Model Evolution** : As your team and application grow, **your data model will also evolve**. This evolution is not just limited to the data model **but also includes the architecture of how you set everything up.**

- ([32:34](https://www.youtube.com/watch?v=3GHZd0zv170&t=1954s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/04c5a6a7-1df2-4a8c-960e-72218fae998f.jpeg)

## Based on App/Team size

1. **Simpler Data Model for Smaller Applications** : For smaller, earlier-stage applications with a small team and a shared hosted database, a simpler data model is beneficial. Embedding everything is not a bad idea in this scenario.
2. **Performant Data Model for Larger Applications** : For larger applications with a big team and a large sharded cluster, optimizing for performance is crucial. You want a performant data model that **allows you to retrieve and write data quickly.**
3. **In-between Scenarios** : For in-between scenarios, like having a replica set setup, you might want a simpler data model but with a bit of the performant approach.


- ([33:04](https://www.youtube.com/watch?v=3GHZd0zv170&t=1984s)) ([33:40](https://www.youtube.com/watch?v=3GHZd0zv170&t=2020s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/81facd71-4165-4208-8878-7e4aa1f83a3b.jpeg)

## Based on simplicity

1. For a simpler data model, **focus on the most frequent operations and consider embedding everything** and using a few patterns.
2. If you want a bit of both, start considering the data size, use embedding and linking, and use as many patterns as necessary.
3. For the most performant data model, **optimize for the importance of operations, frequent operations, and the data size.**
   1. This means using embedding and linking, using a lot of patterns, and being creative with this flexible approach.

Remember, the flexible data modeling approach is about being creative and iterative, just like your application development process. It’s about finding the right balance and making adjustments as your application evolves.

- ([34:10](https://www.youtube.com/watch?v=3GHZd0zv170&t=2050s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/15a7db4e-532f-4881-a6a1-8cb32e844439.jpeg)


- ([25:01](https://www.youtube.com/watch?v=3GHZd0zv170&t=1501s)) ([25:29](https://www.youtube.com/watch?v=3GHZd0zv170&t=1529s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/1ab36213-60dc-4d5c-b02a-aecb3fadaae2.jpeg)
