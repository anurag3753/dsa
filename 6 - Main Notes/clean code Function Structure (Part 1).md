
2025-04-21 17:27

Status:

Tags: [[chapter4]] [[clean code function structure]] [[clean code]]

# Function Structure (Part 1)

## Key Principles

### Function Size

- **Small Functions**: Functions should be very small, ideally around four lines of code.
- **Indentation**: Aim for minimal levels of indentation, ideally one level. We do not want any internal braces inside our functions.
- **Naming**: Functions should be well-named and organized into well-named classes within well-named namespaces.

### Function Arguments : 
	We should treat every function argument as a liability and not an asset

- **Minimize Arguments**: Fewer arguments are better. 
	- Zero is ideal, one is okay, 
	- two is acceptable, and three is bordering on sloppy.
	- If three or more arguments are so cohesive that they can be passed together into a function, then **we should better declare them as an object.**
- **Boolean Arguments**: Avoid passing booleans as they indicate a function does two things. Instead, create separate functions for each case.
- **Output Arguments**: Avoid output arguments as they are unexpected and can confuse readers. **Use return values instead.**
	- Example, passing list in python and function is modifying the list. It is a bad practice.
- **Null Arguments**: Avoid passing `nulls`, as they act like pseudo-booleans. Create separate functions for cases where null might be used.

### Error Handling

- **Error Checks**: Avoid cluttering functions with error checks and null checks. Use exceptions for error handling.
- **Defensive Programming**: Avoid defensive programming within your system; rely on unit tests to catch errors.
	- I hate littering my code with the null checks and error checks.
	- We need to trust our tests. And we should trust our system to be not allowing the null values, to be slipped through in our functions.
	- Defensive programming leads to offensive code, and is generally a huge waste of time.
	- If you are constantly checking for null values, it means that your unit tests are not preventing you from passing those nulls. So, fix your unit tests and remove null conditions checks in your code.
		- However, when accepting data from public API's we need to do defensive programming and check for null and all other possible scenarios, because we do not know what other people are going to pass to our functions.

### Function Structure

- **Public and Private Methods**: Public methods should be at the top, followed by private methods that are called by the public ones.
	- But again, follow the convention that is followed inside that particular language.

- **Stepdown Rule:**
	- Important stuff goes at the top and the details goes at the bottom.
	- Organize functions so that higher-level functions are at the top, and lower-level functions are below, stepping down one level of abstraction at a time.
	- It should read just like the magazine article. Important things (public function) on the top and the details (private functions) at the bottom.
	- No function down below, calls a function up above.
	- **We can have this thing possible in python, as python allows for the possibility of the inner functions.**
	- If we have more than one public functions, I will first finish the top level public function (And write all the related private functions as the inner function) and then I will declare another public function.

![[Pasted image 20250421102849.png]]

### Switch Statements
	we hate switch statements. 

![[Pasted image 20250421201203.png]]

- In the above diagram, suppose we have two modules in our code. `modA` and `modB` and `A` is using some function from `B`. This means we will have statement like
```python
# module A.py
from modB import fun_b # this leads to src code dependency of modA on modB
fun_b(arg1, arg2)
```

- Because of this, dependency:
	- both the modules can not be compiled separately.
	- can not be deployed separately.
	- any change to module B will force a recompile and redeployment of module A
- Using OO we can revert the `src` code dependency and yet, leave the runtime dependency alone. (which is acceptable)

![[Pasted image 20250421214023.png]]

- We introduce a polymorphic interface. `modA` depends on the interface, and `modB` derives from this interface.
- So, this way `modB` dependency points against the runtime dependency.
	- Source code dependency opposes the flow of control/run-time dependency.
	- This allows module A and module B to be deployed separately.
	- Module B can plugin to module A. Infact, there can be many such module B that can act as plugin to module A and **A's module have no knowledge of them at all.**
	- **This is one of the feature of OO (independent deployability)**

#### Problem with switch statement:
It does not allow the independent deployability. Suppose a switch statement is dependent on many other modules. The **arrows** pointing in the direction of the **flow of control**.
Now, any change to these modules, will have an impact on the switch statement and anything dependent on the switch statement. **All these applications needs to be recompiled and redeployed.**

![[Pasted image 20250422081524.png]]

How to resolve the Switch statements ?
	We have 2 options.
		- Invert the dependencies with polymorphism.
			- Take the argument of the switch and replace it with an abstract base class that has a method that corresponds to the operation being performed by the switch.
			- Each of the cases of the switch becomes a derived class that implements that method to do what the case did.
		- Move switch statement, to a place in code, where it can't produce the problem.
