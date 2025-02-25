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


Or, create a table:

| Name  | Age |
|-------|-----|
| Alice | 20  |
| Bob   | 21  |

# Overview about Funix

Funix is a python library which converts a python function or class definition into a webapp. Anything that has to be displayed on the screen has to be returned as a function(other than the text which is used for taking an input from the user).
Python objects get mapped to a widget through funix. This happens without manual widget creation in most cases, using its inbuilt type-to-widget mapping system.

Take a look at a basic python program which displays a person's name on the screen after taking it as an input on the webapp.
```python
import funix
def name(enter_your_name:str)->str:
    n=enter_your_name
    return n
```

This is its webapp:
![image](https://github.com/user-attachments/assets/635b5089-5a76-4a09-98b9-46fc284d4add)

The following is another program which has two functions. Notice how and we call the first function inside the first one.

```python
import funix
def No_of_characters_in_your_name(enter_your_name:str)->int:
    return len(enter_your_name)

def Calculate_Cost(Enter_your_name:str)->str:
    r=8
    n=No_of_characters_in_your_name(Enter_your_name)
    return(f"Cost of painting your name on the wall is: {r*n}Rs.")
```
On the Webapp:
![image](https://github.com/user-attachments/assets/7f5a401b-a961-47a7-96ca-f64f9e59f95b)
![image](https://github.com/user-attachments/assets/55fb3d81-c25d-4112-b702-bafa949c86b5)

Note: When we have multiple functions called independently(not nested), they appear separately on a menu bar on the left side of the page and have to be opened and executed separately. 

For obtaining the webapp for a python program:

1. First run the python file
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
