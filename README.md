
# Being expressive with functions

### Learning objectives

* Learn about the definition of a function in the mathematical context.
* Understand what it means to say that a function depends on one or more variables.
* Understand how to express a function with several variables.
* Understand how to express a function that is composed of another function, and why it is useful to express functions that way.

### Introduction

Before, we have learned how to write functions in Python, and how functions are useful if you want to reuse written code. You also learned how to use arguments as inputs to a function, and how the value inserted as an argument changes the function outcome. 

Now, it's time to dig a little deeper and talk about the *mathematical* meaning of a function. In this lecture, it will become clear how this mathematical definition is related to the programming logic of a function. Some of these concepts may feel like review, but solidifying this foundation will provide clarity when we move on to explore other mathematical topics.

### Functions: an introductory example

Let's start with an introductory example. Imagine that you're a broker and assigend with renting out apartments in a big apartment block. There are apartments of various sizes and the price depends on the number of bedrooms. 

Talking more mathematically, we say that **the _price_ is a function of the _number of bedrooms_**. In mathematical terms, we generally like to express this as follows:

$$\text{price} = f(\text{number of bedrooms})$$
or, alternatively

$$ y = f(\text{x})$$

where $y$ is the price and $x$ is the number of bedrooms. This is purely naming convention, but you'll see often that 

- The **_output_** (also denoted **_dependent_** or **_response_** variable) is given by $y$. the output variable (here: the price) is a variable that depends on something else.
- The **_input_** (also denoted **_independent_** or **_explanatory_**) is given by $x$. The input variable is a variable that stands by itself, but triggers a change in the output variable (here: number of bedrooms).

Now let's say the price of the apartment is set in a very simplified way, and there is a perfectly linear relationship between the apartment size and the rental price. Say that the price goes up by 500 USD/month for every bedroom an apartment has. In that case, we can express the price as follows:


$$\text{price} = 500 * \text{number of bedrooms}$$
or
$$y = f(x) = 500 * x = 500x$$ 

Often, when using function notation, the multiplication sign "*" will be dropped.

### Link to functions in Python

Now, you'll see how mathematical functions relate to functions in Python. That's right: you can use Python functions to express how a mathematical functions! For the example above, a Python function can be written as:


```python
def f(x):
    return 500*x
```

Or, when programming, you might want to switch back to the more intuitive names:


```python
def price(n_bedrooms):
    return 500*n_bedrooms
```

You can see that
- The input variable is included in the function argument.
- The function returns the output variable.

### Evaluating functions at specific values

Now, let's evaluate the function $f(x)$ at specific values of $x$. The key to understand functions is to understand that "function of $x$" basically means that the function value changes, when $x$ changes. Note that, additionally, the same input value for $x$ will always return the same output from the function! 

For example, when $x = 3$, you get that $f(x=3) = 500*3 = 1500$. Interpreting this using our example, we can say that an apartment with 3 bedrooms is rented at a price of 1500 USD/month.

What about a 5-bed apartment? We can calculate this again, and we can also use our Python function to get to the result! we can use either our python function `f()` *or* `price()`


```python
f(5)
```




    2500




```python
price(5)
```




    2500



So far, it seems like a small step going from expressing a function in math to expressing a function in code!

### Functions with multiple inputs

When thinking of our previous example, it is pretty unrealistic to think that the number of bedrooms is the only factor affecting the rental price. In reality, several other factors will affect the final price. Let's assume for now that there is only one other factor affecting, the location, is affecting the house price. Say that we have information on a certain variable, being the **_location index_**, which can take a value from 0 to 10, going from considered "bad" neighborhoods to prime neigborhoods.

We then say that **the _price_ is a function of the _number of bedrooms_ and the _location index_**. In mathematical terms, we generally like to express this as follows:


$$\text{price} = f(\text{number of bedrooms, location index})$$
or, alternatively

$$ y = f(\text{x,z})$$

Here, $x$ and $y$ are defined as before, and $z$ is the location index.

-------------

--------------------

### Unpacking  the $x$ in  $f(x)$

