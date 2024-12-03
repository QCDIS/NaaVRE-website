# Readiness level framework for virtual labs in NaaVRE

This draft version contains some revision questions, which are marked in <span style="color:green">green</span>.

Version 1.0.0

NaaVRE facilitates data processing, data analysis, and simulation by enabling scientists to create their own virtual labs.
A collaborative effort between ecosystem specialists, computational scientists, data scientists, and development and operations engineers 
ensures that virtual labs are optimized to support research effectively.
Virtual labs evolve through distinct stages: Initially, development is the primary focus. As the lab matures, 
it transitions to support a first user, and ultimately, multiple users can conduct experiments within the environment.  

This readiness level framework assists researchers in building virtual labs by:
- Defining the content of virtual labs. 
- Describing the roles involved in the development and use of a virtual lab.
- Describing the progression of a virtual lab through readiness levels, highlighting requirements, milestones and responsibilities.

## Content of a virtual lab
A virtual lab can contain four types of assets <span style="color:green">(Should we choose between the terms: resource & asset? Nanohub uses “resource”. Maybe we should discuss this with domain scientists)</span>:
- The codebase: Any code written for the virtual lab.
- Libraries: Code used by the codebase, but not written for the virtual lab.
- Data: Stored data that is produced by data processing, data analysis, and simulations in NaaVRE.
- Containerized cells and workflows.    

Besides assets, we encourage the creators of a virtual lab to support the usability of the assets, by providing documents:
- Metadata.
- Documentation, including a tutorial.
- Software management plan <span style="color:green">(Do we need a virtual lab to specify who is planning to upkeep the virtual lab? Shall we focus on getting a readiness level framework which mentions a software management plan, and work out the details of what should be in the software management plan later? I think a software management plan belongs to a readiness level which no lab will currently reach.)</span>

## Virtual lab roles
NaaVRE aims to be a virtual research environment (VRE) that enables experts in computational ecology and ecological data analysis
to create virtual labs in which users conduct their research.
Our platform needs contributions from the following roles to enable innovative research methods:
- Virtual lab core developers: Create a new virtual lab in NaaVRE. 
- Virtual lab code reviewer: Provides feedback during core development on the user-friendliness, maintainability, and robustness of the
source code and other assets.
- Virtual lab developer: Once a virtual lab has reached a stage in which it can be used by others, users can expand and adapt the source code to suit their needs.
- Virtual lab user: Researchers couple virtual labs assets, use their own datasets, and set their own parameters to run their own experiments in the virtual lab.
  - Golden user: First user of the virtual lab.
- Virtual lab visitor: Visits the virtual lab to see how experiments were done.
- Virtual lab owner / Principal investigator: Coordinates the further development of the VL with a scientific vision. Will initially be the golden user
who initiates the construction of a new virtual lab to do experiments and create a first publication based. This will often be done by the team involved in the core development.
- Virtual lab technical coordinator: Knows the lab from a technical perspective. Pushes the lab to the next readiness level. Works at VLIC.
- Virtual lab service operations: Can support users. Knows the lab and can help out when problems arise. <span style="color:green">Do we want a specific trainer role?</span>  
- Virtual research environment (VRE) development and operations (DevOps) engineer: Creating and maintaining NaaVRE the software in which virtual labs can be created. This is done by LifeWatch.
- Networked infrastructures scientist: Contribute state-of-the-art components to the NaaVRE and can publish technical papers 
that demonstrate the relevance of NaaVRE in the field of networked systems.

A person can fulfill multiple roles. In the virtual labs the distinction between development and use is a continuum. How many changes a scientist 
will make to the codebase and libraries depends on whether the virtual lab already has the necessary assets for the user.

## Readiness levels
We discern four readiness levels in the development of a virtual lab. A new virtual lab starts at level 1.
For each higher readiness level improvements should be made to the assets and documents in order to make the lab usable by others with an increasing amount of independence from the virtual lab core developers and VRE DevOps team.

