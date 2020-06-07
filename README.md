# BigdataPrinciples_3and4

## Chapter 1:
#### What is a Apache Thrlft?

It's a tool that can be used to define staticallytyped, enforceable schemas. It provides an interface definition language to describe theschema in terms of generic data types, and this description can later be used to auto-matically generate the actual implementation in multiple programming languages.


#### How we use the node in the SuperWebAnalytics.com?

The nodes in SuperWeb Analutics.com using Thirft unions  that can be used for nodes with a singe representations. And, the unions allow the schema to envolve as the data evolves. For example:

![Chapter3](https://user-images.githubusercontent.com/48557621/83958229-1955ae00-a835-11ea-9b7b-245521b5723d.PNG)


 #### What are the rules that i need to follow if i want to change the schema but still be backward compatible existing data?
 For this, we have 3 rules:
 #### 1.-Fields  may  be  renamed  because  the  serialized  form  of  an  object  uses  thefield IDs, not the names, to identify fields
 #### 2.-A  field  may  be  removed,  but  you  must  never  reuse  that  field  ID because the Thrift would try todeserialize that old data into the new field, which will lead to either invalid orincorrect data.
 #### 3.-Only  optional  fields  can  be  added  to  existing  structs because existing data won’t have those fields and thus won’t be deserializable.
