## IEEE Maintenance Process (IEEE 1219)
- Activity Definition -> Implementation process of the activity
- Input -> Items that required as input of the activity
- Output -> item produced by the activity
- Control -> items that provide control over the activity
- Metrics -> items that are measured during the execution of the activity

## ISO/IEC 14764 Maintenance Process

The maintenance process comprises the following high-level activities:
1. Process implementation
	- Create maintenance processes and strategies.
	- Procedures for Modification Request should be established
	 - Put the CM process into action
2. Problem and modification analysis
	- Perform a preliminary investigation
	- confirm the issue
	- create choices for executing the change
	 - Keep track of outcomes
	 - obtain clearance for the option of modification
3. Modification implementation
	- Conduct a thorough investigation
	- The modification should be developed, coded and tested
4. Maintenance review and acceptance
	- Conduct evaluations
	 - Obtain approval for the change
5. Migration
	- confirm the  migration is compliant with ISO/IEC 12207
	 - make a migration strategy
	  - user should be notify
	  - carry out processes in parallel
	- Notify the user that the transfer has begun
	- conduct a post-op evaluation
	- make sure that old data can be accessed
6. Retirement
	- develop plan for retirement
	- acknowledge user for retirement plans
	- parallel operations
	- acknowledge user start of retirement
	- old is accessible

# Maintenance Models

## Reuse-Oriented Model

- Existing components can be re-use in software maintenance
- Consist following steps:
	- Identifying components from <-- Old System that can be reused
	- Understand components
	- Modify the old system components so that they can be used in the new system
	- Integrating the modified components into the new system

This can take experience when modifying the 
Angular Controller from the Senior's Open Source Code
### Quick Fix Model

- changes are quickly made to the code then -> Documentation
- new code recompiled to produce -> new version
- embodies a commonly used approach to software maintenance
- low cost $ 
- less concern on the impact of modification

Note: Just small fix only, it good when there is no huge impact on the system, 
for example , changing a button color, changing the font size


### Iterative enhancement model

- Kaizen -> gradual and systematic enhancement of procedures

- First Changes are made to highest level documents
- Then changes propagated down to the code level
- Assume complete documentation is available
-  begins with existing system's artifacts, namely, requirements, design, code, test, and analysis document
- High Level document -> Low level document -> Code Base
- Allows maintainers to redesign the system, based on the analysis of the existing system

#### Stages of enhancement model
- Analysis of software system
- Classification of requested modification
- Implementation of requested modification

### Full Reuse Model

- Full Reuse of old system components into the new system
-  The new system is built from components of the old system and others available in the repository

#### Prerequisite
- Availability of Repository of artifacts describing the earlier versions of the present and similar systems.

#### Two Major Steps
1. Perform requirement analysis and design of the new system
2. Use the appropriate artifacts, such as requirement, design, code, and test from any earlier versions of the old system.

#### Flow
1. Identify the components of old system that can be reuse
2. Understand the components
3. Modify the old system components to support new requirement
4. Integrate the modified components to form a newly develop system


### Staged Model for Closed Source Software

#### Stages
1. Initial Development, develop the first functioning version of the software
2. Evolution, developers improve the functionalities and capabilities of the software to meet the needs and expectation 
3. Servicing, developer fix minor and emergency defects, and no major functionality is included
4. Phaseout, no more servicing is undertaken, while vendors seek to generate revenue as long as possible
5. Closedown, the software is withdrawn from the market and customers are directed to migrate to a replacement


##### Initial Development

- Software Developers built the first version of the system from the ground up
- SDLC phases / releases are not informed to the customer
- Focus on key foundations for future iteration: software architecture and team knowledge

##### Evolution

- After development is done
- satisfy the demands and expectations of clients, software engineers increase the system functionalities and capacities
- Rapid patches and new releases are sent to customers, user feedback is gathered for enhancements
- Evolves in response to customer needs for new features and competitive offerings
- Change in operational environment and business behavior may cause evolution as well


##### Servicing
- Software Architecture are keys that would affect the service stage
- Minor changes to the source code are performed, with no visible improvements to the user
- Very costly and complicated, keep the amount of modification to a minimum or utilize wrappers to make changes
- Modification undermines the system architecture even more necessitation more servicing

##### PHASEOUT

- Supplier opt not to add more additional servicing during this stage
- software become obsolete as change are no longer granted
- Users have to work around to system's recognized flaws (Since there is no modification)
- The more the CR, going back to servicing stage becomes extremely difficult

##### CLOSEDOWN

- Final shutdown, seller removes the software product from the market
- Recommend other solutions to clients









