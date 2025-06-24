
2025-06-24 10:44

Status:

Tags: [[notes/3 - Tags/design pattern|design pattern]] [[notes/3 - Tags/decorator design pattern|decorator design pattern]]
# Decorator Design Pattern
- The **Decorator Design Pattern** allows you to add new functionality to objects dynamically by wrapping them with decorator classes, without altering their structure.

![[decorator_design_pattern_explaination.png]]
- We have a base object with features say F1, we can wrap it around with a decorator which will increase its features by (F1+F2). This decorated object is inherently an object in itself and can be decorated again. This process can go till infinity. 

**Use Cases:**
- Pizza Shop (Base Pizza + Extra Toppings(Cheese, Olives, Extra Veggie, Jalapeño))
- Coffee (Base Coffee + Extra Toppings (Milk, cream ...))
- Car (Base Model + Extra Features (Seat Cover, sound system, floor mats, USB adapters))

**Why do we need Decorator Pattern ?**
- It solve the problem of **Class Explosion.** 
- Class explosion happens when you need to create a separate subclass for every possible combination of features or behaviors, leading to a large and unmanageable number of classes.  
- The decorator pattern solves this by allowing features to be combined dynamically at runtime, reducing the need for excessive subclassing.

![[decorator_design_pattern.png]]
```python
from abc import ABC, abstractmethod

# Base Component
class Pizza(ABC):
    @abstractmethod
    def get_description(self) -> str:
        pass

    @abstractmethod
    def get_cost(self) -> float:
        pass

# Concrete Component
class Margherita(Pizza):
    def get_description(self) -> str:
        return "Margherita"

    def get_cost(self) -> float:
        return 10.0

# Decorator Base
class ToppingDecorator(Pizza):
    def __init__(self, pizza: Pizza):
        self.pizza = pizza

    @abstractmethod
    def get_description(self) -> str:
        pass

    @abstractmethod
    def get_cost(self) -> float:
        pass

# Concrete Decorators
class Cheese(ToppingDecorator):
    def get_description(self) -> str:
        return self.pizza.get_description() + ", Cheese"

    def get_cost(self) -> float:
        return self.pizza.get_cost() + 1.0

class Olives(ToppingDecorator):
    def get_description(self) -> str:
        return self.pizza.get_description() + ", Olives"

    def get_cost(self) -> float:
        return self.pizza.get_cost() + 0.5

# Usage
if __name__ == "__main__":
    pizza = Margherita()
    print(pizza.get_description(), ":", pizza.get_cost())

    pizza_with_cheese = Cheese(pizza)
    print(pizza_with_cheese.get_description(), ":", pizza_with_cheese.get_cost())

    pizza_with_cheese_and_olives = Olives(pizza_with_cheese)
    print(pizza_with_cheese_and_olives.get_description(), ":", pizza_with_cheese_and_olives.get_cost())
```
### **Abstract Methods in Base and Subclasses**

- When you declare a method as `@abstractmethod` in a base class (like `Pizza`), you are saying:  
    “Any concrete subclass must implement this method.”
    
- If a subclass (like `ToppingDecorator`) **does not** implement the abstract methods, but also declares itself as abstract (by inheriting from `ABC` or having its own `@abstractmethod`), it **does not have to** implement those methods yet.
    
#### **Implications:**

- You **cannot instantiate** an abstract class (one with unimplemented abstract methods).
- Only the **first concrete subclass** (one that implements all abstract methods) can be instantiated.

#### **Why do this?**

- This is useful when you want to create an **abstract hierarchy**:
    - The base class (`Pizza`) defines the interface.
    - An intermediate abstract class (`ToppingDecorator`) may add some shared logic or fields, but still leaves some methods abstract.
    - Only the final concrete classes (like `Cheese`, `Olives`) implement all methods and can be instantiated.
#### **When do we do it?**

- When you want to **enforce a contract** across several layers of inheritance.
- When you want to provide **shared code** in an intermediate class, but still require subclasses to implement certain methods.

---
### **Example in Your Code**

- `Pizza` is abstract: defines `get_description` and `get_cost` as abstract.
- `ToppingDecorator` is also abstract: it does not implement those methods, so it stays abstract.
- Only concrete decorators (like `Cheese`, `Olives`) implement all methods and can be instantiated.
### **Summary Table**

| Class              | Implements all abstract methods? | Can be instantiated? | Purpose                                 |
| ------------------ | :------------------------------: | :------------------: | --------------------------------------- |
| `Pizza`            |                No                |          No          | Defines the interface                   |
| `ToppingDecorator` |                No                |          No          | Adds shared logic, still abstract       |
| `Cheese`/`Olives`  |               Yes                |         Yes          | Concrete, can be used to create objects |

## Python Decorators Vs Decorator Design Pattern

**Decorator Design Pattern** and **Python decorators** are related concepts but serve different purposes:

---
### Decorator Design Pattern (OOP Concept)

- **What:** A structural design pattern that allows you to add new behavior to objects dynamically by wrapping them with decorator classes.
- **How:** You create a base interface/class, concrete components, and decorator classes that extend the base and wrap components.
- **Use case:** Add features (like toppings to a pizza, scrollbars to a window) at runtime, without modifying the original class.
- **Example:** See the pizza and toppings example above.

---

### Python Decorators (Language Feature)

- **What:** A special syntax in Python (`@decorator`) for wrapping functions or methods to modify their behavior.
- **How:** You define a function (or class) that takes another function and returns a new function, often using closures.
- **Use case:** Add cross-cutting concerns (logging, timing, access control) to functions or methods in a reusable way.
- **Example:**
```python
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print("Before")
        result = func(*args, **kwargs)
        print("After")
        return result
    return wrapper

@my_decorator
def say_hello():
    print("Hello")
```
---
### Summary Table

|Aspect|Decorator Design Pattern|Python Decorators|
|---|---|---|
|Applies to|Objects (classes)|Functions/methods (and classes)|
|Purpose|Add behavior to objects|Add behavior to functions/methods|
|Implementation|Class-based, uses composition|Function-based, uses closures|
|Syntax|No special syntax|Uses `@decorator` syntax|
|Example use|GUI widgets, pizza toppings|Logging, timing, authentication|

---

**In short:**

- The Decorator Pattern is an OOP design pattern for objects.
- Python decorators are a language feature for functions/methods, inspired by the pattern but implemented differently.


# References
- https://sbcode.net/python/decorator/
- [Concept & Coding](https://www.youtube.com/watch?v=w6a9MXUwcfY&list=PL6W8uoQQ2c61X_9e6Net0WdYZidm7zooW)
