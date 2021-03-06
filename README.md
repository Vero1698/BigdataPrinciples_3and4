# BigdataPrinciples_3and4

## Chapter 1:
#### 1.-What is a Apache Thrlft?

It's a tool that can be used to define staticallytyped, enforceable schemas. It provides an interface definition language to describe theschema in terms of generic data types, and this description can later be used to auto-matically generate the actual implementation in multiple programming languages.


#### 2.-How we use the node in the SuperWebAnalytics.com?

The nodes in SuperWeb Analutics.com using Thirft unions  that can be used for nodes with a singe representations. And, the unions allow the schema to envolve as the data evolves. For example:

![Chapter3](https://user-images.githubusercontent.com/48557621/83958229-1955ae00-a835-11ea-9b7b-245521b5723d.PNG)


 #### 3.-What are the rules that i need to follow if i want to change the schema but still be backward compatible existing data?
 For this, we have 3 rules:
 
 1.-Fields  may  be  renamed  because  the  serialized  form  of  an  object  uses  thefield IDs, not the names, to identify fields
 
  2.-A  field  may  be  removed,  but  you  must  never  reuse  that  field  ID because the Thrift would try todeserialize that old data into the new field, which will lead to either invalid orincorrect data.
  
3.-Only  optional  fields  can  be  added  to  existing  structs because existing data won’t have those fields and thus won’t be deserializable.

#### 4.-What is the key envolving Thrift Schemas? Describe it.

The numeric identifies associated with each field, and they used to identify fields in their serialized form.


#### 5.-what is the importance of checking the extra properties at the beginning of your batch processing workflow?

Check the extra properties of batch processing help to would split your dataset into "valid data" and "invalid data", after, this it would be sent you a notification if you have a invalid data. So, this step would be help you to makes easier to imple-ment the rest of yourr workflow because it take that you have the stricter properties you care about it, but, the problem can be this step doesnt help to determine the context where the corruption happened.


## Chapter 2
#### 6.- What are the storage requirements for the master data set? And Describe it.

Efficient appends of new data:it must be easy and efficient to append a new set of data objects to the master dataset.

Scalable storage: The batch layer stores the complete dataset—potentially terabytes or peta-bytes of data. It must therefore be easy to scale the storage.

Support for parallel processing: The batch storage must consequently support parallel pro-cessing to handle large amounts of data in a scalable manner.

Tunable storage and processing costs:  You may choose to compress your data to help mini-mize your expenses, but decompressing your data during computations can affect performance.

Enforce-able immu-tability: The best you can do is put checks in place to disallow mutable operations. These checks should prevent bugs or other random errors from trampling over existing data.


#### What can we use the vertical partition in a data set  and filesystem for?

The vertical partition is a partition of your data so that a function can access the data for calculation to make the batch layer of a data set more efficient, allowing large performance gains.
And , if we talk abou the filesystem, the vertical partition can be done by sorting yourdata into separate folders.

#### Why do distributed file systems become a problem in the short term?

The problems that can arise are:

1.- The addiction of master data sets, where accessing data from different folders can generate a serious problem when finding files with the same name, then the mv operation will fail.

2.- At the time of storing data, you choose a file format and compression, where when you find different formats, this process will fail absolutely and copy the records in a new folder into a new file with the file format used in master folder.

#### how can you make use of a distributed filesystem to store the masterdataset for SuperWebAnalytics.com?

 A key observation is that a graph schema provides a natural vertical partitioning ofthe data. You can store all edge and property types in their own folders. Vertically par-titioning the data this way lets you efficiently run computations that only look at cer-tain properties and edges






