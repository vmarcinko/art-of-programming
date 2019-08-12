# DATA

---

In mathematics, we use data such as this:

    23, 0, -45, 3424242342

How do we call this type of data?

**Number**, or numerical data.

What are common operations that can be done with numbers:

Adding, subtracting, multiplying, comparing etc... Whole mathematics at our disposal.

---

Is this data:

    5.43
    -12.0004
    501.005

also of **number** type as previous ones:

    23
    0
    -45
    3424242342
  
?

Yes. 

But they are also different in a way, right? How?

Yes. One example has data of **decimal** type and other one of **integer** type. But both of them are **number** type also.

So, "integer" and "decimal" belong to common type "number". How do we call a type that is part of some larger type?

A subtype.

---

How do we call type of following data?

    Blah
    A
    John Doe
    This is my first sentence

Text. Or **string**, in programming languages. 

OK, great, now we know 2 types of data: **number** and **string**.

What operations can be done with strings?

Splitting on certain position, comparison, removing portions of text, counting length of text, etc...

---

What is the type of following data?

    Yes/No
    0/1
    true/false

**Boolean**, or binary (in math).

What is the characteristics of boolean data?

We have data with just 2 possible values - one that defines truthy value, and other falsy.

What operations are done on booleans?

Checking whether something is true or not, switching to opposite value, all binary operations etc...

OK, now we know one more primitive data type.

### Encodings

Again, what is this data type:

    -24.55

A number. Or more precisely, a decimal number. OK.

But, what about this:

    -24AA.55

A string.

Why?

Because decimal number type cannot contain letters (AA), only a string can have it.

OK, and if -24AA.55 is a string, and we remove one A, we get -24A.55. What data type is this?

Still a string.

And if we remove one A more from -24A.55, we get -24.55. Is this still a string?

Weeeeeell.....yes, but we mostly think of it as a number.

But why it also can be a string?

Because string can also consist entirely of numbers.

And what about this - is this a string or a boolean then?

    true

Well, it can be either also, but we mostly think of it as boolean, because this is kinda "common word" in most programming languages to represent boolean value.

Because we want to remove ambiguity between strings and other data types, let's introduce special character 
to mark something as a string, and let's pick a double quote, such as:

    "This is a string"
    "true"
    "-23.45"   

Could have we picked a single quote instead of double quote?

Yes, of course. We could've picked any character we wanted - this is our textual format, we can decide however we want to represent something. 

The way we write different data values is called **encoding**, or more precisely, **textual encoding** 
because we're writing them here as sequence of characters, unlike **binary encoding** where we can write 
data as sequence of bytes.

We demonstrated how we use special character to designate special data type in textual encoding 
(example String above), so how could we designate special data type in binary encoding?

Similar - with some special byte that marks the data type! Maybe something like having prefix byte value:
- 0 - following 4 bytes are integer
- 1 - following 8 bytes are for decimal
- 2 - following 1 byte is boolean
- 3 - following 1 byte specifies string length N, and then N bytes are string

What type of encoding (textual or binary) is more compact, meaning, encoded form is smaller?

Binary. Since it is more compact, it's usually faster to read/write.

What type of encoding is easier to read?

Textual of course! That's mostly the reason why nowadays the most popular formats for program communication are 
text ones (JSON, XML).

Also, programs are mostly written in text files, and they have data encoded in them also, such as:

    var a = 'true'
    var b = true;

---

OK, some examples from real life... 
Say you want to have data that represents someone's **name** (eg. Johanna Smith), what data type you would choose?

A string.

And in case of data to represent person **description**?

String again.

And someone's **age**?

A number.

And what number subtype - integer or decimal? Why?

Integer, because we never use decimal precision for age values.

And to represent if someone is employed? What data type would you choose now and why?

Boolean type, because a person can only have 2 possible values here - employed or unemployed. Positive or negative.

### Collections

Up until now, we were learning about few so called **primitive data types**. 
But sometimes we want more **complex** data values, acting as **collections** of mentioned primitive data values.
Let's say we have a bunch of numbers:

    22, 3, -300, 56, 1, 0, 11

