
2025-06-26 21:53

Status:

Tags: [[dsa]] [[python]] [[syntax]]
# User Input

### Taking List Element as input
```python
my_list = input()
arr_of_ints = list(map(int, my_list.strip().split()))
```
---
### match keyword (introduced in 3.10+)
- This is the substitute for the `switch` in Python

```python
  name = input("What's your name? ")

  match name: 
      case "Harry" | "Hermione" | "Ron":
          print("Gryffindor")
      case "Draco":
          print("Slytherin")
      case _:
          print("Who?")
# | Much like or keyword, this allows us to check for multiple values in the same case statement.
```

```python
def get_media_type(filename):

    filename, filetype = get_parts(filename)
    
    match filetype:
        case "gif" | "png":
            return f"image/{filetype}"
        case "jpg" | "jpeg":
            return f"image/jpeg"
        case "txt":
            return "text/plain"
        case "pdf" | "zip":
            return f"application/{filetype}"
        case "" | _: # Note, how to check any empty case and for all case
            return "application/octet-stream"
```
---


# References
