
2025-03-23 12:04

Status:

Tags: [[system design]] [[back of the envelope]]


# System Design Capacity Estimations


Capacity Estimations are generally calculations done to fulfill the non-functional requirements.
- Availability
- Amount of data that needed to be stored
- Number of transactions that need to be supported
Do we need to necessarily do these calculations ?
	- Just check with the interviewer, if they want you can dig deep for these calculations
	- Else, you can do basic calculations that can help you choose the various technology you are planning to pick for the system.

Metric System:
	- Always do calculation in terms of millions, billions and trillions
	- Do not think in terms of lakhs and crores and thousands and then do conversion
	- 1 million = 10^6
	- 1 billion = 10^9
	- 1 trillion = 10^12

Storage Capacity
	- 1B = 8 bits
	- 1 kB = 1024 B
	- 1 mB = 1024 kB
	- 1 gB = 1024 mB
	- Instead of writing a lot of zeros in interview, instead write k, m, g
	- Also remember:
		- k * k = m
		- m * k = g
		- g * m = t
		- t * g = p


Some memorizations:
	- 1 day = 86400 sec
	- 1 million/day ~ 10-12/sec
	- 1 million/min ~ 700/min
	- 1 million/hour ~ 42k/hour


# References
[how-i-calculate-capacity-for-systems-design](https://dev.to/ievolved/how-i-calculate-capacity-for-systems-design-3477)
[# Back of the Envelope Calculation for System Design Interviews](https://www.codementor.io/@robinpalotai/back-of-the-envelope-calculation-for-system-design-interviews-z4ljbsp5l)