If you want to have a collection value that contains all these numbers, and it is important:
- that each element has a position in it, meaning, elements are ordered by position, and allows duplicates, then we use a **list** data type
- that element position does not exist, thus no ordering is present when reading from it, and there are no duplicate values in it, then we use a **set** data type (like mathematical set)

OK, so again, let's say we have a **list** that contains following numerical elements:

    22, 3, -300, 0, 1
    
What is the size of such list?

It's 5.

What is the element in position 0?

It's 22, because first position in list is under position (or frequently called "index") 0.

What is the element under position 1?

It's 3

And under position 5?

There is no element under position 5, since whole list contains 5 elements, so largest position is 4.

And if we add number 22 to this list, what is the size of such list?

It would be 6.

---

Ok, so imagine now the same bunch of numbers present in a **set**:

    22, 3, -300, 0, 1
    
Remember, order of elements is not present, and there are no duplicates.

What is the size of such set?

It's 5.

What is element at position 0?

It's impossible to fetch such element, because set doesn't have positions, doesn't have any order, just like math sets, usually drawn as circles around elements.

And if we add number 22 to this list, what is the size of such list?

It's still 5, since a set doesn't allow duplicates, and we already have element 22.

Currently, again, as with case with strings and other data types, we don't have textual way to differentiate between a list and a set, 
so let's introduce special characters for that, **[ el1, el2, ... ]** for a list, and **#{ el1, el2, ... }** for a set, something like:

     [ 22, 3, -300, 0, 1 ]      (list)
    #{ 22, 3, -300, 0, 1 }      (set)

Can a list or set have no elements?

Of course, here they are:

     [ ]      (empty list)
    #{ }      (empty set)
    
---

OK, now we come to one of most important collection data types.
In your life, you probably filled countless paper forms with your personal data. 
Let's say we have a following person data, such as:

    "id":         4413,
    "name":       "John Doe",
    "age":        56,
    "employed":   true

You notice that this complex piece of data has **key-value**, or **name-value**, structure. Each **key (name)** has a **value** associated with it.  
We call such data type a **map**, and it is another collection data type we introduced (previous ones are list and set).

Actually, for same reason already mentioned in case of **string, list or set**, let's use some special characters to 
define a map - **{ ... }**, so we would have following:

    {
        "id":         4413,
        "name":       "John Doe",
        "age":        56,
        "employed":   true
    }

So, how many **keys** (person **attributes**) does the person map above has?

There are 4. It's **id, name, age, employed**.

And what are keys in this map?

    { "id": 4413, "name": "John Doe", "age": 56, "employed": true }

It's **id, name, age, employed** again, it's the same map, just written in single line.

And what is data type of these keys - id, name, age...? (warning - question is about key type, not value type)

It's a string.

Does it make sense for a map to have duplicate keys, such as "age" being present 2 times, for example:

    {
        "id":         4413,
        "name":       "John Doe",
        "age":        56,
        "employed":   true,
        "age":        16,
    }

No, we wouldn't know what the actual value of attribute "age" is then. 
A map cannot contain duplicate keys.

What's the value under key "employed"?

It's **true**.

What data type that is?

It's boolean.

What's value under key "name", and what is its type?

It's "John Doe", and it's a string.

And if we want to introduce new "nickname" attribute, what type it would be?

A string of course, something like:

    {
        "id":         4413,
        "name":       "John Doe",
        "age":        56,
        "employed":   true,
        "nickname":   "Johny"
    }

But some people don't have a nickname - how will we represent that then? Should we just omit this "nickname" key then?

Yes, that's one possibility. But if we decide to keep this key, what do we need then?

Some special value that means "nothing" - a **null** (or **nil** sometimes) is mostly used for that:

    {
        "id":         4413,
        "name":       "John Doe",
        "age":        56,
        "employed":   true,
        "nickname":   null
    }

Such attributes that can have no value we call **optional** attributes. 
  
But, as we know, a person can have also multiple nicknames, say

    "Johny", "BigJ", "Maverick"

Do we need to change the name of "nickname" key?    

Of course, it should be "nicknames" now, instead of "nickname"! Names are really important in programming, 
they should always reflect their meaning.

And what about its data type? Should it be one of collection data types (list, set, map) 
or a primitive (boolean, string, number...)?

Definitely a collection, because we have multiple nicknames (*Johny, BigJ, Maverick*), not just a single value.

