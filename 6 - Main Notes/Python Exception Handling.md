
2025-06-07 20:02

Status:

Tags: [[python]] [[notes/3 - Tags/python exception handling|python exception handling]]
# Python Exception Handling

## Try-Catch-Else

- Else block gets executed only when the `try` is successful
- In below scenario, if we have written `x` print in code w/o else block, then when the exception occurs system will complain of the `x` got referenced before assignment.
```python
try:
    x = int(input("Enter x: "))
except ValueError as e:
    print("x is not an integer", e)
else:
    print(f"Value of x: {x}")
```

## Excepting Multiple Exceptions
```python
    try:
        parts = date.split(",")
    except (IndexError, ValueError, KeyError):
        return None
```

# References
