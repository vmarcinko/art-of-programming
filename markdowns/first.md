# DATA

In mathematics, we use data such as this:

    23, 0, -45, 3424242342

How do we call this type of data?

**Number**, or numerical data.

---

Is this data:

    5.43
    -12.0004
    501.005

also of number type as previous ones:

    23
    0
    -45
    3424242342
  
?

Yes. 

But are they also of different type?

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

---

What is the type of following data?

    Yes/No
    0/1
    true/false

**Boolean**, or binary (in math).

What is the characteristics of boolean data?

We have data with just 2 possible values.

OK, now we know one more data type.

### Textual representation

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

OK, so all data values, regardless of their type, have their textual representation (string) so they can all be mistaken for string values, 
But we like different data types because they provide different meaning to the data, and also different operations.

What are common operations that can be done with numbers:

Adding, subtracting, multiplying, comparing etc... Whole mathematics at our disposal.

What operations can be done with strings?

Splitting on certain position, comparison, removing portions of text etc...

What operations are done on booleans?

Checking whether something is true or not, switching to opposite value, all binary operations etc...

Because we want to remove ambiguity between strings and other data types, let's introduce special characters 
to mark something as a string, and it would be double quotes, such as:

    "This is a string"
    "true"
    "-23.45"   

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
- that each element has a position in it, and allows duplicates, then we use a **list** data type
- that order of elements is not present, and there are no duplicates, then we use a **set** data type (like mathematical set)

OK, so again, let's say we have a **list** that contains following numerical elements:

    22, 3, -300, 56, 1, 0, 11
    
What is the size of such list?

It's 7.

What is the element in position 0?

It's 22, because first position in list is under position (or frequently called "index") 0.

What is the element under position 1?

It's 3

And under position 7?

There is no element under position 7, since whole list contains 7 elements, so last position is 6.

And if we add number 22 to this list, what is the size of such list?

It would be 8.

---

Ok, so imagine now the same bunch of numbers present in a **set**:

    22, 3, -300, 56, 1, 0, 11
    
Remember, order of elements is not present, and there are no duplicates.

What is the size of such set?

It's 7.

What is element at position 0?

It's impossible to fetch such element, because set doesn't have positions, doesn't have any order, just like math sets, usually drawn as circles around elements.

And if we add number 22 to this list, what is the size of such list?

It's still 7, since a set doesn't allow duplicates, and we already have element 22.

Currently, again, as with case with strings and other data types, we don't have textual way to differentiate between a list and a set, 
so let's introduce special characters for that, **[ el1, el2, ... ]** for a list, and **#{ el1, el2, ... }** for a set, something like:


    [ 22, 3, -300, 56, 1, 0, 11 ]       (list)
    #{ 22, 3, -300, 56, 1, 0, 11 }      (set)
    
---

OK, now we come to one of most important collection data types.
In your life, you probably filled countless paper forms with your personal data. 
Let's say we have a following person data, such as:

    id:             4413
    name:           "John Doe"
    age:            56
    employed:       true


You notice that this complex piece of data has **key-value**, or **name-value**, structure. Each key/name has a value associated with it.  
We call such data type a **map**, and it is another collection data type we introduced (previous ones are list and set).

So, how many **keys** (person **attributes**) does the person map above has?

There are 4. It's **id, name, age, employed**.

And what is data type of these keys - id, name, age...? (warning - question is about key type, not value type)

It's a string.

Does it make sense for a map to have duplicate keys, such as "age" being present 2 times, for example:

    id:             4413
    name:           "John Doe"
    age:            56
    employed:       true
    age:            16

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

    id:             4413
    name:           "John Doe"
    age:            56
    employed:       true
    nicknames:      #{ "Johny", "BigJ", "Maverick" }

### Nested structures

Let's take initial person map:

    id:             4413
    name:           John Doe
    age:            56
    employed:       true

Lets' say we want to add **address** attribute. Let's pick a string as its data type, 
so we end up with a person such as:

    id:             4413
    name:           "John Doe"
    address:        Elm Street, 123, Cleveland, Ohio, USA        
    age:            56
    employed:       true

And it's perfectly valid person map. But thing is, as we mentioned, we use different data types 
because they have different meaning, and provide different operations on them. So we pick data type 
that is most plesant to work with. 

In case of an address, we will probably somewhere in our program want to read later an 
address' parts separately (city, street, state, country...) and process them in some way. 
For example, maybe we will validate whether country field is one of valid country names, 
and that street number is a positive integer etc...

If address such as:
    
    Elm Street, 123, Cleveland, Ohio, USA

is just a string - how would you fetch separate address' parts?

Well, maybe you would split this single big string by commas, and hope that there are 5 parts. 
And also hoping that first part is street number, second part is street name, third part is city etc...
Basically, you hope that this string has some predefined format that a person entering it was holding onto.
Quite fragile idea, don't you think? 

Do we know some data type that already provides address' parts separately?

Yes, a **map**!

So, we can maybe decide to have address value as a map with 5 keys, it would maybe look like this:

    Street:         Elm Street
    Street number:  123
    City:           Cleveland
    State:          Ohio
    Country:        USA

You probably also seen this countless times in those paper forms with multiple boxes for address' parts,  
where you had to enter your address. This data type has much better guarantees for valid data and is much more 
pleasant to work with compared to plain **string**.    

Now, let's get bakc to our complete person value:

    id:             4413
    name:           "John Doe"
    address:        Street:         Elm Street
                    Street number:  123
                    City:           Cleveland
                    State:          Ohio
                    Country:        USA
    age:            56
    employed:       true

What we have here is a map (address value) **within** a map (person value). 
This is called **nesting**, or **embedding**, when one complex value contains another complex value.
Here, an address is embedded, or nested, within a person.