![[Pasted image 20250422082836.png]]

- **Polymorphism Over Switch**: Replace switch statements with polymorphism to manage dependencies and maintain independent deployability.
- **Main Partition**: Switch statements can be safe in the main partition if dependencies point in the right direction.
	- Main partition should depend on the application, and the application should have no dependencies on the main partition. In essence, main is a plugin to the application
	- This technique is called `Dependency Injection` and there are many frameworks that can help with this.
	- The trick to dependency injection ?
		- Carefully define and maintain your partitioning.
		- Use the frameworks and to inject a few entry points from the main into the rest of the application.
	- Switch statements do no harm as long as they stay in the main partition.

![[Pasted image 20250422083102.png]]

- A system that is independently deployable, is also **independently developable.**
## Programming Paradigms:
	- Functional Paradigm
	- Structured Paradigm
	- Object Oriented Paradigm
### Functional Programming
	We want to put discipline on the side effects.
- Functional programming promotes to write programs without any assignment statements.
	- Instead of setting values, you pass those values are arguments of the functions.
	- Instead of looping, you recurse through a set of function arguments.
- Side Effects:
	- When a function changes a variable that outlives the function call. Ex: when it changes the state of an instance variable, then the function has a side effect. This is a persistent source of errors.
	- Side effects functions often comes in pairs (open/close , new/delete) and they generally follow an order (open must be called before close)
	- Temporal Coupling:
		- When functions must be called in order it is called temporal coupling.
		- How to eliminate temporal coupling ? (Yes, we can get rid of it)
	```python
	# Get all the data from the database
	def collect_db_data(conn, query):
		conn.connect()
		conn.run_query(query)
		conn.close()
	# A good example of it is `with open` block in python. It leaves the system 
	# the same state as before. No lying around of open file pointers.	
	```
_**NOTE:**_ Our goal is not to eliminate side effects. Our goal is to impose the discipline upon where and how those side effects happen.

- **Command-Query Separation**: Commands change state and return void, while queries return values and do not change state.
	- Function that returns value, should not change state. (Ex: Getters function)
	- A function that change state, should not return anything, they can throw exception (Ex: Setter functions)
```python
user = authorizer.login(userid)
# It is clear that autorizer is changing the state of the function. But it is not clear with the return object are we supposed to do ?
"""
1. Do we need to class user.logout() at some point ?
2. Would not it be better, if autorizer manages it.
3. If yes, then why did autorizer returned you back ?
"""
# Often times, if for some reason login failed we are tempted to return some kind of error code but it's better to throw exception and maintaining the convention that the command return None/void.
```
### Tell Don't Ask

- **Avoid Queries**: Tell objects what to do rather than asking them for their state and making decisions based on that.

#### Long Chain of functions
```shell
O.getX().getY().getZ().doSomething() # Violation
O.DoSomething() # This should be the preferred way

```
- 1st one was clear violations of Tell, Don't Ask. 
- 2nd one, we delegated the task, and it is that function responsibility to figure out things.

These long chains also violate something called as "Law of Demeter".This law states that it is a bad idea for single functions to know the entire navigation structure of the system.

![[Pasted image 20250421110300.png]]

### Structured Programming

- **Sequence, Selection, Iteration**: Compose algorithms using these three basic operations.
- **Single Entry/Exit**: Functions should have a single entry and exit point, allowing for easier reasoning and understanding.

![[Pasted image 20250421110449.png]]

- Try not to do `early returns` and `break` statements inside your code. We are not talking here about the simple code, but in a moderate complex code. Early return and breaks, makes code a lot harder to understand.
- If you keep your functions very small (4 lines of code) as we read in an earlier chapter, then your code will automatically be following the structured programming.
## Conclusion

- **Reader Responsibility**: Your primary responsibility is to make your code understandable for your readers.
- **Maintainability**: Follow these principles to create clean, maintainable, and understandable code.

# References
[Function Structure - Orielly]([https://learning.oreilly.com/videos/clean-code-fundamentals/9780134661742/9780134661742-code_01_04_00](https://learning.oreilly.com/videos/clean-code-fundamentals/9780134661742/9780134661742-code_01_04_00 "https://learning.oreilly.com/videos/clean-code-fundamentals/9780134661742/9780134661742-code_01_04_00")/)

