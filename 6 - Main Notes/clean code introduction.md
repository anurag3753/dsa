
2025-03-12 21:57

Status:

Tags: [[notes/3 - Tags/clean code introduction|clean code introduction]] [[clean code terminology]] [[clean code]] [[chapter2]]


# clean code introduction


### Introduction to Clean Code

- The video is a remake of the first episode of "Clean Code" by Uncle Bob, aiming to improve the quality of scripting, video, and audio editing.
- The importance of first impressions is emphasized, leading to the decision to refactor the initial episode.

### Course Overview

- The text outlines the topics covered in the "Clean Code" course, including choosing good names, function structure, test-driven development, architecture, SOLID principles, and component principles.

### Importance of Good Code

- The text references Kent Beck's book "Implementation Patterns," which emphasizes the importance of good code. Uncle Bob stresses that clean code is crucial for the success of a company, sharing a personal story to illustrate this point.

### Story of a Company Killed by Code

- In 1988, a company developed a network management system in C and used a debugger from Sword Inc.
- Sword's debugger was initially successful, but the company failed to deliver a reliable C++ version, leading to its downfall.
- The story highlights the consequences of rushing to market without maintaining code quality.

### The Consequences of Rushed Development

- The narrative continues with a story about a company that rushed its initial product to market, resulting in a tangled and unmanageable codebase.
- The inability to transition from C to C++ due to the messy code led to the company's downfall, highlighting the importance of maintaining clean code from the start.

### The Impact of Bad Code on Productivity

- Initially, projects may start quickly, but as the codebase becomes messy, productivity slows down significantly. Managers, who base their plans on initial productivity, face challenges when the development pace decreases, leading to broken promises and financial losses.

### Misguided Solutions to Productivity Issues

- Common managerial responses, such as tightening deadlines, mandating overtime, or hiring more staff, often exacerbate the problem rather than solve it.
- Brooks' Law is introduced, stating that adding manpower to a late project makes it later, as new staff need time to learn and adapt to the existing codebase.

### The Temptation of a Complete Redesign

- Developers may suggest starting over with a complete redesign, but this approach is risky and often fails for large projects.
- The story illustrates how a "big redesign in the sky" can lead to further delays and dissatisfaction among both customers and developers.
- The tiger team is spending their time pouring over the old code, to understand what the system does. Then we want to spend time in making the code better by some definition of better.
- Initially productivity increases, but later it decreases over time. Because the code is slowly becoming mess. And it starts taking more and more time to fix the mess.

### The Nature of Software Rot

- Over time, software systems tend to degrade and become difficult to maintain, a phenomenon referred to as "software rot."
- The text introduces the concept of "rigidity," where a system resists change and requires modifications in multiple places to fix a single issue, leading to unpredictability and blown estimates. 
	- A system is rigid when that system requires us to make many changes at many different places in order to add a single new behavior or to fix a single bug
- Rigid system makes any change hard for the developer, and they will be hesitated in giving the estimations to manager for the change.

- ### The Challenges of Rigid Systems

- Rigid systems are described as unpredictable and difficult to estimate, leading to frustration and blown estimates. The text humorously illustrates the challenges of dealing with such systems.

### The Importance of Addressing Code Quality

- The only effective way to deal with a messy codebase is to confront and clean it, rather than running away from the problem.
- The text emphasizes the need for continuous attention to code quality to prevent the accumulation of technical debt and maintain productivity.

### Fragility in Systems

- A system is considered fragile when fixing a single bug or adding a new feature causes malfunctions in unrelated parts of the system.
- An example is given where a simple spelling correction in a menu led to widespread system crashes because customer systems were parsing those menus.

### Inseparability in Systems

- Inseparable systems are those where components cannot be easily reused in other systems due to tight coupling.
- An analogy is used where a car with a welded trailer cannot be separated without significant effort, similar to code that cannot be reused without extensive modification.

### Opacity in Systems

- Opacity refers to code that is so poorly structured that it is difficult to understand the author's original intent.
- Opaque code is compared to a pigsty in a rainstorm, emphasizing its unreadability and complexity. Opaque code is hard to read, hard to understand and hard to change.

### The Impact of Bad Code

- Bad code significantly impedes productivity, and developers often blame external factors like managers or deadlines.
- The text argues that developers are responsible for the code they write, and rushing leads to messy code.

### The Illusion of Speed

- Rushing to meet deadlines creates a mess, which ultimately slows down development.
- The idea of going back to clean up code later is a myth, as urgency and deadlines never truly diminish.

### The Importance of Clean Code

- Clean code is essential for maintaining speed and productivity in both the short and long term.- The text emphasizes that the only way to go fast is to write clean, well-structured code from the start.

### The Importance of Clean Workspaces (Sushi Chef Analogy)

- The analogy of a sushi chef is used to illustrate the importance of maintaining a clean workspace. The chef's ability to work quickly and efficiently is attributed to the cleanliness and organization of their workspace.

### Defining Clean Code

- Several experts provide their definitions of clean code:
    - **Bjarne Stroustrup**: Clean code should be elegant and efficient, doing one thing well.
	    - Elegant code: Is the code that does a lot of things in few words.
	    - Efficient Code: is code that uses very less CPU cycles
    - **Grady Booch**: Clean code is simple, direct, and reads like well-written prose. 
    - **Michael Feathers**: Clean code looks like it was written by someone who cares.
    - **Ward Cunningham**: Clean code is predictable, with routines that meet expectations.

### The Boy Scout Rule

- The idea of leaving code better than you found it is introduced, inspired by Robert Baden Powell's exhortation to leave the world better than you found it. This encourages developers to make small improvements to the codebase continuously.

### Lessons Learned

- The narrative underscores the importance of maintaining clean and well-structured code.
- It warns against the pitfalls of prioritizing speed over quality, as this can lead to unsustainable codebases and ultimately harm a company's success.

Overall, the text underscores the critical importance of clean code and the dangers of neglecting code quality. It highlights the challenges of managing a messy codebase and the potential consequences for both developers and businesses.

# References