1. Core Development: Core development of the virtual lab is taking place in co-development with the Lifewatch VRE development and operations team.
2. First use: The first person not involved in the core development of the virtual lab can start using the virtual lab.
This user will receive support from the Lifewatch (VRE) development and operations team. This is the stage in which the lab is
considered ready enough to support a golden use case. Quality assurance can indicate that the lab is ready for its first use.
3. Workshop use: The lab can be used by multiple workshop participants under the guidance of an instructor that can point out what the user can safely change and can not change in the lab. 
4. Operational service: All scientists are welcome to create their own instance of the lab for their research. No more support is needed to work in the lab. Any problems arising should be treated as bugs.

Whenever users of the virtual lab come up with a new idea that does not fit in the possibilities of the virtual lab they are using, 
they can contact LifeWatch to discuss the possibilities of creating a new virtual lab.

![ NaaVRE_development_cycle.png not found](NaaVRE_development_cycle.png)  
The virtual lab moves through the readiness levels, from core development to operational service. Users coming up with ideas for new experiments that do not fit in the virtual lab, 
can, in collaboration with LifeWatch, create a new virtual lab that fits their needs.  

The following table shows expectations of the timeliness, and number of teams and users involved per readiness level.

| Readiness level     | Duration   | Developers | Users    | Context dissemination | 
|---------------------|------------|------------|----------|-----------------------|
| Core development    | 3-6 months | 1 team     | 0        | Metadata publication  | 
| First use           | 3 months   | 1 team     | 1        | Paper publication     |
| Workshop use        | 3 months   | 10-25      | 10-25    |                       |
| Operational service | 3 months   | infinite   | infinite |                       |

### If the golden user is a core developer
In the case where the golden user is also a core developer, there will be less priority given to the usability of the virtual lab for others
as the primary concern of the core developers will be to create a virtual lab that meets their needs to do their research.
In this case having code reviews and quality assurance is still recommended to increase the maintainability of the code for
future use, regardless of whether the lab will be used by the same researchers, other researchers from the same research group,
or researchers from other institutions.

### Setting up a new lab
A new NaaVRE virtual lab can start with the creation of a new data processing, data analysis or simulation tool or with the migration of a legacy tool. 
In both cases we recommend to start off by doing the following:
- Store the codebase on a repository with version control (e.g. git).
  - Make sure personal tokens for APIs do not end up in version control. ToDo Vlic: Guideline for secret management https://github.com/QCDIS/projects_overview/issues/276
