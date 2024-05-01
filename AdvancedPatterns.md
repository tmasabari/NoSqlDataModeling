### Metadata

- Title:Advanced Schema Design Patterns
- URL:https://www.youtube.com/watch?v=bxw1AkH2aM4
- ([01:40](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=100s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/ffbb48bd-a605-4bf5-8511-56ebe23d596c.jpeg)

# Patterns

* We can make a parallel between MongoDB schema design pattern with the software design patterns described by the gang of four.
* The patterns are not full solutions but rather **building blocks identified over many years that act as a common language within a team.**

- ([03:07](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=187s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/669b32c4-9412-4933-b718-903184a3e942.jpeg)

The primary purpose of these patterns is to **improve the performance of your schema and simplify data access by prearranging data in a simpler form.**

- ([03:25](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=205s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/b0867091-8987-4774-badf-b1c7d35f8106.jpeg)

# Cautions

* You'll see a lot of these cases in system where duplication of data is not that bad. Some patterns bringing you basically these cases just to make things faster.
  * However, caution is needed when using these patterns as **some may lead to data duplication or staleness.**
* While **data duplication is generally discouraged**, especially when striving for **a 3rd normal form** in your model, there are situations where it may be desirable.
  * If we have a 3rd normal form, and we have a relationship between invoice to the addresses, if we change the address, we basically change the address for all the invoices. You see in this case, it makes more sense to add the information about the address being inside the invoice, and even if it's duplicated.
* Understanding your system and the type of data it will be dealing with is crucial. This understanding will help determine whether data staleness or denormalization is acceptable. If you’re coming from the SQL world, denormalization might not be new to you as it’s often one of the first avenues explored when trying to improve performance.

- ([05:20](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=320s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/9d252ce5-a975-4844-a2e6-6722a7bdeb3b.jpeg)

# Different patterns and use cases

* This table is not set in stone but serves as a guide towards the patterns you should be looking for.
* For instance, if you’re developing an Internet of Things application, certain patterns are likely to be more relevant.
* It’s important to remember that these patterns are tools to aid in design and optimization, and their effectiveness will depend on the specific requirements and constraints of your system.

- ([05:52](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=352s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/985d28d0-2bcc-401a-831f-84eed1385b4e.jpeg)

# Modeling Tradeoff

1. **Simplicity and Performance** : In an ideal world, the goal is to design with both simplicity and performance in mind.
2. MongoDB provides this balance for most early release projects, allowing developers to design with simplicity while also achieving performance.
3. **Growth and Complexity** :
   1. As software grows, so does its complexity.
   2. **This increased complexity can lead to a decrease in performance as more computation is required.**
   3. Companies that **grow need to scale,** which requires significant consideration of performance.
4. **Schema Design and Performance** :
   1. Successful scaling requires careful thought about schema and performance.
   2. While additional performance benefits can be achieved, they often come at the cost of simplicity.
   3. **For larger projects, it’s beneficial to focus on schema design early on to emphasize performance.**
   4. This can **reduce the need for major schema changes in later release phases.**
5. **In-Depth Data Modeling Methodology** :, there’s a presentation by Daniel as part of MongoDB Live that you might find useful.

- ([05:59](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=359s)) ([07:30](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=450s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/55b52aea-7067-4e69-9e01-7ef5e5069978.jpeg)

# Data Model Methodology

## Phases of data modeling in MongoDB

1. **Describing the Workload** : The first phase involves identifying the most important operations and quantifying them. This phase also includes assessing the resources needed (servers, disk space, network requirements, etc.) and making assumptions about the workload. All these assumptions should be tracked and revisited as the project progresses.
   1. NOTE: Maybe we think that something we'll be **limited to a number 1,000.** You may have 1,000 maximum friends, for example.
   2. As we go further in the project, or in deployment operation, **if some of these assumptions end up being wrong**, those will be very good indicator that we should go back to the board and **re-look at our design to see the impact of being wrong on those assumptions.**
2. Data Modeling : The next step is to model all the data in the system and identify the relationships between different pieces of data. These relationships could be one-to-one, one-to-many, or many-to-many.
   1. It’s important to quantify these relationships, especially **in big data contexts where “many” could mean thousands or millions.**
   2. This phase also involves **deciding whether to embed or link** relationships.
3. Then you can answer the most important question on your design. Should you **embed or link that relationship?**
   1. Embed means I'm going to take the two pieces of information and **they're going to be in the same collection,** and
   2. linking means that **two pieces of information will live in a different collection, a**nd we will reference one to the other one.
4. Applying Patterns : Once the data is modeled, the next phase is to apply patterns to improve the design. The need for patterns should be recognized and then applied appropriately.

- ([08:01](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=481s))  ([10:56](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=656s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/9f80faf1-9939-42f4-b9a1-ae2d6e014ca4.jpeg)

## Flexible

Simplicity vs Performance : The methodology should be flexible, allowing for a balance between simplicity and performance. 

1. For simpler applications, the focus might be on embedding data and applying fewer patterns.
2. For more complex applications, there might be a mix of embedding and linking, and more patterns might be applied to optimize performance.
3. As you may guess, there's in between for those, which is we do a little bit more description on the workload, and we apply some patterns, but maybe not as much as if we're really trying to optimize everything for performance.

Remember, these phases are not set in stone but serve as a guide to help navigate the complexities of designing and optimizing a MongoDB schema. The effectiveness of these methodologies will depend on the specific requirements and constraints of your system.

- ([11:04](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=664s)) ([12:27](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=747s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/bdc7deb3-b9e0-49cb-8573-aa785f0fb57e.jpeg)

# Use Case - Mongo Insurance Portal (MIP)

## **Identify business requirements**

The MIP project aims **to merge legacy RDBMS systems and provide a fast user interface.** Future considerations include enabling customers to access data through a mobile app. Data query is going to be done in batch through analytics. 

([12:44](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=764s))([13:32](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=812s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/0d7993e6-cb0f-48f1-98e4-ea47e33d8381.jpeg)

## Identify **Operations** 

* List all operations, such as syncing with other systems (a write operation),
* loading user profiles, providing an account overview (UI-driven queries), and
* processing claims.
* **It’s important to focus only on current needs,** as MongoDB allows for **easy schema changes in the future.**
  * I put a question mark. It's just to let you know that at this point, what we're going to do is really focus on what we need to do now. The things that are in the future, it's nice to think about it, but a great thing with MongoDB, it's very easy to make changes to the schema.
  * Let's concentrate on the thing that we know we need to handle.

- ([14:01](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=841s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/4986be1d-b103-4c8b-b86d-f69b6cfab3a6.jpeg)

## Qualify operations

**Each and every operation should be quantified.** 

* For example, syncing changes to the MIP system might occur once a hour (24 writes/day) and could take up to 10 minutes.
* **The UI-driven queries are particularly important, with a response time requirement of two milliseconds.**
  * This is the **budgets** that the team was building those systems, giving us the people who handle the database.
  * user or login has to be fast, getting the navigation bar has to be fast, and any page in the middle which is either the overview one or this one, you retrieve the document, also has to be fast.
* **Data Relationships** : The next step is to examine the relationships between data entities (users, policies, claims, bills, documents, messages). If simplicity is the goal, these entities could be embedded in a large users collection, with each entity linked in a one-to-many relationship.
* **Performance** : All queries need to be fast to meet the UI response time requirements. However, the current design may not be fast enough, indicating a potential need for optimization.

- ([14:53](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=893s)) ([15:17](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=917s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/8389ec5e-0b3c-4ee8-8e60-ccdcc7c6933b.jpeg)

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/3853ec11-9ce7-4fbf-a345-8ca319e1a0b2.jpeg)

- ([15:54](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=954s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/6d3fc284-c15d-4e70-bb05-b96bda50e29d.jpeg)

## ER Diagram

([16:13](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=973s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/27d73fdd-7482-4501-9e99-7bce5225e837.jpeg)

# Simple design

If we're going on the simplicity side, we'll put these here, and just say, "Hey, we're going to have a big collection of users, in which we're going to put the policy claim." 

Everything is linked as a relationship of one to many, and everything's going to be embedded.

The issue we may have with that is that it sound like to be fast enough.

# Applying Patterns Magic

## **Identifying Domains**

We're going to talk a lot about ways of working with our requirements & mockups, and generating our patterns based on that.

One of the requirements is that we render this page extremely fast. To do that, we're actually going to **physically draw boxes around the different domains**. The way that we're going to do that is by first finding the most commonly loaded part of the page.

The different domains that need to be rendered are identified. These include the header, navigation, and main body of the page. Each domain is analyzed to minimize load time.

* **Header Optimization** : The header, which includes the username and possibly a profile photo, is loaded most frequently. **To ensure fast loading, the data is queried once and then stored in the session.**
* **Navigation Optimization** : The navigation section contains various information like policies, open claims, billing amount due, documents, and messages. Each of these elements has a **relationship with the user (so this will vary by user)**, not necessarily with each other. The goal is to load this section quickly, with a requirement of less than two milliseconds.


([16:59](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1019s)) ([18:56](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1136s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/cb697fdf-bbe7-44a6-8db7-85f3fee20643.jpeg)

## Identify relationship

([20:47](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1247s)) ([22:52](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1372s))


* **Model and Relationship Identification** : The relationships between different elements (policies, claims, billing, documents, messages) and the user are identified. This is part of the second phase of the methodology.
  * Though from RDBMS point of view the claims, documents, messages are related to the claims not directly to users, but from the UI use case point of view we need the claims counts for the user.
  * Realistically, claims have a relationship to policies. If you have a policy for your home and a policy for your car, the relationship is between each individual policy and the claim itself. we're only displaying a number here. We don't necessarily care about the relationship between claim and policies.
  * For another example, if I was inquiring about creating a new policy, that message would come directly to me, and wouldn't actually have anything to do with the policy (i am enquiring), because that policy hasn't yet been created.

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/00887e51-b8ec-4be5-bd9e-1b25120c19bd.jpeg)

## Keeping data together

* **Pattern Application** : The third phase involves applying patterns to balance simplicity and performance. **While keeping everything in one large object is simple,** it can lead to large documents that **are slow to load and consume a lot of memory.**
* On the other hand, **creating a collection for each element could improve performance but might complicate the system.** The goal is to find a balance that allows the page to load as quickly as possible.
* All the information necessary to generate the navigation bar is stored with the user. This information is **potentially stored in the session,** allowing for efficient rendering of the section.
* The way that we're going to render this information and keep it together with the user is by identifying two patterns specificall, the extended reference pattern for things like claims, and the computed pattern for things like billing.

- ([24:11](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1451s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/8a7273db-eedc-4ed5-b2c6-06f5c209eee1.jpeg)


# **Computed Pattern**

* The computed pattern is used to **store a computed value instead of calculating the value every time.**
* This is **similar to a view in the relational world,** where you aggregate across many rows to create a calculation.
* Like a cached aggregation.

1. **Efficiency with MongoDB** : MongoDB offers an efficient approach by making trade-offs between reads and writes.
   1. **Most applications have a read to write ratio of about a 1000 to 1,** so the goal is to make reads as fast as possible.
   2. This can be achieved by increasing the number of writes to significantly reduce the operations and the time it takes to do a read.
2. **Using the Computed Pattern** : **Instead of aggregating across many documents, the computed pattern is used to store the result of the aggregation**.
   1. This approach is part of the original goal to load the page as quickly as possible.

- ([24:41](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1481s)) ([25:12](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1512s))([26:13](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1573s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/24237878-e1f3-4ce1-bf0f-e45ea604aeda.jpeg)

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/37638f8c-bdd6-4bc5-b09b-4e58a41b6afe.jpeg)

# Extended reference pattern avoid $lookup

This pattern **keeps a reference to data from one collection to another,** making the data needed to generate a page readily available. This **requires denormalization to increase read performance**. The goal is to avoid additional reads and the latency they introduce.

MongoDB does not have joins. We have $lookup. But again, we're trying to make this as fast as possible. 

Whenever we have to add an additional read, we're adding additional latency to our round trip in order to generate our page. Two reads is going to be slower than one read, so we want to avoid having to do a $lookup

- ([26:32](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1592s)) ([26:50](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1610s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/3ebb130c-2d7d-4171-9c25-ae8d8482e78b.jpeg)

- ([27:04](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1624s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/4c7eb746-abf8-4ec6-84ab-8a76116452f3.jpeg)

## Users collection schema

* The schema shows the relationship between users and different parts of the application.
* **Under 'Extended Reference'**, only necessary information of policies (like the name of the policy and an ID for linking) is kept in the user’s collection.
  * A policy generally has a lot more information than we're keeping in this user's collection. For example, there's a policy premium. We don't copy that over because that's not necessary for the generation of our view.
  * What is necessary is the name of the policy as well as some sort of ID that allows us to link on the website to the actual policy and get more information.
* **Computed Pattern** : This pattern prevents the need to aggregate across multiple documents. It’s used to store computed values like **open claims, document count, and message count, which are used to quickly generate the display in the navigation**.

- ([27:13](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1633s)) ([28:15](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1695s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/f7c9ac01-0e19-4a38-879b-43b3fcc92d43.jpeg)

# **Combining Patterns**

* The billing section combines patterns. **Discrete operations that happen with the user are stored.** For example, an ‘owe’ operation is added when a premium is calculated, and a ‘paid’ operation is added when a payment is made. **The application can quickly calculate the total amount owed** by adding and subtracting these operations.

  * Whenever we have a discreet operation, we're updating this users collection
* **Scalability and Maintainability** : Storing discrete operations rather than constantly updating every document in the user’s collection makes the system more maintainable and scalable.

- ([28:29](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1709s)) ([30:13](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1813s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/23d96052-5754-4768-925a-d97e2fe8a6b9.jpeg)


## **Why don't we just store the current amount owed?**

* Let's say that you have a million users, and those users all have a different amount owed.
* If once a month you had to calculate a new premium balance, and then completely asynchronously users pay, that means that you're constantly going to be updating every single document in your user's collection. That's not really maintainable. That's not scalable, and that's not a great way to implement this solution.
* What we can do is we can store the discreet actions that happen with the user that's relevant. If you have a job once a month that comes in and calculates premiums, we can see that we have an operation, in this case, in 2019 in December, we have an owe operation. It's like a plus.
* Then we see every month, we have somebody paying towards that premium, and we have a paid operation.
* From the application perspective, we can very quickly calculate, by doing addition and subtraction, what the total amount owed will be.
* The application has each individual month, as well as the owed and paid operations, and that gives us our total that we actually displayed, which is the due amount of 800.


# Bucket pattern

This pattern **breaks up a single domain object into multiple documents.** This really **leverages the power of arrays** because it allows you to **keep a set number of items per document, and when you combine multiple documents, you get the sum of all related objects**.

This pattern is useful for **keeping relevant information close together,** which is beneficial for operations like **paging.**

There should be something called the **max size of your bucket.** How many items should we be storing in this array?

- ([30:58](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1858s)) ([31:22](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1882s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/8d0e67ad-fa8c-4711-8f89-5973a670cb97.jpeg)

## Use case -Between 2 extemes of document per metric Vs One for all

There's two extreme way to represent the data. One is the device will send their data, and for every single little metric will create a little document. The other extreme will be we'll create one document with all the metrics for a given device.

Both end don't really works very well. The bucket metric is really an in-between solution to these two where metrics get grouped together, either per hour, per day, you choose. But that's what it is. See it as an in-between solution and grouping data. -This is absolutely what we see most customers use, especially when it comes to the Internet of Things for scaling purposes.

* **Use Cases** : The Bucket Pattern is commonly used **in Internet of Things (IoT) projects.** It provides an in-between solution for representing data, where metrics get grouped together, either per hour, per day, etc. **This pattern is particularly useful when scalability is required.**

- ([31:43](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1903s)) ([32:06](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1926s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/1242aaf8-0dc1-47a9-a082-26c892d16393.jpeg)

## Policies collection use case

Now, looking back at our original page, what we're doing is we're displaying a list of policies. Given that, we need to **only keep a subset of policies,** in order to generate this display. We're also **keeping claims along with the policy**.

- ([30:55](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1855s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/c1f018d5-fa97-4ca5-85ec-b8265ebb78a1.jpeg)


* Similar to what we saw before with extended reference, we have information about a car. The car is relevant to the policy.
* Now there might be another collection called cars that has much more information about these cars. '
* For example, how are we applying individual cars to policies? Here, we only need enough information to generate the display.
* What we have is just the name, type, year, and some attributes. Now, these are all contained within a larger bucket.
* **The reason this bucket pattern is so powerful is because it allows us to embed intelligently.**
* You'll notice at the very top of the screen we have an _id, and that _id references the user object.
* We are now referencing back, and we're intelligently bucketing our data so that it can be displayed efficiently. We again have enough policy information to display what we need to display, when we need to display it.

- ([33:12](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=1992s)) ([34:05](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2045s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/c8170a89-7134-4cf6-951e-6f9a75e4f85c.jpeg)

## Pagination use case

* We're assuming that we've clicked on the document link, and we know from the user session, or the user's collection, that we have the document count of eight. We know that there should be eight things, but we're only displaying six on the screen.
* This pattern allows us to keep two documents that look similar but have different sets of data. For example, if we have a total of eight documents but our display physically shows six documents, we can have a bucket of six and a bucket of two.
* The `_id` continues to reference the user, allowing us to quickly use a range query or regular expression to query based on `_id` to get all of those different documents.

- ([34:12](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2052s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/6a0a0c2c-f92b-40a9-a3f8-416d40616ed1.jpeg)

# Outlier pattern 80-20 rule

**This pattern focuses on an 80% versus 20% use case. An outlier is something that occurs rarely.** In this case, we’re increasing the amount of work that has to be done to generate our outliers versus our 80% or a high use case. **We do this by creating another collection called overflow to keep the outliers separate**. 

* **Overflow Collection** : **In the Outlier Pattern, we create another collection with the overflow. Anything over the maximum set for the bucket size would go into the documents overflow collection**. The overflow collection would be very sparsely used, given our data.
* Now, because we're creating another collection, that means **we also need to represent a new code path.** We have to write a new code path in order to access those overflows. **There is additional work** when it comes to that layer pattern, but this is **really useful for releasing things in phases.**

- ([34:35](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2075s)) ([35:02](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2102s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/d22d2f76-ec24-4e43-a4d9-6e15ef21de62.jpeg)

## Bucket Vs outlier

The choice between the Bucket Pattern and the Outlier Pattern is made by looking at our data. **Your schema decisions *can and should* be  data driven.**

* For example, **if most users have between zero and 60 documents, *that gives us a size for our bucket.*** We determine our maximum by data-driven solutions.
  * We see that we have a very long tail after about 61 documents. It's very uncommon to have that many documents associated with the user.
* The Outlier Pattern would be useful for our outliers, which are very uncommon to have that many documents associated with the user.
* We **don't want an ever-growing array** because we have the possibility of hitting that 60-megabyte cap, and large documents are just unwieldy to manage.

### Migrating Vs New project

This is much easier to do when you have an existing project that you're migrating, than it is with brand new projects. But because we are migrating from an existing source, we have the **ability to create a histogram of our documents. We have existing customers**, and those customers each have documents associated with them, so **we can see what frequency we have different sizes of documents.**

- ([35:25](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2125s)) ([35:50](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2150s))([36:09](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2169s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/42cc6942-0eb8-43b0-aac5-0620596244e0.jpeg)

### Document collection use case

* Our _id references our user account. **We have a bucket that contains six documents.** Why six? In this case, **our display physically shows six documents**, and going back to our original idea that the **data should be stored as it's needed,** we need to display six documents so that's why we have a bucket of six.
* But  The document count said eight, so what do we do with the rest?
* This is the fundamental part of the bucket pattern. The bucket pattern allows us to keep two documents that look similar but have different sets of data. **We have a bucket of six and a bucket of two,** six plus two equals eight, so that gives us the total number of documents.
* You'll notice that the _id continues to reference the user. If we needed to get all documents for a user, **we could very quickly use a range query or regular expression to query based on _id to get all of those different documents.**
* **Now, there's also a timestamp.** We need some sort of value to differentiate because _id is a primary key, we can't just use the number 10,000. This is what the bucket pattern looks like, but we still need to make a choice.

- ([36:32](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2192s)) ([36:57](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2217s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/13483452-47be-4cd7-a666-c9a77d359755.jpeg)

- ([37:18](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2238s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/fe6e8c61-e115-4f41-ae71-12a148ecc868.jpeg)

* We can also use the overflow pattern. The overflow pattern represents this data exactly the same. **What we're doing is we're creating another collection with the overflow.**
* If you recall our original schema, we had six documents contained in an array, the bucket size that our maximum was set to six, for this example, and then anything up over six would go into the documents overflow collection. The documents overflow collection can also be represented in different ways and using different patterns. But here, what I'm doing is I'm creating a separate document for each overflow.
* **The overflow collection would be very sparsely used,** because given our data, we're looking at a long tail. Essentially, we come back to the idea that the representation is the same, **you just need to pick one.**

- ([37:46](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2266s))([38:17](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2297s))

![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/ed3a01fa-b3a1-4511-b6aa-9b968cf116ed.jpeg)

# Approximation pattern

**Approximation Pattern** in MongoDB to optimize CPU usage. 

1. **Problem** : A customer was experiencing high CPU usage (about 90%) due to a **hidden counter** in the footer of their site. **This counter issued an update statement every time a page was loaded, which was very frequent and resource-intensive (90% CPU).**
   1. There's a lot of work that gets involved for every single increment that happens potentially hundreds of thousands of times a second.
2. **Solution - Approximation Pattern** : This pattern is a facsimile (close enough) of an actual value and is useful when the exact value is not needed.
   1. For example, in the case of page visits, it **doesn’t matter if 1 million people versus 1,000,005 people** visited your site. The fact that it’s over a million is what matters.
3. The increment was done at a random interval, **leveraging the law of averages to ensure that the counter would be fairly accurate over time.**
4. **Result** : This significantly reduced the load on the server, bringing the CPU usage down from 90% to about 10% to 5%.

This pattern is particularly useful for things like page counters and Internet of Things applications, where exact counts are not necessary and reducing the load on the server is beneficial.


- ([38:38](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2318s)) ([39:34](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2374s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/52554301-7dc0-41d8-a132-365a73c79ddd.jpeg)

- ([39:53](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2393s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/b413ce49-582b-47d9-b70d-d89091c095ec.jpeg)

## **Implementation** :

In the original solution, an increment hit the database for every single page load. 

By using the Approximation Pattern, the number of actual increments was reduced by **incrementing by a much larger number.**

 For example, incrementing by 10 or 100 instead of 1. 

**This was done by creating a counts collection with a single document called page views that had a single count.**

Then you can see at the bottom, we only incremented at a random interval. The law of averages states that every 100 page loads, we're going to be updating our counter. Our **counter will be fairly accurate over time.** 

This is a way that we significantly reduced the amount of load on that server. We went from **90% down to probably about 10% to 5%** on that server.

- ([40:12](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2412s)) ([40:35](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2435s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/21b90e99-c049-4ed3-b5ea-d7af92044b3e.jpeg)

- ([40:57](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2457s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/ecaf59ce-4829-4386-9792-a5f6436eae27.jpeg)

Conclusion

- ([41:20](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2480s)) ([41:52](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2512s))

  ![img](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/8614bf48-46b3-4ce2-b655-2e30b65ede78.jpeg)
- ([41:59](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2519s)) ([42:26](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2546s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/d2c67b47-f78d-4b49-8743-df737ccc5685.jpeg)

- ([42:51](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2571s)) ([43:13](https://www.youtube.com/watch?v=bxw1AkH2aM4&t=2593s))

![](https://nc-cdn.oss-us-west-1.aliyuncs.com/denote/ytnoteext/ef63c672-0674-4734-9a60-cffa38524e03.jpeg)

-- With NoteGPT
