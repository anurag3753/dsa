
2025-03-17 13:28

Status:

Tags: [[clean code terminology]] [[clean code]] [[chapter2]]


# clean code names++

#### Importance of Naming

- Naming is a critical aspect of software development, as it is pervasive across directories, files, classes, methods, variables, and namespaces.
- Good naming reveals the intent of the code, making it easier to understand and maintain.

#### Key Principles

- **Reveal Intent**:    
    - Names should clearly convey the purpose of the entity they represent.
    - If a comment is needed to explain a name, the name is not sufficiently descriptive.

- **Self-Descriptive Variables**:
	 - Variables should act as their own comments, making the code self-explanatory.
	 - Use explanatory variables to clarify complex logic.
	
- **Avoid Implementation Details**:    
    - Names should not describe implementation details, but rather the problem being solved.
    - Use known conventions and mathematical concepts where applicable (e.g., intervals for ranges).
    
- **Avoid Disinformation**:    
    - Names should not mislead or provide incorrect information.
    - Avoid concrete names for abstract concepts and ensure names match their functionality.
    - **It is one of the worst things that the programmer can commit**. It consumes a lot of developer time to make the new change.

- **Pronounceable Names**:    
    - Choose names that are easy to pronounce to facilitate communication among developers.
    - Avoid cryptic abbreviations and ensure names are clear and understandable.
    - Ex. `qty` is short for quantity. Use `quantity` instead of `qty`
    
- **Avoid Encodings**:    
    - Avoid using prefixes or encodings that denote types (e.g., Hungarian Notation).
    - Modern IDEs and compilers provide type information, making such encodings unnecessary.
    
- **Nouns and Verbs**:    
    - Classes and variables should be named using nouns or noun phrases.
    - Methods should be named using verbs, reflecting the action they perform.

- #### Additional Considerations
	- **Maintenance Overhead**: The true cost of software is in its maintenance, so clarity in naming is crucial.
	- **Adaptability**: Be willing to change names if their meanings evolve over time.
	- **Avoid Noise Words**: Eliminate unnecessary words that do not add value to the name. Avoid using generic terms like "Manager," "Processor," "Data," or "Info" as they do not convey specific meaning and often indicate uncertainty about the entity's purpose.

- **Nouns and Predicates**:
	- Variables, especially those holding class instances, should be nouns or noun phrases.
	- Boolean variables should be named as predicates (e.g., `isEmpty`, `isTerminated`) to read well in conditional statements.
	
- **Methods as Verbs**:    
    - Methods should be named using verbs or verb phrases (e.g., `PostPayment`, `GetPrice`).
    - Methods returning Booleans should be named as predicates (e.g., `IsPostable`).
    - Properties, which are methods pretending to be variables, should also be Nouns. If they are boolean, then they should be predicates.
    
- **Avoid Nouns for Accessors**: Use verbs like "get" for accessor methods (e.g., `GetFirstName`, `GetFuelRate`).
    
- **Enums as Adjectives**: Enums often describe states or object descriptors and should be named accordingly.
	```python
	from enum import Enum
	class Color(Enum):
		RED = 1
		GREEN = 2
		BLUE = 3
	class Size(Enum):
		SMALL = 1
		MEDIUM = 2
		LARGE = 3
	class Status(Enum):
		PENDING = 1
		CLOSED = 2
		CANCELLED = 3
	```
    
- **Readable Code**: Code should read like well-written prose, with statements forming clear sentences.
    
- **Scope and Name Length**:    
    - Variable names should be proportional to their scope length: longer names for longer scopes, shorter names for shorter scopes.
    - Functions and classes follow the opposite rule: shorter names for longer scopes, longer names for shorter scopes.
    - Private classes should have long and descriptive names. It acts as a self comment.
    - Derived classes (Inheritance classes), tend to have longer names because adjectives gets added to them, generally.
    - Variables that have short scopes, can abbreviate to just 1 letter as well.
	    ```python
	    class Account:
		    pass
		class SavingsAccount(Account): # Derived class
			pass
	    ```
    
- **Avoid Abbreviations**: Use clear and pronounceable names to facilitate communication among developers.
    
- **Avoid Encodings**: Avoid using type encodings like Hungarian Notation, as modern IDEs and compilers provide necessary type information.
    
- **Grady Booch's Principle**: Clean code should read like well-written prose, using appropriate parts of speech for classes, variables, and methods.
    
- **Martin Fowler's Reprimand**: Emphasizes writing code that is understandable by humans, not just computers.
    
#### Conclusion
	1. Choose your names thoughtfully
	2. Communicate your intent.
		1. If you need to write comment to write your intent, then it is a bad name
	3. Avoid Disinformation
		1. Remember that a name says what it means and means what it says
	4. Remember to create names that people can pronounce
	5. Avoid Encodings
	6. Choose Parse of Speech well. It should read like a sentence.
	7. The Scope Rule.
			Variables: 
				Shorter scope -> Shorter names
				Global scope -> Longer names
			Funtions/Classes:
				Opposite rule to the Variables
	8. Any fool could write code that computer can understand. But a good programmer writes code that a human can understand.

- Describe the Problem: `include_second`,`include_third`.
	- Variable name should not try to describe the logic

# References
