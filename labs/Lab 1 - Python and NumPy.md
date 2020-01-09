---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name
**Curly Zhao**


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


Are the markdown files auto updated when the notebook file is saved?

Are all variables in all code cells global? If yes, how do we create local variables?

What is the raw mode in notebook?


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np
a = np.ones((6, 4))
a[0:][0:] = 2
print(a)
```

## Exercise 2

```python
b = np.ones((6, 4))
np.fill_diagonal(b, 3)
print(b)
```

## Exercise 3

```python
c = a * b
print(c)
```

## Exercise 4

```python
d = np.dot(a.transpose(), b)
print(d)
e = np.dot(a, b.transpose())
print(e)
```

## Exercise 5

```python
def test(x, y):
    z = x*2 + y**2
    print(z)
test(3, 4)
```

## Exercise 6

```python
def arrayTest():
    a = np.random.randn(4, 3)
    b = np.random.randn(4, 3)
    c = np.random.randn(4, 3)
    print(a+b+c)
    print((a+b+c)/3)
arrayTest()
```

## Exercise 7

```python
def arrayCountOnes1(arr):
    num = 0
    for i in range(len(arr)):
        for j in range(len(arr[i])):
            if arr[i][j] == 1:
                num = num+1
    return num
print(arrayCountOnes1(b))
def arrayCountOnes2(arr):
    arr1 = np.where(arr == 1)
    num = len(arr[arr1])
    return num
print(arrayCountOnes2(b))
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd
df1 = pd.DataFrame(a, index = list(range(len(a))), columns = list(range(len(a[0]))))
print(df1)
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
df2 = pd.DataFrame(b, index = list(range(len(b))), columns = list(range(len(b[0]))))
print(df2)
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
df3 = pd.DataFrame(c, index = list(range(len(c))), columns = list(range(len(c[0]))))
print(df3)
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
def arrayCountOnesPanda(arr):
    df4 = pd.DataFrame(arr, index = list(range(len(arr))), columns = list(range(len(arr[0]))))
    df4 = df4[df4==1].count()
    return np.sum(df4.to_numpy())
print(arrayCountOnesPanda(b))
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df['name']
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
titanic_df.set_index('sex',inplace=True)
titanic_df.loc['female']
len(titanic_df.loc['female'])
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index(inplace=True)
```

```python
titanic_df
```
