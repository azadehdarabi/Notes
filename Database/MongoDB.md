
should create user in admin database

create admin  user:
`db.createUser({user: "admin", pwd: "admin", roles:[{role: "readWrite", db: "golmorad"}]})`

### **Terms you might not know:**

**graphical user interface (GUI)**: an interface through which a user interacts with electronic devices such as computers, hand-held devices and other appliance ([source](https://www.techopedia.com/definition/5435/graphical-user-interface-gui))

**JavaScript Object Notation (JSON)**: A lightweight data-interchange format that is easy for humans to read and write, and easy for machines to parse and generate. ([source](https://www.json.org/))

**integrated development environment (IDE)**: combines common activities of writing software into a single application, like editing source code, building executables, and debugging, which enables programmers to consolidate the different aspects of writing a computer program ([source](https://www.codecademy.com/articles/what-is-an-ide))

**NoSQL database**: originally referring to “non SQL” or “non-relational”, a database that provides a mechanism for storage and retrieval of data that is modeled in means other than the tabular relations used in relational databases ([source](https://en.wikipedia.org/wiki/NoSQL))

**on-premises** (also known as on-premise, and abbreviated “on-prem”): on-premise software that is installed and runs on computers on the premises of the person or organization using the software, rather than at a remote facility such as a server farm or cloud ([source](https://en.wikipedia.org/wiki/On-premises_software))

**SQL database** (also known as relational database): a collection of data items with pre-defined relationships between them. These items are organized as a set of tables with columns and rows. ([source](https://searchdatamanagement.techtarget.com/definition/relational-database))

# The MongoDB Basics: Databases, Collections & Documents

Data in MongoDB is made up of three types of components: **databases**, **collections**, and **documents**. The database sits at the top of the hierarchy, collections at the next level, and documents at the bottom.

![[Pasted image 20230805160846.png]]

A **database** provides a container for storing and organizing data.

Each database contains one or more collections, and each **collection** contains zero or more documents.

A database can contain multiple collections, but a collection cannot span multiple databases. Likewise, a collection can contain multiple documents, but a document cannot span multiple collections.

The **document**, which is comprised of field/value pairs, is at the heart of the MongoDB data structure. Most interactions with MongoDB occur at the document level.

A **field** can contain a single value, multiple fields, or multiple elements.

![[Pasted image 20230805161319.png]]

**scalar value**: a variable that holds one value at a time. It is a single component that assumes a range of number or string values.


![[Pasted image 20230805162321.png]]

