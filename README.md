# B-Tree-RDBMS-Indexing-main
Java Project made with the use of Java Libraries and core concepts like Java OOPS, Multithreading, Serialization, Java Swing, etc.

## Tech Stack Used
Java, Java Swing and AWT, and core Java Programming concepts like OOPS, Multithreading, Serialization, etc.

## Introduction and Aim of the Project

The relational database i.e. a database in the form of rows and columns is stored in the form of extents and data pages. The extents can be understood as folders and the data pages can be understood as files. So, each row is stored in the data page sequentially. Usually, the limit of a data page is 8KB. So, after a data page gets completely filled, the next row goes into a new data page. Usually, an extent can accomodate 8 data pages i.e. its size is usually limited to 64 KB. So, after an extent has accomodated 8 data pages, a new extent is created and a new data page is created and the further rows start getting stored from there.

### Table Scan Method
Now, if we want to search some data, the entire database is searched for it i.e. every extent, and every data page in those extents and every row in those data pages is searched. So, the time complexity of this searching is O(N) where N is the number of rows in the data base. This technique of searching the data is called Table Scan as the entire table is being scanned.

### Index Seek Method
We know that if the data has some particular indices attached to it, the searching becomes faster. We also know that arranging the data in the form of a Binary Tree makes searching faster. In a binary tree, the data in the left sub-tree of a node is smaller than its data and the data in the right sub-tree of a node is larger than it. So, a B-Tree has the same property but not just with 2 children, with multiple children. So, we create indices upon the attributes of the relational database and for each attribute, we maintain a seperate B-Tree that stores the indices. The data is present in the last level of the B-Tree and it tells us the exact location of the data. Exact location means the extent number, data page number and the row-offset of the data. So, we first have to reach the correct index and then that index helps us reach the data. Reaching the correct index means traversing the B-Tree and it takes O(logdN) (d is in the base of the log) time where d is the number of child nodes of a node in B-Tree and N is the number of rows in the database. Then, it tells us the exact location of the data which means it takes O(1) time to reach the data after we have reached the correct index. This technique of using indices to make searching faster is called Index Seek Method.

### Aim of the Project
So, the project aims at showing the differnce in speed and searching time of the Index Seek and Table Scan Searching methods and analyzing the advantages and siadvantages of both the methods.

### Advantage of Index Seek Over Table Scan
The advantage of Index Seek Method over the Table Scan method is very clear. The searching time is reduced from Linear to Logarithmic.

### Drawbacks of Index Seek
1. In index seek method, let us say that there are C number of columns (attributes). So, if we want to create indices upon every attribute, we will have to scan the entire data base C times initially for creating the indices. So, the entire database will be scanned for creating the indices every time. After this, the search upon the attribute using Index Seek method will always be logarithmic.
2. The second major drawback is extra space. We will create Index Pages. These index pages are nothing but the nodes of the B-Tree. So, extra space is used for making the searching faster.
