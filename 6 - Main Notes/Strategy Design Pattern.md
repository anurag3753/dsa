
2025-06-23 18:45

Status:

Tags: [[notes/3 - Tags/design pattern|design pattern]] [[notes/3 - Tags/strategy design pattern|strategy design pattern]]
# Strategy Design Pattern
It is used whenever there are multiple algorithms/strategies to perform a particular task and which strategy to use is decided at the runtime. Basically, we encapsulate these strategies into separate classes and dynamically decide which one we want to use.

- The Strategy pattern is about having a choice of implementations that accomplish the same relative task.
- The particular strategies' algorithm is encapsulated in order to keep the implementation de coupled from the context.

**Use Case:**
1. **Payment Methods in E-commerce:**  
    Allow users to choose between different payment strategies (credit card, PayPal, bank transfer) at checkout.
2. **Sorting Algorithms:**  
    A program can switch between different sorting strategies (quick sort, merge sort, bubble sort) depending on data size or type.
3. **Compression Algorithms:**  
    File compression tools can use different compression strategies (ZIP, RAR, 7z) based on user preference.

![[strategy_design_pattern.png]]

```python
"""
Childs have same code. But that code is not available with Parent.
Hence, childs ends up implementing the same code. (Dupilcated)

Solution: Create an interface for the common code and create concrete classes
implementing the required feature mentioned in interface.
Create a reference of the Interface inside the main base class.
"""
from abc import ABC, abstractmethod

class IDriveStrategy(ABC):
    @abstractmethod
    def drive(self):
        "Implement the drive strategy."

class SportsDriveStrategy(IDriveStrategy):
    def drive(self):
        return "Implement the Sports Drive Strategy."

class PassengerDriveStrategy(IDriveStrategy):
    def drive(self):
        return "Implement the Passenger Drive Strategy."

class NewDriveStrategy(IDriveStrategy):
    def drive(self):
        return "Implement the Sports Drive Strategy in New Drive."

class Vehicle:
    def __init__(self, drive_strategy: IDriveStrategy):
        self.drive_obj = drive_strategy

    def drive(self):
        return self.drive_obj.drive()

class OffRoadVehicle(Vehicle):
    def __init__(self):
        super().__init__(NewDriveStrategy())

class SportsRoadVehicle(Vehicle):
    def __init__(self):
        super().__init__(SportsDriveStrategy())

class CityVehicle(Vehicle):
    def __init__(self):
        super().__init__(PassengerDriveStrategy())

# Example usage:
if __name__ == "__main__":
    offroad = OffRoadVehicle()
    print(offroad.drive())  # Output: Implement the drive strategy C.

    sports = SportsRoadVehicle()
    print(sports.drive())   # Output: Implement the drive strategy A.

    city = CityVehicle()
    print(city.drive())     # Output: Implement the drive strategy B.
```

### Another Simpler Example

![[strategy_design_pattern1.png]]

```python
# pylint: disable=too-few-public-methods
"The Strategy Pattern Concept"
from abc import ABC, abstractmethod

class ISortStrategy(ABC):
    "A strategy Interface"
    @abstractmethod
    def sort(self):
        "Implement the sorting strategy"

class BubbleSort(ISortStrategy):
    "A Concrete Strategy Subclass"

    def sort(self):
        print("Implement the BubbleSort strategy")

class QuickSort(ISortStrategy):
    "A Concrete Strategy Subclass"

    def sort(self):
        print("Implement the QuickSort strategy")

class SelectionSort(ISortStrategy):
    "A Concrete Strategy Subclass"

    def sort(self):
        print("Implement the SelectionSort strategy")

class Context:
    def __init__(self, strategy: ISortStrategy):
        self.strategy = strategy

    def set_strategy(self, strategy: ISortStrategy):
        self.strategy = strategy

    def sort(self):
        self.strategy.sort()


# Usage
context = Context(QuickSort())
context.sort()  # Output: Implement the QuickSort strategy

context.set_strategy(SelectionSort())
context.sort()  # Output: Implement the SelectionSort strategy

context.set_strategy(BubbleSort())
context.sort()  # Output: Implement the BubbleSort strategy
```
# References
- https://sbcode.net/python/strategy/
- [Concept and Coding](https://www.youtube.com/watch?v=u8DttUrXtEw&list=PL6W8uoQQ2c61X_9e6Net0WdYZidm7zooW&index=5)