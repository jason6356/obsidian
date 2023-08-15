

## Lehman's Laws

### Implication of Lehman's Law

#### Assumptions management
- mainly focus on e-type software
- this focus on the environment 
- if environment change then the software change
- When you develop system, from your experience, do you expect you get full 
- not full specification
- we need to make assumption before making the system
- we need to record the assumption
- we need to revise back the assumption
- is it applicable? or should I remove it from document

#### Evolution Management

- focus on change control
- all changes are documented, identified and recorded,
- examine how the changes is, is this change is going to lead to proper delivery of the new software? risky?
- how to trace changes
- evolution does not mean coding, maybe architecture changes, we use other tools for it
- try to improve the plan of the change
- impact analysis (Chapter 9) -> It is not easy to change software

#### Release Management

- management of release
- is the release safe or not
- make sure release is safe to distribute
- try to make sure release is clean (try to not include with deprecated functions)

### SPE (Specified, Problem, Evolving)
- Category of software is determine by Lehman's during his reaserch on software evolutions and maintenance with these 2 factors
	- How a program interact with its environment
	- How flexible the environment and the underlying problem that the program address

#### S-Type Program

- clear and complete specification
- they already state the solution already
	- Example -> Program that use to divide 2 numbers
- the acceptance of these program is based on the specification
- is the specification is meet with the requirement

#### P-Type Program

- refer to the real world problem
- not practical
	- for example, you want to create a chess game, its a very complex logic
	- its not practical to fulfill all the complex logic inside
	- we need to make assumption
- The acceptance is based on the outcome of the program by the stakeholder

#### E-Type Program

- those common software we are using
- Environment change -> it has to change
- it does not have complete specification
- commercialized software

### COT - Commercial off the shelf

#### Benefits of COT
- Why COT is increasingly famous
	- It can be reuse
	- reduce time of development
	- high quality, being used by different company
	- well tested, follow the standardized of the way of doing (architecture as well)
	- better management of the human resource

#### Difficulties of COT
- incompatibility
	- you may not be able to access full function of the cot
- highly dependent of the supplier/support
	- "Any question call this number"
	- we depending on them, if they cannot then we hailat
- the evolution of the component we would not know
	- when its going to have next version we dun know

### CBS - Component Based System/Software

- when we are practicing Component Based Development
- Component -> Individual Working Unit
- So once the system is done, should have multiple components working together

#### Maintenance Activity

- we need to reconfigure the component
	- we need know that not all component come from outsource one, we can develop it inhouse
	- adjust the interface
	- update the interface -> coding interface
	- integration of the components
- configuration management
	- is a set of activities used to support our software development
		- example, version control is a configuration management activity
		- documentation also configuration management activity
		- why ?
			- we need to know what are the items include in the development of the software
			- Hardware, Tools, Document, Test Cases, Reports, Staff, Developer involved
			- we need to control and track
			- like we need to know what is the latest of the srs, latest changes 
- monitoring of our system performance
	- even we integrate the component, we need to monitor the performance of the system
	- we need enhance also the component based software

#### Difficulty of the Maintenance
- frozen functionality
	- if your component rely on the supplier, if the supplier gone already, you cant do anything
- incompatibility of upgrade
	- if your component upgrade, we cannot make sure it can integrated with our software
- trojan horse
	- some of the component has trojan horse that collect your data without your consent
- unreliable cots components
	- not all the supplier has reliable components
- defective middleware
	- middleware may not be fully working with all function
 

