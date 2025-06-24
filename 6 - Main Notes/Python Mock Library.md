
2025-06-12 19:17

Status:

Tags: [[python mock]] [[pytest]] [[python]]


# Python Mock Library

Mock Object is essentially a simulated object that mimics the behavior of some other real object.
Ex: An API, a Database, a Mail Server etc.

The idea behind mock object is that when testing our code we should don't want to test the functionality of an external API. We want to test the functionality of our own code.

### Example Scenario
Consider a function where we send a request to an API, receive a response, process this response, and perform some actions based on it. We want to test whether this entire flow functions correctly.

### Challenges with External APIs 
- **Unreliability**: The external API we depend on might fail or be unavailable. 
- **Bugs**: The API might have bugs or issues that persist for a few days.
- **Independence**: We do not want to test the API itself, nor do we want to rely on it to verify the functionality of our code.

## Solution: Mock Objects
To address these challenges, we can use mock objects that simulate the behavior of the API. By doing so, we can: 
- **Isolate Testing**: Focus on testing our own code, assuming the API works correctly.
- **Control Responses**: Create mock objects that mimic the expected responses from the API.
- **Ensure Reliability**: Test our code without being affected by the external API's availability or issues.
By using mock objects, we can confidently test our code's functionality and ensure it behaves as expected, regardless of the external API's state.

## Mock Objects
- One special thing about mock objects is that, whenever they are called their output is also a Mock Object.
- Mock Object syntax looks like this `Mock(*args, **kwargs)`, they can accept any number of arguments and keyword arguments.
- In python, we can mock the objects in 2 ways:
	- Using a decorator `mock.patch`(preferred)
	- Using a `with context` block
- We can set as many properties as possible inside a Mock Object (No restriction)
- We can define the `name` of a mock. This is useful for debugging. The name is propagated to child mocks.
- A special property called `return_value` can also be set on the mock object. It will then be returned upon calling the mock object. (And it will not create another mock object in this case.)
- Whenever we patch any object, its corresponding mock object is automatically passed to the test function as an argument.
- Always try to refer the dependencies used by your function through the package path which is in present inside the local scope, inside your test function.
```python
from unittest.mock import Mock

# Fundamentals
m = Mock() # Creates a mock object called `m`
m1 = m() # Creates another mock object `m1`. Call to a mock object creates another mock object
m = Mock(name="Learning Mocking") # When you print this obj, name will also be printed. This helps in debugging.
m = Mock(val1 = 3, val2 = 5, val3 = 6)
m.val1 # Will print 3 and similar process will work for others too.
m = Mock(val1 = 3, return_value = 5) # m() will always return 5
```

## Functions called on Mock Objects
This is the list of various functions that we can call upon the mock objects.
- `mock_obj.assert_called_once()`: It verifies if the mock object is called once during the test.
- `mock_obj.assert_called_with()`: It verifies if the function is called with the specified arguments.
- `mock_obj.call_args_list()`: It returns what calls were made to my mock object. And what arguments were passed inside those calls. The return value comes in form of a `list`.
- `mock_obj.assert_has_calls()`: It tells you which calls has been made to the . Check its usage in below example3.

### Example 1
```python
# sample.py
from dice import roll_dice

def guess_number(number):
    result =  roll_dice()
    if number == result:
        return "You won!"
    else:
        return "You lost!"
```

```python
# test_sample.py
import pytest
from unittest.mock import Mock, patch
from sample import guess_number

@patch("sample.roll_dice") # Provide package path of the function you want to mock
def test_guess_number(mock_roll_dice):
	mock_roll_dice = 3
	assert(guess_number(3)) == "You won!"
	mock_roll_dice.assert_called_once()

# After parameterizing the test
@pytest.mark.parametrize("_input,expected", [
    (3, "You won!"),
    (4, "You lost!")
])
@patch("sample.roll_dice")
def test_guess_number(mock_roll_dice, _input, expected):
    mock_roll_dice.return_value = 3
    assert guess_number(_input) == expected
    mock_roll_dice.assert_called_once()
```

### Example 2
```python
# sample.py
import requests

def get_ip():
    response = requests.get("https://httpbin.org/ip")
    if response.status_code == 200:
        return response.json()["origin"]
```
```python
# test_sample.py
from sample import get_ip

@patch("sample.requests.get")
def test_get_ip(mock_request_get):
    mock_response = Mock() # Writing Mock Object for response object
    mock_response.status_code = 200
    mock_response.json.return_value = {"origin": "0.0.0.0"}

    mock_request_get.return_value = mock_response

    assert get_ip() == "0.0.0.0"
    mock_request_get.assert_called_with("https://httpbin.org/ip")


@patch("sample.requests.get") # Optimized Way
def test_get_ip(mock_request_get):
    # Compact way of specifying return values on the mock objects
    mock_response = Mock(**{"status_code": 200, "json.return_value": {"origin": "0.0.0.0"}}) # Writing Mock Object for response object

    mock_request_get.return_value = mock_response

    assert get_ip() == "0.0.0.0"
    mock_request_get.assert_called_with("https://httpbin.org/ip")
```

##### Side Effect
- `mock_obj.sideeffect`: **Useful for raising exceptions or dynamically changing return values.**
	- You can't throw any exception using the `return_value`.
- You can also throw exceptions using `side_effect`.
- You can also specify a `custom` function that needs to be called whenever `side_effect` is called.
- Any parameter that you will pass in the function, will automatically get passed to the side effect function.
```python
def my_side_effect(num):
	return num+1

m = Mock()
m.side_effect = my_side_effect # passing a function reference to side_effect

print(m(3)) # Output 4
print(m(4)) # Output 5
```

### Example 3
```python
# sample.py. It is using two random functions. How to patch in this case
import random

def random_sum():
    a = random.randint(1, 10)
    b = random.randint(1, 7)
    return a + b
```

```python
# test_sample.py
from sample import random_sum

@patch("sample.random.randint")
def test_random_sum(mock_randint):
	mock_randint.side_effect = [1, 5] # a = 1, b = 5
	assert random_sum() == 6
	mock_randint.assert_has_calls([call(1, 10), call(1, 7)])
	# You need to match the actual arguments passed to the mocked function, not the values you want it to return.
```

### Example 4
```python
import time
import requests

def silly():
    params = {
        "timestamp": time.time(),
        "number": random.randint(1, 6)
    }

    response = requests.get("https://httpbin.org/get", params)
    if response.status_code == 200:
        return response.json()["args"]

```

- We need to mock 3 different dependencies in this example.
- `time.time()`, `randome.randint()`, `requests.get()`
```python
@patch("requests.get")
@patch("sample.random.randint")
@patch("sample.time.time")
def test_silly(mock_time, mock_randint, mock_requests_get):
    test_params = {
        "timestamp": 123,
        "number": 5 
    }
    mock_time.return_value = test_params["timestamp"]
    mock_randint.return_value = test_params["number"]
    mock_response = Mock(**{"status_code": 200, "json.return_value": {"args": test_params}})
    mock_requests_get.return_value = mock_response

    assert silly() == test_params
```
- Note the order in which the mocks are passed inside the function. The `lowest` defined should come `first` and so on.


# References

- [Indian Pythonista](https://www.youtube.com/watch?v=dw2eNCzwBkk&list=PLyb_C2HpOQSBWGekd7PfhHnb9GnqDgrxS&index=9) **Must Watch**
- [Advanced Mocking Indian Pythonista](https://www.youtube.com/watch?v=M46H4GIdfl0&list=PLyb_C2HpOQSBWGekd7PfhHnb9GnqDgrxS&index=10) **Must Watch**