- Choose a license for the virtual lab. We recommend using the [Apache license 2.0](https://choosealicense.com/licenses/apache-2.0/) if this is compatible with the other packages and software you use in the virtual lab. If the Apache License 2.0 does not suit your need, you can pick your own license, see https://choosealicense.com/ .
- Add a version number to the virtual lab. 
- Publish virtual lab metadata outside the virtual lab. Tip: Create the metadata in the external catalogue to avoid duplicate effort. <span style="color:green">ToDo: Check if we have a single preferred metadata catalogue</span>.
  - Track the metadata with version control, such that the changes to metadata can be viewed by virtual lab users.
  - ToDo VLIC: Choose a metadata standard. 
 
### During core development
Where possible, do the following while building the virtual lab:
- Pin versions of used software and libraries in the dependencies to prevent compatibility problems when updates occur to the packages and software.                                                                                                                                                                                              
- Start each cell in the notebook with a title.
- Parallelize the execution of the parts of the code where this is useful. A tutorial is available [here](https://github.com/QCDIS/lifewatch-notebooks/blob/main/NaaVRE-tutorials/splitting-classic.ipynb).
- Create documentation for the virtual lab.
  - Track the documentation with version control.

The following roles are involved during this phase:
- Virtual lab owner / Principal investigator: Provides the use case that will be the first application of the virtual lab.
- Virtual lab core developer: One or multiple core developers create a new virtual lab in NaaVRE. The virtual lab owner can be one of the core developers.
- Virtual lab code reviewer: Provides feedback on the user-friendliness, maintainability, and robustness of the
source code and other assets. We recommend starting with reviews as early on in the development process, as this may contribute to a clear architecture, and good code quality.
- Virtual research environment (VRE) development and operations engineer: Supports the creation of the new virtual lab by giving the core development team advice and changing the virtual research environment where necessary. 

#### Core development milestone
The milestone to reach during core development is a demonstration of running the workflow of the virtual lab.

### From core development to first use
A usability study should be done to determine if the lab is ready for its first use. The usability study should look at least at the following criteria:
- Security
  - Personal tokens are not tracked by version control.
- Licensing
  - The virtual lab has a license.
- Versioning
  - The virtual lab has a version number.
  - Versions of used software and libraries are pinned. 
- Metadata
  - The metadata of the virtual lab is published.
- Codebase
  - The code executes without errors: The code can be executed without errors: Currently, you can verify this by manually executing all cells in the notebook on a machine on which the code was not developed (to ensure no references are made to local resources).
  - The responsibility of each cell in the notebook is clear and can be described in a single sentence.
- Parallel processing is applied where suitable.
- Containerization
  - The notebook cells can be containerized.
- Workflow execution
  - The containerized cells can run without any modifications.

### During first use
The following should be done during 
- Data
  - Make data fair.
- Scenarios
  - Make sure and describe how the virtual lab can be used on multiple scenarios.
- Versioning
  - Give each containerized cell a persistent identifier and version number <span style="color:green">(This is currently not a feature in NaaVRE. But might become possible in the future. Added to [potential ToDos](#potential-todos-for-lifewatch-vlic))</span>
- Documentation
  - Create a [user manual](#User-manual) for the virtual lab.
- Metadata
  - Fill in all metadata fields
- Codebase
  - Add unit tests to verify the behavior of used methods and libraries.

#### First use Milestones
During first use, two papers should be published:
1. A paper in the ecosystem domain.
2. A technical paper.

#### First use responsibilities
The following roles have a responsibility in this phase:
- Virtual lab core developer: Provides support to the virtual lab owner.
- Virtual lab owner / Principal investigator: Uses the virtual lab to do their research. Publishes a paper in the ecosystem domain.
- Networked infrastructures scientist: Publishes a technical paper.
- Virtual lab service operator: When the virtual lab owner, and reviewers believe the virtual lab to be ready to be used by others,
the virtual lab service operator can try out the virtual lab with a fresh pair of eyes and do suggestions. The can help the virtual lab owner identify issues arising when others start using the virtual lab.
- Virtual research environment (VRE) development and operations engineer: Support the core developers and golden user by providing advise and changing the virtual research environment where necessary.

### From first use to workshop use
The virtual lab is ready for workshop use, if it meets the criteria for first use, and additionally the following:
- Metadata
  - All the fields of the metadata standard are present. 
- Scenarios
  - The virtual lab can be used in multiple scenarios.
- Documentation
  - At least one domain scientist who was not involved in the development of the virtual lab has reviewed the user manual. The coding experience of the reviewer of the user manual is similar to the coding experience of the intended user.
  - How to use the virtual lab on a different scenario is explained.
- Codebase
  - Unit tests verify the behavior of used methods and libraries. There should be a testing guideline, which will be done in this issue [\#274](https://github.com/QCDIS/projects_overview/issues/274).
  - The virtual lab reads, writes and exchanges data in a way that meets domain-relevant community standards. [5] <span style="color:green">I think we will need to consult some ecologists to determine these standards. I aditionally emailed Nafiseh. </span>                                                                                                                                                                                                                                                                                                         
  - The code within cells is easily human-readable and others can easily modify it. If methods have side effects, this is clear to the user.
  - The input and output of each cell is clear. It is both clear what the structure is (e.g. what data type is used) and what the data content is from a domain perspective.
- Workflow
  - The duration of computation, memory usage, and power usage of the container is acceptable. As there is currently no dashboard to monitor resource usage, contact the VLIC team for guidelines.

### During workshop use
The following should be done during workshop use:
- Documentation
  - Gather user feedback on the documentation.
- Codebase
  - Find out if the architecture of the virtual lab is understandable and maintainable.

#### Workshop use milestone
In this phase at least one workshop should be given to a group of 10 to 25 potential users.

#### Workshop use responsibilities
The following responsibilities apply during this phase:
- Virtual lab owner / Principal investigator: Gathers user feedback and determines how to facilitate other users in the virtual lab.
- Virtual lab Service operations: Gives trainings to users. <span style="color:green">Do we want a specific trainer role?</span>
- Virtual lab Technical coordinator: Answers any technical questions arising from the workshop use which the service operator can not answer. Has been involved as VRE DevOps engineer during the previous stages.

### From workshop use to operational service
The virtual lab is an operational service if all previous criteria apply and additionally the following criteria apply:
- Dependencies are specified. The dependencies are in the dockerfile, but should be duplicated in the metadata such that a person can in theory also run the source code on their own machine after installing the dependencies manually.
- <span style="color:green">Deployed on MyLifeWatch</span>

### During operational service
The following should be done during operational service:
- Make the containerized cells and workflow interoperable with other systems when use cases for the interoperability between NaaVRE and another system arises.

#### Operational service responsibilities
The following responsibilities apply during this phase:
- Virtual lab owner / Principal investigator: Coordinates the further development of the virtual lab with a scientific vision. 
- Virtual lab Technical coordinator: Ensures the VRE keeps supporting the virtual lab.
- Virtual lab Service operations: Is the primary point of contact in case any problems arise with the virtual lab. <span style="color:green">Do we want a specific trainer role?</span>

### User manual
The following guidelines can be used to determine the completeness of a user manual.
- The virtual lab is explained from the following viewpoints:
  - A conceptual viewpoint. There is an intuitive description of what happens.
  - A mathematical viewpoint. How the real world system relates to the used mathematical algorithm is clear.
- The parameters are clear.
    - It is clear what the ecological meaning of the parameter is.  
    - It is clear how to change these parameters.
- There is a tutorial: Virtual lab developers are strongly encouraged to create a tutorial for virtual labs early on in the development. In the simplest case, this is the existing main notebook with a description of the processes that occur during execution.  
  - The tutorial can be done without supervision.
- Known potential pitfalls in using the virtual lab are described.
- There is a description of the standards used for data exchange with application programming interfaces and databases.
- Storage location: The description of the virtual lab from a conceptual and mathematical viewpoint is stored on [NaaVRE.net](https://naavre.net/). 
- Architecture
  - A description of the architecture of the virtual lab. In the simplest form this can be the flowchart created when composing a workflow.

## Sources
- These recommendations are partially based on ideas presented in the paper [Introducing the FAIR Principles for research software](https://www.nature.com/articles/s41597-022-01710-x), the [Fair software checklist](https://fairsoftwarechecklist.net/v0.2/), and [fair-software.eu](https://fair-software.eu/recommendations/license).

## Potential ToDos for LifeWatch VLIC
- Make NaaVRE generate a persistent identifier and version number for containerized cells. See [Containerized cells and Workflow](#containerized-cells-and-workflow).
- Software management plan: Shall we focus on getting a readiness level framework which mentions a software management plan, and work out the details of what should be in the [software management plan](https://zenodo.org/records/7248877) later?
- Choose a metadata standard for Virtual labs.  https://github.com/QCDIS/projects_overview/issues/275
- Create recommendations for testing: https://github.com/QCDIS/projects_overview/issues/274
- Guideline for secret management https://github.com/QCDIS/projects_overview/issues/276

## Feedback
Any feedback on this document is appreciated. Please contact the LifeWatch VLIC team if you have any questions or comments on the document.