OK, so some collection is needed here. Should it be a map? Why?

Not a map, because map is of key-value structure, and here we just have multiple values, 
we don't have a need for keys here.

So - it comes down to a list or a set ? Which one?

Well, both would work, but a **set** would suit better, because we don't want duplicates here 
(same nicknames duplicated - such as *Johny, BigJ, Maverick, BigJ*), and we don't care about ordering/positions when we read it.

So if we add "nicknames" set attribute to a person map, we will end up with following map value:

    {
        "id":         4413,
        "name":       "John Doe",
        "age":        56,
        "employed":   true,
        "nicknames":  #{ "Johny", "BigJ", "Maverick" }
    }

What if we wanted to specify person nicknames, but in order of importance, so that first is the most used, and the last one is least used nickname.
What data type would you use for such "nicknames" attribute ?

Well, the **list** is needed then, because someone who reads this data later will need to know what the order of nicknames in a list, otherwise, it wouldn't know which one is more important. 
Ordering is very important in such example. So instead of:

    "nicknames":  #{ "Johny", "BigJ", "Maverick" }

we would have something like:

    "nicknames":  [ "Johny", "BigJ", "Maverick" ]
    
But since we use a list now, can it happen that creator of such data mistakenly puts duplicate here - such as 

    "nicknames":  [ "Johny", "BigJ", "Maverick", "Johny" ]
?

Ahhh, yes, that would be bad, unlike a set, a list allows duplicates. Well, I guess this is the trade-off, and we only have 
a set or a list to pick from.

Let's go back to using a **set** for nicknames:

        "nicknames":  #{ "Johny", "BigJ", "Maverick" }

If a person doesn't have any nickname, how would we represent that?
- with **no key** ("nicknames") within a person map
- with **null** value - `"nicknames": null`
- with **empty set** value - `"nicknames": #{ }`
 
Actually, all 3 options would work, but... 
First 2 options would require additional description for anyone who reads the data to know what is the meaning of null value (or no key),  
whereas 3rd options is best one because empty set is normal value with already sufficiently precise meaning - no elements present in the set, so it would be best option. 

So rule of a thumb is:

    An empty list (or a set) should be preferred to null value to represent no elements in collection

Let's move on ... What do you think, can a **map** contain **another map** inside?

Sure, this is called **nesting**, or **embedding**, when one complex value contains another complex value.

For example, say we add a **spouse** attribute to our person:

    {
        "id":         4413,
        "name":       "John Doe",
        "age":        56,
        "employed":   true,
        "spouse":     {
                        "id":         741
                        "name":       "Johanna Smith"
                        "age":        51
                        "employed":   false
                      }
    }

And is a "spouse" attribute optional or not?

Marriage is optional, so I guess this attribute is optional also :-)

How would we represent that a person has no spouse?

With **null** value, or without "spouse" key, something like:

    "spouse": null 

As we said, map is a **key-value** data structure, and as in previous "person" example, 
a map is very often used to represent some **entity** which has its **attributes** (such as person with its attributes).

What would be **attributes**, for some **car** entity?

Something like vehicle manufacturer, model, serial number, production year etc...

An entity doesn't have to be just a real thing in this world. What does following map represents for example?

    {
        "type":         "block-bank-account",
        "account-id":   441234534,
        "reason":       "Money loundring detected via this account!"
    }

This seems like some type of **command**, or **request**, to block bank account. 
I guess. Mostly because "type" attribute has action in **imperative** form. 

And what about the next map?


    {
        "type":         "bank-account-blocked",
        "account-id":   441234534,
        "reason":       "Money loundring detected via this account!",
        "timestamp":    "2019-06-11 20:22:05"
    }

Well, this "type" field contains action **in past tense**, and a **timestamp** attribute, 
so this map represents something like an **event**, maybe due to previously executed command from previous example, right?

But a map can be used for other things also, not just for representing entities, and one frequent example is following. 
What data type is used for keys in this (a bit more complex) map?

    {
        4413:      {
                        "id":         4413
                        "name":       "John Doe"
                        "age":        56
                    },
        8913:       {
                        "id":         8913
                        "name":       "Rick Smith"
                        "age":        44
                    },
        7771:       {
                        "id":         7771
                        "name":       "Vince Salash"
                        "age":        13
                    }
    }

