---
title: "Funix Library"
description: "Welcome Post"
author: "J004-Siddhartha Hrishikesha Voleti, Vansh Lata, Madhvikaben Vasava"
date: "2/25/2025"
---


# Dataframe



```python
import pandas, matplotlib.pyplot
from numpy import arange, log
from numpy.random import random

def table_and_plot(
    df: pandas.DataFrame = pandas.DataFrame({
        "a": arange(500) + random(500)/5,
        "b": random(500)-0.5 + log(arange(500)+1),
        "c": log(arange(500)+1) })
    ) -> matplotlib.figure.Figure:

    fig = matplotlib.pyplot.figure()
    matplotlib.pyplot.plot(df["a"], df["b"], 'b')
    matplotlib.pyplot.plot(df["a"], df["c"], 'r')

    return fig

```

I can also write math equations:

$$
y = x^2
$$


I can create lists easily:

- One
- Two

I can also create numbered lists:

1. One
2. Two


Or, create a table:

| Name  | Age |
|-------|-----|
| Alice | 20  |
| Bob   | 21  |

# Overview about Funix

Funix is a python library which converts a python function or class definition into a webapp. Anything that has to be displayed on the screen has to be returned as a function(other than the text which is used for taking an input from the user).
Python objects get mapped to a widget through funix. This happens without manual widget creation in most cases, using its inbuilt type-to-widget mapping system.


For obtaining the webapp:

1. First run the program

2. On your terminal run the following program: ```funix {path_to_the_python_file_as_a_string}```

The same steps have been showed on a VS Code Terminal in the image below
![image](https://github.com/user-attachments/assets/8e841118-52a7-443d-817a-3f8c0a5efffd)

# Program for Plotting graphs

The following is a python program for choosing a function(out of three functions- sine,cosine and tangent), which also allows the user to set the amplitude(A), wave number(k), phase constant(c) for the function and the color of the graph(out of four choices).
```python
import funix
import matplotlib.pyplot as plt
import matplotlib.figure
import numpy

def Plot_Graphs(Function: funix.hint.Literal['A*tan(kx+c)', 'A*sin(kx+c)', "A*cos(kx+c)"],A: funix.hint.FloatSlider(0, 8, 0.1), k: funix.hint.FloatSlider(0, 10, 0.1), c: funix.hint.FloatSlider(0, 2*numpy.pi, 0.01),Colour: funix.hint.Literal['Blue', 'Green', 'Red','Black','Purple']) -> matplotlib.figure.Figure:
    fig=plt.figure()
    fn=Function
    x = numpy.linspace(0, 20, 200)
    if fn=="A*tan(kx+c)":
        plt.plot(x,A*(numpy.tan((k*x)+c)),color=Colour)
        plt.ylabel(f"{A}tan({k}x+{c})")
    elif fn=="A*sin(kx+c)":
        plt.plot(x,A*(numpy.sin((k*x)+c)),color=Colour)
        plt.ylabel(f"{A}sin({k}x+{c})")
    else:
        plt.plot(x,A*(numpy.cos((k*x)+c)),color=Colour)
        plt.ylabel(f"{A}cos({k}x+{c})")
    plt.xlabel("X-axis")
    
    return fig
```


This is how the webpage for it looks:
![image](https://github.com/user-attachments/assets/f9ed6943-a5ad-48e9-afed-f1c8ba5c8410)


Let's take a look at the function definition line of the above program:
```python
def Plot_Graphs(Function: funix.hint.Literal['A*tan(kx+c)', 'A*sin(kx+c)', "A*cos(kx+c)"],A: funix.hint.FloatSlider(0, 8, 0.1), k: funix.hint.FloatSlider(0, 10, 0.1), c: funix.hint.FloatSlider(0, 2*numpy.pi, 0.01),Colour: funix.hint.Literal['Blue', 'Green', 'Red','Black','Purple']) -> matplotlib.figure.Figure:
```
The ```->matplotlib.figure.Figure:``` specifies that the function has to return a ```matplotlib.figure.Figure``` object.

In the following line:
```A: funix.hint.FloatSlider(0, 8, 0.1), k: funix.hint.FloatSlider(0, 10, 0.1), c: funix.hint.FloatSlider(0, 2*numpy.pi, 0.01)```
A, k, and c are the float values set using the slider in the webpage.

Similarly in ```Function: funix.hint.Literal['A*tan(kx+c)', 'A*sin(kx+c)', "A*cos(kx+c)"]``` the variable ```Function``` stores the string variable chosen using the circle checkboxes in the webpage.
