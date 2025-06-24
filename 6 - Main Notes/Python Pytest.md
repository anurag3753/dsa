
2025-06-10 08:46

Status:

Tags: [[pytest]]


# Python Pytest

### Pytest:
- `pytest` is a third-party library that allows you to unit test your program.
- It is a good idea to test all the corner-cases for your code & also those cases which can result in Exceptions.
- We should break our tests into multiple groups of test. Example for square() , it could be like: test_negative_number, test_positive_number, test_zero, test_string(Expecting it to raise Exception).
- `pytest` will not allow us to run tests as a folder simply with this file (or a whole set of files) alone without a special `__init__` file. In your terminal window, create this file by typing `code test/__init__.py`. Note the `test/` as before, as well as the double underscores on either side of `init`. Even leaving this `__init__.py` file empty, `pytest` is informed that the whole folder containing `__init__.py` has tests that can be run.

#### Pytest import mechanisms
- [Pytest reference page](https://docs.pytest.org/en/7.1.x/explanation/pythonpath.html?highlight=folder#pytest-import-mechanisms-and-sys-path-pythonpath) Important document to read.


#### Floating Point Testing
- pytest provides `pytest.approx()` to allow comparison of floating point numbers
```python
def test_float():
	"some_func(number) returns a float"
	"pytest.approx() allows for some approxmation comparison"
	assert some_func(number) == pytest.approx(number.decimal_digits)
	"The tolerance allowed by pytest can be controlled using argument - abs"
	assert some_func(number) == pytest.approx(number.decimal_digits, abs=1e-2)
	# 1e -2 = 1 * (10 ^ -2) Lower this value, stricter the check will be done.
```
# References
