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