Yes, integer is key type in this map.

And what is the meaning of these keys in this map (Hint - take a look at person map associated with each key)?

Yes, these keys are actually person IDs. We could even call this whole map something like "person by ID map".
 
So, what would this map be good for?

It would be great for quick lookup of a person based on its ID.

And if we used person **name** (string) instead of **ID** as a key - what would it would be good for? 

For quick lookup of a person based on its name.
In general, such data structure is called an **index**, and maps are also frequently used for indexes, not just for entities.

When you hear word "index", what it mostly reminds you of?

A database, right! Actually, in overly simplistic terms, databases actually store similar "map-like" structures 
for each created index on disk, so the queries could find relevant data much faster if we search by some indexed columns (id, name ...). 
 
### Re-shaping the data

Lets' say we want to add **address** attribute to our initial person value. 
Let's pick a string as its data type, so we end up with a person such as:

    {
        "id":         4413
        "name":       "John Doe"
        "address":    "Elm Street, 123, Cleveland, Ohio, USA"        
        "age":        56
        "employed":   true
    }
    
And it's perfectly valid person map. But thing is, as we mentioned, we use different data types 
because they have different meaning, and provide different operations on them. So we aim to pick data type 
that is most plesant to work with. 

In case of an address, we will probably somewhere in our program want to read later an 
address' parts separately (city, street, state, country...) and process them in some way. 
For example, maybe we will validate whether country field is one of valid country names, 
and that street number is a positive integer etc...

Our address example:
    
    "Elm Street, 123, Cleveland, Ohio, USA"

is just a string - how would your program read separate address' parts?

Well, maybe you would split this single big string by commas, and hope that there are 5 parts. 
And also hoping that first part is street number, second part is street name, third part is city etc...
Basically, you hope that this string has some predefined format that a person entering it was holding onto.
Quite fragile idea, don't you think? 

Do we know some data type that already provides address' parts separately?

Yes, a **map**!

So, we can maybe decide to have address value as a map with 5 keys, it would maybe look like this:
    
    {
        "Street":         "Elm Street"
        "Street number":  123
        "City":           "Cleveland"
        "State":          "Ohio"
        "Country":        "USA"
    }
    
You probably also seen this countless times in those paper forms with multiple boxes for address' parts,  
where you had to enter your address. This data type has much better guarantees for valid data and is much more 
pleasant to process with our program compared to plain **string**.

But, if we take another look to the same value when given as single string value:

    "Elm Street, 123, Cleveland, Ohio, USA"

Compared to destructured map value, what is nice with this shape of data?

Yes, it's much shorter, and probably easier to read by human eye!
That's actually often the case, so there is a saying something like:

    Humans love strings and programs love maps.
    
That's why we often re-shape same data to better suit some new context. For example, when we want to present the 
address on some user interface, say web page, our programs will frequently format (convert) given address 
as single line string, to be easier to read.  

### Entity types

We said earlier than a map is often used to represent some entity, such as a person, a company, a car, whatever.
Imagine we have a list of such entities, such as a list of people, and each person has only 2 attributes - "name" and "email":

    [ 
        { "name": "John Doe", "email": "john@gmail.com" }, 
        { "name": "Johanna Smith", "email": "johanna@yahoo.com" },
        { "name": "Rick Tracy", "email": "rick@facebook.com" }
    ]
It's easy to imagine some code that would read such a person list, and do something with it, like send email to each person in the list.

But what if we have some **list of mixed entities**, let's say people **and** cars, and a car naturally has 
different attributes ("model" and "year"):

    [ 
        { "name": "John Doe", "email": "john@gmail.com" }, 
        { "model": "Ford C-Max", "year": 2009 },
        { "model": "Peugeot 206", "year": 2012 },
        { "name": "Rick Tracy", "email": "rick@facebook.com" }
    ]

Now, imagine some code would read this list, loop over it, and for each element do some type-specific action:
- if element is a person, send email with person information
- if element is a car, generate PDF file with its car information

How would you check if list element is of specific type - a person or a car?

Well, maybe first check if element map has "name" key - if it does, it is a person, and if not, then it is a car.

Hmmm, OK, that would work. But imagine if car would rename its "model" key into "name", then **both** person and car would have "name" key.
What then?
   
