
2025-06-24 23:31

Status:

Tags: [[notes/3 - Tags/factory design pattern|factory design pattern]] [[notes/3 - Tags/design pattern|design pattern]] 

# Factory Design Pattern

**Why do we use it ?**
- If we have a big codebase, and we need to initialize the same object at multiple places in our codebase based on some condition, then it leads to code duplicacy and slowly becomes unmanageable.
- Factory Design Pattern provides a centralized object creation, making it manageable.

![[factory_design_pattern.png]]

![[factory_design_pattern1.png]]
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def draw(self):
        pass

class Circle(Shape):
    def draw(self):
        print("Drawing a Circle")

class Square(Shape):
    def draw(self):
        print("Drawing a Square")

class Rectangle(Shape):
    def draw(self):
        print("Drawing a Rectangle")

class ShapeFactory:
    def get_shape(self, shape_type: str) -> Shape:
        if shape_type == "CIRCLE":
            return Circle()
        elif shape_type == "SQUARE":
            return Square()
        elif shape_type == "RECTANGLE":
            return Rectangle()
        else:
            raise ValueError(f"Unknown shape type: {shape_type}")
        
def main():
    factory = ShapeFactory()

    # Create a Circle
    shape1 = factory.get_shape("CIRCLE")
    shape1.draw()

    # Create a Square
    shape2 = factory.get_shape("SQUARE")
    shape2.draw()

    # Create a Rectangle
    shape3 = factory.get_shape("RECTANGLE")
    shape3.draw()

if __name__ == "__main__":
    main()
```
---
# Abstract Factory Pattern
- It is also known as Factory of Factories.


# References
- https://sbcode.net/python/factory/
- [Concept and Coding](https://www.youtube.com/watch?v=7g9S371qzwM&list=PL6W8uoQQ2c61X_9e6Net0WdYZidm7zooW&index=7)
