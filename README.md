# Docments
> Document parameters using comments.


`docments` provides programmatic access to comments in function parameters and return types. It can be used to create more developer-friendly documentation, CLI, etc tools. For instance, here is a function with docments-compatible comments:

```python
def add(
    a:int, # the 1st number to add
    b:int, # the 2nd number to add
)->int:    # the result of adding `a` to `b`
    "Add `a` to `b`"
    return a+b
```

The library provides one main function, also named `docments`, which returns a `dict` with the parameter names as keys, and comments as values. The return value comment appears in the `return`.

```python
docments(add)
```




    {'return': 'the result of adding `a` to `b`',
     'a': 'the 1st number to add',
     'b': 'the 2nd number to add'}



This is the same format that `__annotations__` uses in Python.

```python
add.__annotations__
```




    {'a': int, 'b': int, 'return': int}



## Install

Using pip:

    pip install docments

Using conda:

    conda install -c fastai docments

## Details

If you need more space document a parameter, place one or more lines of comments above the parameter, or above the return type:

```python
def add(
    a:int, # The first operand
    # This is the second of the operands to the *addition* operator.
    # Note that passing a negative value here is the equivalent of the *subtraction* operator.
    b:int,
    # The result is calculated using Python's builtin `+` operator.
    # Note that this can be overridden for types using the `__add__` magic method
)->int:
    "Add `a` to `b`"
    return a+b
```

```python
docments(add)
```




    {'return': "The result is calculated using Python's builtin `+` operator.\nNote that this can be overridden for types using the `__add__` magic method",
     'a': 'The first operand',
     'b': 'This is the second of the operands to the *addition* operator.\nNote that passing a negative value here is the equivalent of the *subtraction* operator.'}