Hmmm, a problem, maybe by "year", or "email" key then?

Yeah, but same problem with "name"/"model" is present here, you never know when different entities have same map keys, 
or when they decide to rename it later. Good programming is much about introducing making explicit concepts that are important. 
So, what about introducing special **type** key:

    [ 
        { "type": "PERSON", "name": "John Doe", "email": "john@gmail.com" }, 
        { "type": "CAR",  "model": "Ford C-Max", "year": 2009 },
        { "type": "CAR", "model": "Peugeot 3008", "year": 2012 },
        { "type": "PERSON", "name": "Rick Tracy", "email": "rick@facebook.com" }
    ]

Differentiation is easy now, right? It doesn't depend on fragile entity attributes. 
Now our code would look like:
- if element's "type" equals "PERSON", send email with person information
- if element's "type" equals "CAR", generate PDF file with car information

But... let's say a car entity, beside "model" and "year", also needs a **type** attribute that defines 
whether the car is SUV, limousine or some other type of vehicle?
Can we use name "type" for this new key that is specific only to car entity? Something like:

    { "type": "CAR", "type": "LIMOUSINE", "model": "Ford C-Max", "year": 2009 }

No, because a map cannot have multiple keys with same name, and "type" is already used for entity type differentiation.

What shall we do then?

Yes, rename the problematic keys. So, should we rename already present entity "type" key into something else, 
say "entity-type", or should we introduce this new key under some other name like **"car-type"**?

    { "entity-type": "CAR", "type": "LIMOUSINE", "model": "Ford C-Max", "year": 2009 }
or    
    
    { "type": "CAR", "car-type": "LIMOUSINE", "model": "Ford C-Max", "year": 2009 }
      
Well, both would work, since in both cases we don't have same key name used.

But, let's say that we decide to rename "entity-type" into something like **"--type--"**:

    { "--type--": "CAR", "type": "LIMOUSINE", "model": "Ford C-Max", "year": 2009 }

How likely is it that some entity in the list has same attribute name as **"--type--"**?

Very unlikely.

Why?

Well, these special dash characters (**--**) are not likely to appear in attributes names, so very little chance for collision.

OK, well, that's a good thing, right? And, this **"--type--"** data, is this data one of entity's 
**natural attributes** (eg. person attributes, car attributes)? 

Well, no. It's more additional data attached to entity attributes, so our programs would easily differentiate entity type. 
Such data that additionally describe some other data, we call such data **meta data** - data about data.   

So, our complete list would look something like this:
   
    [ 
        { "--type--": "PERSON", "name": "John Doe", "email": "john@gmail.com" }, 
        { "--type--": "CAR", "type": "LIMOUSINE", "model": "Ford C-Max", "year": 2009 },
        { "--type--": "CAR", "type": "SUV", "model": "Peugeot 3008", "year": 2012 },
        { "--type--": "PERSON", "name": "Rick Tracy", "email": "rick@facebook.com" }
    ]

And if we separate this single list into 2 lists, each containing separate entity type (CAR, PERSON), 
do we need this **--type--** key?

No, it was needed when list contains entities of different types.

| --type-- | name       | email             | type      | model         | year |
|----------|------------|-------------------|-----------|---------------|------|
| PERSON   | John Doe   | john@gmail.com    |           |               |      |
| CAR      |            |                   | LIMOUSINE | Ford C-Max    | 2009 |
| CAR      |            |                   | SUV       | Peugeot 3008  | 2012 |
| PERSON   | Rick Tracy | rick@facebook.com |           |               |      |

### Schema

This **"--type--"** key in an entity map is actually very important in programming. 

Imagine someone writes down this kind of "CAR" value:

     { 
        "--type--":     "CAR",
        "model":        "Ford C-Max", 
        "year":         true 
     }

Just looking at a syntax, is this a **correctly written** map value?

Yes. Curly braces are here (**{ }**), we have a **key-value** structure, etc...

What is the type of "year" key (attribute)?

A boolean.

Is there anything that prevents someone using a boolean value for a "year" key in a map?

No.

Looking at following car map example:

     { 
         "--type--":    "CAR", 
         "model":       "Ford C-Max", 
         "has-wife":    true 
     }

