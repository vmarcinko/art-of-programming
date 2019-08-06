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
    
---

OK, now we come to one of most important collection data types.
In your life, you probably filled countless paper forms with your personal data. 
Let's say we have a following person data, such as:

    "id":         4413,
    "name":       "John Doe",
    "age":        56,
    "employed":   true

You notice that this complex piece of data has **key-value**, or **name-value**, structure. Each key/name has a value associated with it.  
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

Let's say a person has multiple nicknames, say

    "Johny", "BigJ", "Maverick"
    
, we have to decide what data type will we use...
Should it be one of collection data types (list, set, map) or a primitive (boolean, string, number...)?

Definitely a collection, because we have multiple nicknames, not just a single value.

OK, so some collection is needed here. Should it be a map? Why?

Not a map, because map is of key-value structure, and here we just have multiple values (*Johny, BigJ, Maverick*), 
we don't have a need for keys here.

So - it comes down to a list or a set ? Which one?

Well, both would work, but a set would suit better, because we don't want duplicates here 
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

Well, the list is needed then, because someone who reads this data later will need to know what the order of nicknames in a list, otherwise, it wouldn't know which one is more important. 
Ordering is very important in such example. So instead of:

    "nicknames":  #{ "Johny", "BigJ", "Maverick" }

we would have something like:

    "nicknames":  [ "Johny", "BigJ", "Maverick" ]
    
But since we use a list now, can it happen that creator of such data mistakenly puts duplicate here - such as 

    "nicknames":  [ "Johny", "BigJ", "Maverick", "Johny" ]
?

Ahhh, yes, that would be bad, unlike a set, a list allows duplicates. Well, I guess this is the trade-off, and we only have 
a set or a list to pick from. 

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
Imagine we have a list of such entities, such as a list of people:

    [ 
        { "name": "John Doe", "email": "john@gmail.com" }, 
        { "name": "Johanna Smith", "email": "johanna@yahoo.com" },
        { "name": "Rick Tracy", "email": "rick@facebook.com" }
    ]
It's easy to imagine some code that would read such a person list, and do something with it, like send email to each person element (a map) in the list

But what if we have some **list of mixed entities**, let's say people **and** cars :

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
or when they decide to rename it later. What about introducing special **type** key:

    [ 
        { "type": "PERSON", "name": "John Doe", "email": "john@gmail.com" }, 
        { "type": "CAR",  "model": "Ford C-Max", "year": 2009 },
        { "type": "CAR", "model": "Peugeot 2006", "year": 2012 },
        { "type": "PERSON", "name": "Rick Tracy", "email": "rick@facebook.com" }
    ]

Differentiation is easy now, right? Now our code would look like:
- if element's "type" equals "PERSON", send email with person information
- if element's "type" equals "CAR", generate PDF file with car information

If a car entity naturally has an **type** attribute that defines whether the car is SUV, limousine or some other type of vehicle?
Can we use name "type" for this new key that is specific only to car entity? Something like:

    { "type": "CAR", "type": "LIMOUSINE", "model": "Ford C-Max", "year": 2009 }

No, because a map cannot have multiple keys with same name, and "type" is already used for entity type differentiation.

So, should we rename already present entity "type" key into something else, say "entity-type", 
or should we introduce this new key under some other name like **"car-type"**?

    { "entity-type": "CAR", "type": "LIMOUSINE", "model": "Ford C-Max", "year": 2009 }
or    
    
    { "type": "CAR", "car-type": "LIMOUSINE", "model": "Ford C-Max", "year": 2009 }
      
Well, both would work, since in both cases we don't have same key name used.

But, let's say that we decide to rename "entity-type" into something like **"--type--"**? Like:

    { "--type--": "CAR", "type": "LIMOUSINE", "model": "Ford C-Max", "year": 2009 }

How likely is it that some entity in the list has same attribute name as **"--type--"**?

Very unlikely.

And, this **"--type--"** data, is this data one of natural entity attributes (eg. person attributes, car attributes)? 

Well, no. it's more additional data attached to entity attributes, so our programs would easily differentiate entity type. 
Such data that additionally describe some other data, we call such data **meta data** - data about data.   

So, our complete list would look something like this:
   
    [ 
        { "--type--": "PERSON", "name": "John Doe", "email": "john@gmail.com" }, 
        { "--type--": "CAR", "type": "LIMOUSINE", "model": "Ford C-Max", "year": 2009 },
        { "--type--": "CAR", "type": "SUV", "model": "Peugeot 2006", "year": 2012 },
        { "--type--": "PERSON", "name": "Rick Tracy", "email": "rick@facebook.com" }
    ]

Again, do we need such special "--type--" key if a list contains only entities of same type, say person list?

No, it is used solely when list contains entities of different types.

| --type-- | name       | email             | type      | model         | year |
|----------|------------|-------------------|-----------|---------------|------|
| PERSON   | John Doe   | john@gmail.com    |           |               |      |
| CAR      |            |                   | LIMOUSINE | Ford C-Max    | 2009 |
| CAR      |            |                   | SUV       | Peugeout 2006 | 2012 |
| PERSON   | Rick Tracy | rick@facebook.com |           |               |      |



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

### Map key optionality - null, empty list or set
### Flattening nested map
### Reshaping data for better usability
- list into map as index
- date string into map
- address string into map
### map "types"
### Bytes as data type, binary vs textual representation