So the $x$ part of $f(x)$ indicates that the function produces different outputs with different values of $x$.  As our values of $x$ change, the output of the function also changes.  By describing our function as $f(x)$, or as "a function of $x$", we also indicate that the same $x$ input always returns the same output from the function.  

Now take a look at another function:

$$ f = 3x + y$$

To determine this output, we need to know more than a specific value of $x$.  We also need to know the value of $y$.  So it's no longer the case that a specific input of $x$ always returns the same output from this function.  After all, if we fill in that x = 4, then $f = 3*4 + y$, and $f$ would still vary with different $y$ values. 

It is not just a specific input of $x$ that returns the same input, but specific inputs of $x$ *and $y$* that always return the same output.  We indicate this like so:

$$ f(x,y) = 3x + y$$


```python
def f(x,y):
    return 3*x + y
```

And to indicate that we are evaluating the function at specific values of $x$ and $y$, we write the following: 

$$ f(3,4) = 3*3 + 4 = 13$$


```python
f(3, 4)
```




    13



A function whose output depends on *multiple* variables, like $x$ and $y$, is called a **multivariable function**.

#### Test your knowledge

Take a look at a new function.  How would we express the function:

$$ f = 3x + 4$$

Is that a multi-variable function?  Well, while the number 4 influences the output of the function, we do not need to know anything but the value of $x$ in order to determine the output of the function.  So we still would express that function as a single variable function:

$$ f(x) = 3x + 4$$

And in code:


```python
def f(x):
    return 3*x + 4
```

### Unpacking  the $f$ in  $f(x)$

Now that we understand the significance of $x$ in $f(x)$ what does the $f$ mean?  Well not too much.  It just a label for a specific function.  We could easily written our previous function as:

$$ g(x) = 3x + 4$$

You will see functions labeled differently, $f(x)$, $g(x)$, $J(x)$.  This is just a way of labeling the function, similar to how we name our functions in code.  For example, we can assign:

$$ f(x) = 10x + 12 $$

$$ g(x) = x + 100 $$

Later on, we can reference the second function, $g(x)$, and know which function we're referring to.

### Functions depending on other functions

Now that we know how to label different functions, we can also take a look at what it means for functions to depend on other functions.  In code, we see this all of the time.  For example, here is a function that we have solved before.


```python
def squared_error(actual, expected):
    return (actual - expected)**2

squared_error(4, 2)
```




    4



But we can really break this function into two:


```python
def error(actual, expected):
    return actual - expected
    
def squared_error(actual, expected):
    return error(actual, expected)**2

squared_error(4, 2)
```




    4



In code, composing our functions from other functions helps us break down a problem.  It will be easier for us understand our code when we refer to it later on.  Similarly, functional composition in mathematics can also help break down problems and assist with readability.  Here is how we express it.  Let's represent the function `error` as $g(x, y) = x - y $, where $x$ represents actual and $y$ represents expected. 

$$g(x, y) = x - y  $$

Now we can represent squared error as the following.

$$ f(g(x, y)) = g(x, y) ^2 $$

Take a close look at this second function.  We are expressing that this second function, $f$, depends on $g(x, y)$ and thus also depends on $x$ and $y$.  The output of the function $f$ will vary according to a few inputs.  As we'll see soon, functional composition helps us break down some complex problems.  But really, we're just saying that to determine what $f(g(x,y))$ will output, we need to know the variables $x$ and $y$ as well as the function $g(x, y)$.  This relationship is similar to our `squared_error` function because we need to know the `error` function, as well as the arguments of `actual` and `expected`.  

Let's see one more example to make sure that we have the hang of it.  Take the following function:

$$z(x) = (3 + 4x)^2$$  

Now let's try to represent with functional composition.  How?  Here's one way:

$$f(x) = 3 + 4x $$ 

$$ g(f(x)) = f(x)^2 $$

### Summary

In this section, we learned about expressing functions mathematically.  We saw that when what we call a function, the letter we use, whether $f$ or $g$ or $z$, doesn't matter.  We only are giving our function a name that we easily can refer to later on.  In the parentheses, we indicate what the output of the function is dependent on.  Sometimes the output of the function depends on one variable, and sometimes our function depends on multiple variables.  Sometimes our function depends on another *function*, whose output depends on other variables.  