Is there some **expected** key missing?

Yes, a "year".

And does "has-wife" attribute make any sense in this car example?

No.

Imagine you have a program that reads car map values written elsewhere. What would you like to happen 
when your program reads some unexpected car examples as above?

Well, it would be nice to check/validate whether such map value conforms to expectations about CAR maps, 
and report an error is it does not.
  
Let's bring back original example:

    { 
        "--type--":     "CAR", 
        "model":        "Ford C-Max", 
        "year":         2009 
    }

If the value of this "--type--" key is "CAR", what keys we **expect** to be present in such a map? 

"model" and "year".

What are their respective data types?

A string ("model") and integer ("year").

And what about optionality? What keys are optional?

Well, we never explicitly talked about it, but since we never used **null** for any such car map example, 
I guess both of them are mandatory (not optional).

And is this valid year value?

        "year":         -150 

Well, year in general can be negative (B.C.), but let's say we don't want to allow that here.

OK, so we can say that **definition of "CAR" type** is consists of following set of keys:
- "model" - string, not optional
- "year" - integer, not optional, only positive number

This kind of type definition is frequently called a **schema**.

For a moment, don't think how would we define it, but such a type definition, or a schema as we call it, 
what would it be good for? 

To be used for validation of car values (represented as maps).

Programs read data to to process it, to do something with it. Data validation is usually done immediately 
**after** reading the data, **before** processing it. Why?

To catch potential error in data as soon as possible, because the processing code can fail 
later due to invalid data and sometimes it's not easy to spot the cause and is much more costly to fix.

#### XML

Let's take a look at following XML data:

```xml
<car>
    <model>Ford C-Max</model>
    <year>2009</year>
</car>
```
Does XML format reminds you a bit of a map ? Why? 
 
Yes, it also has a **key-value** structure like a map, but in XML world, we don't call 
entries **key-value**, but **XML elements**. Each XML element has a name (key) and a value, 
such as `<model>Ford C-Max</model>`or `<year>2009</year>`.

Each XML must start with a root XML element, here it is a `<car>`. Do we have something like that in map?

No, a map doesn't have a root name/key/whatever, it just starts with curly braces **{ }**.

But still, this root XML element `car`, what does it reminds you of?

It's a bit like our **"--type--"** key! It is like a type name - CAR in this example.  

XML world has a way to define a **schema** for XML data and it's called **XML Schema**. 
Here's a schema example that we use to define car "type" (`<car>` XML element):

```xml
<xs:schema targetNamespace="http://www.mycompany.me/car" xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
    <xs:element name="car">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="model" type="xs:string" minOccurs="1" maxOccurs="1"/>
                <xs:element name="year" type="xs:integer" minOccurs="1" maxOccurs="1"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```  
ID of XML Schema above is `http://www.mycompany.me/car`, and in XML world, this ID is called a **namespace**.

Looking at this piece of schema which defines "year" XML element:

    <xs:element name="year" type="xs:integer" minOccurs="1" maxOccurs="1"/>

What does `type="xs:integer"` defines?

That "year" XML element must have **integer** value.

And what about `minOccurs="1" maxOccurs="1"`, what does that means?

That this element has to occur at least 1 time, and at most 1 time, which effectively means it is **required**!

And now we only change our car XML data to reference this schema by its namespace (`http://www.mycompany.me/car`):

```xml
<car xmlns="http://www.mycompany.me/car">
    <model>Ford C-Max</model>
    <year>2009</year>
</car>
```

Is this valid XML data above?

Well, it looks so.

And this one, is this valid XML?

```xml
<car xmlns="http://www.mycompany.me/car">
    <model>Ford C-Max</model>
    <year>-140</year>
</car>
```

No, since year is negative, and we said we would not allow negative years.

But looking at XML Schema definition for `<year>` XML element:

    <xs:element name="year" type="xs:integer" minOccurs="1" maxOccurs="1"/>
  
Does it prevent negative values?

No, negative integer is allowed by this XML Schema. So how will we validate that value?

Well, we can do 2 things:
- validate with XML Schema if it has necessary feature
- validate with the custom code

Actually, XML Schema is quite rich technology, so it has such possibility:

```xml   
<xs:element name="year" minOccurs="1" maxOccurs="1">
    <xs:simpleType>
        <xs:restriction base="xs:integer">
          <xs:minInclusive value="0"/>
        </xs:restriction>
      </xs:simpleType>
</xs:element>
```

#### SQL

Let's say we have "CAR" table within some SQL database, and it has following data: 

| model         | year |
|---------------|------|
| Ford C-Max    | 2009 |
| Peugeot 3008  | 2012 |
| Peugeot 206   | 2001 |

Do you see some similarities here with a **map** data type ? Why?

Well, **table column** is similar to **map key**, and **record/row value** is same as **value** associated with the key. Such as:

    { "model": "Ford C-Max", "year": 2009 }

But table can have many rows. And if we say that single table row is like a map, what is whole table then?

It's a collection of maps, something like **set of maps**, or **list of maps**, something like:. 

    [
        { "model": "Ford C-Max",    "year": 2009 },
        { "model": "Peugeot 3008",  "year": 2012 },
        { "model": "Peugeot 206",   "year": 2001 }
    ]

And in SQL table, is it possible to have some invalid value, such as invalid "year" value:

| model         | year |
|---------------|------|
| Ford C-Max    | 2009 |
| Peugeot 3008  | 2012 |
| Peugeot 206   | aaab |

?

No, it's not possible, because definition of SQL table prevents that.

OK, so let's say that "car" table given above is created with following statement:

```sql
CREATE TABLE car (
    model   VARCHAR(200)    NOT NULL, 
    year    INTEGER         NOT NULL
);
```

we can see that SQL table definition consists of:
 - set of possible columns
 - column data type
 - column optionality
 
Does this reminds you of something?

Yes, a **schema**! SQL table is basically a schema that prevents invalid map data (row) to be inserted in it.

Each SQL table, which we 

How do we insert new map data (row) into SQL table?

Using SQL INSERT command, such as:

```sql
INSERT INTO car (model, year) VALUES ('Ford C-Max', 2009);
INSERT INTO car (model, year) VALUES ('Peugeot 208', 2017);
```

#### Java programming language

Java, as most of modern statically-typed languages, uses **classes** as a schema, as a type definition.

So, if we want to specify "schema" for a car, having 2 attributes: model (string) and a year (integer), we create a Car class such as this:

```java
public class Car {
	public String model;
	public int year;
}
```

You can see how we specified 2 attributes, and their types (string and integer).

And then try to create invalid car value out of it, such as this:

 ```java
		Car car1 = new Car();
		car1.model = "Ford C-Max";
		car1.year = true;
```

Whn does validation of a car value written as above happens in Java language?

During compilation! It would fail with some message as following:

        incompatible types: boolean cannot be converted to int

Attribute "year" is defined in Car class such as this:

    	public int year;

Is there some definition here that would say it is mandatory (not optional)?

No, currently Java cannot specify that directly. It just defines what type it is.

So, should this Car value creation pass compiler check?
 
```java
		Car carValue1 = new Car();
		carValue1.model = "Ford C-Max";
```

Yes, unfortunately.

### Comparison

|      | map value | map key      | map key value    | schema           |
|------|-----------|--------------|------------------|------------------|
| JSON | json      | name         | value            |                  |
| CSV  | csv row   | column       | row column value |                  |
| XML  | xml       | element name | element value    | XML Schema       |
| SQL  | table row | column       | row column value | table definition |
| Java | object    | field        | field value      | class            |

### Garbage

Taking again previous example in shorter form:

    [ 
        { "--type--": "PERSON", "name": "John Doe", "email": "john@gmail.com" }, 
        { "--type--": "CAR", "model": "Ford C-Max", "year": 2009 }
    ]
---

Now, let's get back to our complete person value:

    {
        "id":             4413
        "name":           "John Doe"
        "address":        {
                            "Street":         "Elm Street"
                            "Street number":  123
                            "City":           "Cleveland"
                            "State":          "Ohio"
                            "Country":        "USA"
                        }
        "age":            56
        "employed":       true
    }

### Flattening nested map into tabular data (SQL?)
### CSV, Excel vs SQL?

### Reshaping data for better usability
- list into map as index
- date string into map
- address string into map
### map "types"
### Bytes as data type, binary vs textual representation

## Type system Comparison table - xml, java, json, map, sql