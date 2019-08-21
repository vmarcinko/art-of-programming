# Art of Programming

Every program ever could be sketched as having  things: **code** and **data**:

![Image1](images/code-and-data.png)

Data is **read** from some **input**, program **process** it in some way, and **writes** it to some **output**.

We could even present it via some pseudo-code:

```
    input-data = read-from-some-input();
    output-data = process-input(input-data);
    write-to-some-output(output-data);    
```

---

Imagine a program that plays a note when some key is pressed.

What is reading phase in it?

It's reading a data that represents specific key from keyboard input.  

What is processing phase?

It converts data that represents a key to data that represents a note.

And writing phase?

It writes data that represents a note to sound card output.

---

Imagine a program that draws a circle on the screen when a button is pressed.

What is the reading phase?

Reading the data that represents event about button being pressed.

What is processing phase?

Well, creating the data that represents a circle in some way.

And writing part?

Well, pushing this circle data to graphics card output.

---

Now, let's imagine a program, that
- reads a number from HTTP request
- creates record in SQL table about number received
- calculates result by incrementing a number by 1 if it is weekend, or increment by 2 if it's working day
- writes HTTP response with result number 

What read operations we have hear?

These are:
- reading data that represents HTTP request
- reading current time from hardware clock!

What processing phase operations we have hear?

Well, these are:
- extracting number from HTTP request data
- extracting data from time data that represents whether it is weekend or not  
- creating SQL command from received number to create a record in a SQL table
- calculating result by incrementing received number by desired increment
- creating HTTP response data that from calculated result number

And finally, what are output operations
- sending SQL command to SQL database
- writing HTTP response data to network

