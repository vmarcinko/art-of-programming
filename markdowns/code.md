## Code

Let's take this math function:
```
f(a, b) = a + b * 2; 
```

What is the name of the function?

It's called "f". 

How many **input** arguments it has?

It has 2 - "a" and "b".

What are their data type?

Well, these are numbers of course. Math is dealing with only such type of data.

And what is return data type?

Also a number.

This function "f" - what other functions it depends on?
Maybe it would look more obvious if we used other syntax for this function, such as:
```
f(a, b) = +(a, *(b, 2)); 
```

It depends on 2 functions - adding (+) and multiplication (*). 
We call such functions - **dependencies** of function f.

Where are these function + and * defined?

Nowhere, these are "primitive" functions.

Do these + and * functions care if/where they are used? Or in other words, are they somehow made only 
for usage in function "f" which depends on them currently?

Of course not, any other function can use + and * functions!   

If we define another function:
```
hoho(x) = f(x, 11); 
```

How many dependency functions this "hoho" function has?

It has one **dependency** - function "f".

Is function "f" made to be used only by function "hoho", or it can be used potentially by many other functions that need it?

Function "f" can be used by any other function.

And function "hoho", is it used currently by any function ?

No.

OK, generally speaking, do dependency functions know by themselves or care where and if they are used?

No.

And does any function knows what it depends on ?

Of course, function body is implemented using dependency functions. 
So if we present it with a graph, we can say that:

    (hoho) --- needs --> (f) --- needs --> (+) and (*) 

Function "hoho" is **user (or client)** of fucntion "f", and function "f" is **user of functions "+" and "***".
Functions "+" and "***" are dependencies of function "f" ,and function "f" is dependency of function "hoho".
And function "hoho" is not dependency of anyone currently because there is no **user** of function "hoho". 

Let's repeat the definition of the function "f":
```
f(a, b) = a + b * 2; 
```

We can say it does the following: it is a function that takes 2 arguments, it doubles the second one and adds it to a first one.

Could the function "f" then be implemented as like this:
```
f(a, b) = a + b + b; 
```

Yes, it's just another way to calculate the same result.

What functions it depends right now?

It depends only on function "+" now.

Ok, 

Function "hoho" we defined previously as this:
```
hoho(x) = f(x, 11); 
```

Does it care how function "f" is implemented now in different way? Meaning, does it care if function "f" uses implementation with "+" and "*" or just "+" to calculate its result?

No, it doesn't care. It just cares that for some input arguments it produces correct result, not how it is implemented.

OK, so we can say that **user** functions don't care how their dependencies are implemented as long as they produce correct result.

### Pure functions and side-effects

Until now, we only look at math functions, but programming is different then math, although it shares some concepts.

For example - does the program only deal with number data type?

Of curse not, we already leaned about some primitive (number, string, boolean) and complex (list, set, map) data types.

If we want to create a program that basically calculates the result of mentioned function "f":
```
f(a, b) = a + b * 2; 
```

Can you give some examples where these 2 input argument can come from?

Well, from any kind of input. For example:
- HTTP request (network)
- some file
- web form
- command line arguments when program was executed from terminal (eg. DOS prompt, Unix shell...)

Let's present this input reading function in some code such as:

    input-args-map = read-from-some-input();

How many arguments this function has?

Zero, it has none.

Do we have such function in math?

No, in math the function always has at least some input argument.

So now, our program function, in some pseudo-code, it would look like:
```
    input-args-map = read-from-some-input();
    result = f(input-args-map.a, input-args-map.b);
    ...
```
But we need somehow to push result number to some output. What kind of output examples can you list now:
- HTTP response (network)
- some file
- some web page
- console when the program was executed from terminal

So now our program would look like:
```
    input-args-map = read-from-some-input();
    result = f(input-args-map.a, input-args-map.b);
    write-to-some-output(result);
```

Or in other form:
- pull some data from input
- calculate result output data
- push result data to output

This **"pulling"** function, the result it provide, the input data, can it be different each time the function is called?

Yes, of course. One time it can read one data value, and another time it can be something else.

And what about our **"calculation"** function, our function "f":

    f(a, b) = a + b * 2; 

If we call such function with same argument multiple times, say:

    result = f (3, 4);
    
Will it always give same result regardless when it was called?

Yes, it will always give same result if arguments are the same - 3 and 4 in this case. 

And this **"push"** function, say it pushes the same result value, say number 33, as HTTP response back to 
requester program, does this push depend on say, state of network connection?

Yes, one time it can go through, and other time it can fail if connection broke.

And if **push** function is about writing same value to a file, can a hard drive be full 
in one moment and write fails, and other time it can pass well?

Yes, of course.

So, does a **push** function also depends on time?

Yes, it seems so.

Well, so **push** and **pull** functions are time-sensitive, and **calculation** function is not.

Which typo of functions is not found in math?

Those time-dependent functions - push or pull functions.

We call such time-dependent functions **side-effects**, or **actions**. Those math-like functions, **calculations** as we called them, 
are also frequently called **pure functions**, because their result depends solely on argument values - if the arguments are same, 
the result will always be the same.

When any program is started, it is basically a call to a single function, so let's wrap our previous code in a single **main** function:

```
    main () = 
        input-args-map = read-from-some-input();
        result = f(input-args-map.a, input-args-map.b);
        write-to-some-output(result);
```

How many arguments has this **main** function?

None.

How many **dependency** function it has?

It has 3.

Does it contain **side-effects** ?

Of course, those pull and push functions are side-effects.

And, does it contain any **pure functions**?

Yes, this function "f" which calculates the output result value, it is a pure function.

OK, so function "main" contains side-effects **and** pure function. So overall looking, is "main" function a **pure** one?

No, it is not pure. A function is pure when it doesn't have a single side-effect!

---

