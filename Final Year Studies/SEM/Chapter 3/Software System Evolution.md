
## Definition

the applications of software maintenance activities and processes that generate a
new operational software version with a changed customer-experienced
functionality or properties from a prior operational version, where the time period
between versions may last from less than a minute to decades, together with the
associated quality assurance activities and processes, and with the management of
the activities and processes.


- Key properties of software evolution as **preferred by the stakeholders**
- Changes are made in
- Adjustments should not jeopardize software's reliability 
- The system maintainability should not deteriorate, future adjustments will be more costly if this is not done

### Describe the Software System Evolution

#### Evolution
- Explain the causes, processes, and impacts of software evolution. The nature of the evolution phenomena is examined
#### Process Improvement
- Design, maintenance, refactoring, and reengineering are all approaches to manage
the consequences of software evolution by developing better methodologies and
tools.
- From an engineering standpoint, evolution is studied. i.e. emphasises the
more practical components that aid developers in their daily tasks. As a result, the
foundation of the process improvement approach is methodologies, tools, and
activities that provide the capability to direct, implement, and control software
evolution.



## Lehman's Law
- Assumptions Management
- Evolution Management 
- Release Management

### Assumptions Management
- Identify and write down any assumptions 
- Challenge -> Identify all of the assumptions completely
- Changes in (spec, design, implementation, operational domain) -> revalidate the assumption
- Create and use tools to keep track of all the aforementioned tasks.

### Evolution Management (TL:DR)
- Assess and pursue anti-regressive tasks such as complexity control, reorganization and complete documentation on a regular basis.
- Ascertain that assumptions are identified and recorded in the documentation
- Assess the patterns in the evolution of the software product's functional and nonfunctional requirements in advance

### Release Management
- Release is risk-free
- If release isnt safe, spread the fix changes to numerous release to ensure each one is safe
- if large functional increments are unavoidable, schedule follow-up clean-up releases with a focus on bug fixes and documentation updates
- Minimize the propagation of changes
- Put priority on anti-regressive activities, such as restructuring
- Switching enhancement and extension releases and cleanup and restructure releases

## SPE Taxonomy

### S-Type Program
- NFR and FR that are essential to its stakeholder
- solution's acceptability to its stakeholders is that it is
correct in terms of its formal specification.
- S-type programs are used to address issues that are completely described in a
closed and abstract manner.

![[Pasted image 20230822150758.png]]

### P-Type Program (TLDR)

![[Pasted image 20230822150825.png]]
### E-Type Program
- Automate a human or societal action, simplify assumptions, and interact with the
outside world by requesting or giving services.

#### Example
Operating Systems, business administration software, inventory management,
stock trading etc.


### COT - Commercial off the shelf

- Component-based development
- pre-existing building blocks and connect them
- Purchase components

#### Issue with COT
- Limited adaptation, its hard for system integrators to modify COTS components to fit user needs
- Hidden details, integrators don't know all the details about how these components work, how they change over time
- Dependence on suppliers, integrators rely heavily on the people who create and provide these components


### CBS Maintenance
- source code implementing the wrapper, glue, and tailoring modules
are used to integrate the system, instead of delivering services and functions.
- largely loses control over the precise evolution of
the system, because COTS developers focus on their own business interests.

#### Issue with CBS Maintenance
- Frozen functionality
- Incompatibility of upgrades
- Trojan horses
- Unreliable COTS components
- Defective middleware.

#### Activities

##### Component Reconfiguration
- Add, remove, replacing components of a system

##### Testing and debugging
- fix defects

##### Monitoring of systems
- Monitor the system to be able to better understand the system performance.
- Continuous monitoring enables the maintenance personnel to enhance the
performance of the system, measure usage of resources, keep track of the
anomalies in the system behavior, and perform root cause analysis of system
failures.

##### Enhancing Functionality for Users
- enhancing the functionality of the new system for the users
- Using Tailoring technique

##### Nutshell

- Write additional glue code
- use vendor supplied tailoring technique to customize product

##### Configuration Management Activities

- Track version, detail for each omponents,
- Name of developer
- Contact information
- archieve the source code
- Archive the working versions of all tools, namely, compilers and linkers,
necessary to rebuild a component.
- configuration history
- compatible versions
- support and licenses
- detailed rationale
- contact information
