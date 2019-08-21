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

 