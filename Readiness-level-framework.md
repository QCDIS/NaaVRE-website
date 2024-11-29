# Readiness level framework for virtual labs in NaaVRE

This draft version contains some parts with a high level of doubt, which are marked in <span style="color:green">green</span>.

Version 1.0.0   
Published <span style="color:green">current date</span>

<span style="color:green">This is a boring paragraph. Make it more lively.</span>  
The aim of this readiness level framework is to guide virtual lab developers by giving recommendations of what to include in their virtual lab and what to prioritize. 
The document first describes the content of virtual labs in [NaaVRE](https://naavre.net/) and contributions that can be made 
to create a common viewpoint of the software and the users.
Next it describes five readiness levels in which the virtual lab can be. It then proceeds with checklists that guide
virtual lab creators to get their virtual lab to the next readiness level.

### Content of a virtual lab
A virtual lab can contain four types of assets <span style="color:green">(Should we choose between the terms: resource & asset? Nanohub uses “resource”. Maybe we should discuss this with domain scientists)</span>:
- The codebase: Any code written for the virtual lab.
- Libraries: Used by the codebase, but not written for the virtual lab.
- Data: <span style="color:green">What do we consider to be the role of datasets in the NaaVRE virtual lab? Data will be produced by processing, analysis, and simulations, but do we want to store these internally? </span>
- Containerized cells and workflow.    

Besides assets, we encourage the creators of a virtual lab to support the usability of the assets, by creating the following documents:
- Metadata.
- Documentation, including a tutorial.
- Software management plan <span style="color:green">(Do we need a virtual lab to specify who is planning to upkeep the virtual lab? Shall we focus on getting a readiness level framework which mentions a software management plan, and work out the details of what should be in the software management plan later? I think a software management plan belongs to a readiness level which no lab will currently reach.)</span>

Currently, NaavRE is mostly used for scientific Workflows e.g. data processing, data analysis, and simulation. <span style="color:green">Integrate this sentence in the story.</span>  

### Virtual lab roles
NaaVRE aims to be a virtual research environment (VRE) that enables experts in computational ecology and ecological data analysis
to create virtual labs in which users conduct their research.
Our platform needs contributions from multiple roles to enable innovative research methods:
- Virtual research environment (VRE) development and operations engineer: Creating and maintaining NaaVRE the software in which virtual labs can be created. This is done by LifeWatch.
- Virtual lab core developer: Creates a new virtual lab in NaaVRE. Virtual lab core development is done in a co-development process with the DevOps engineers at LifeWatch. 
- Virtual lab code reviewer: Provides feedback during core development on the user-friendliness, maintainability, and robustness of the
source code and other assets. We recommend starting with reviews as early on in the development process, as this may contribute to a clear architecture, and good code quality.
- Virtual lab quality assurance engineer: If core developers and reviewers believe the virtual lab to be ready to be used by others,
people who were not involved in the development of the virtual lab, can try out the virtual lab with a fresh pair of eyes and do suggestions.
Quality assurance can help the core development team identify issues arising when others start using the virtual lab.
Therefore, it is good to do quality assurance before others who are not in the same institute as the core developers start using the virtual lab.
- Virtual lab developer: Once a virtual lab has reached a stage in which it can be used by others, users can expand and adapt the source code to suit their needs.
- Virtual lab user: Researchers couple virtual labs assets, use their own datasets, and set their own parameters to run their own experiments in the virtual lab.
  - Golden user: 
- Virtual lab visitor: Visits the virtual lab to see how experiments were done.
- Virtual lab owner / Principal investigator: Coordinates the further development of the VL with a scientific vision. Will initially be the golden user
who initiates the construction of a new virtual lab to do experiments and create a first publication based. This will often be done by the team involved in the core development.
- Virtual lab Technical coordinator: Knows the lab from a technical perspective. Pushes the lab to the next readiness level. Works at VLIC.
- Virtual lab Service operations: Can support users. Knows the lab and can help out when problems arise.

A person can fulfill multiple roles. In the virtual labs the distinction between development and use is a continuum. How many changes a scientist 
will make to the codebase and libraries depends on whether the virtual lab already has the necessary assets for the user.

#### Wetlab analogy
If we compare the development of a virtual research environment to the construction of a wetlab, 
the virtual research environment development and operations is the same phase as the construction of a building and rooms that house the wetlabs. 
The core development of a virtual lab would be the same phase as the installation and calibration of the wetlab equipment. 
In order to get the power supply, water supply, ventilation, and drainage pipes in the right locations in the lab,
the equipment installers and construction workers need to coordinate their efforts, like co-development is done for the virtual lab.
Once a lab is finished, the doors of the lab open for researchers to use the equipment in the lab to do their research. 
They can also create custom settings on the lab equipment to suit their needs, likewise a NaaVRE user could do development to change the source code to suit their own research.

### Responsibilities
#### VRE development and operations engineer
- Implement developments from cloud researches and thesis students into NaaVRE.

### Readiness levels
We discern five readiness levels in the development of a virtual lab. A new virtual lab starts at level 1.
For each higher readiness level improvements should be made to the assets and documents in order to make the lab usable by others with an increasing amount of independence from the virtual lab core developers and VRE DevOps team.

1. Core Development: Core development of the virtual lab is taking place in co-development with the Lifewatch team.
2. First use: The first person not involved in the core development of the virtual lab can start using the virtual lab.
This user will receive support from the Lifewatch (VRE) development and operations team. This is the stage in which the lab is
considered ready enough to support a golden use case. Quality assurance can indicate that the lab is ready for its first use.
3. Workshop: The lab can be used by multiple workshop participants under the guidance of an instructor that can point out what the user can safely change and can not change in the lab. 
4. Operational service: Any ecologist can use their own instance of the lab for their research. No more support is needed to work in the lab. Any problems arising should be treated as bugs.

#### What if the golden user is a core developer?
In the case where the golden user is also a core developer, there will be less priority given to the usability of the virtual lab for others
as the primary concern of the core developers will be to create a virtual lab that meets their needs to do their research.
In this case having code reviews and quality assurance is still recommended to increase the maintainability of the code for
future use, regardless of whether the lab will be used by the same researchers, other researchers from the same research group,
or researchers from other institutions.

#### Setting up a new lab
The following should be done from the start of the creation of a new virtual lab:
- Store the codebase on a repository with version control (e.g. git).
- Choose a license for the virtual lab. We recommend using the [Apache license 2.0](https://choosealicense.com/licenses/apache-2.0/) if this is compatible with the other packages and software you use in the virtual lab. If the Apache License 2.0 does not suit your need, you can pick your own license, see https://choosealicense.com/ .
- Add a version number to the virtual lab.                                                                                                                                                                                                                                                                                                   |

#### During core development
Keep the following in mind while building the virtual lab:
- Code quality standards to follow while developing a virtual lab in NaaVRE:
  - In the dependencies versions of used software and libraries are pinned to prevent compatibility problems when updates occur to the packages and software.                                                                                                                                                                                              
  - Notebook cells have titles: Each cell in the notebooks starts with a title.

#### From core development to first use


#### Readiness level checklist
For the content of the virtual lab, the following checklist provides a guideline of what to keep in mind during the development 
and what requirements the virtual lab should meet at different levels of readiness. For each stage the requirements from 
the stages with lower numbers apply as well. The criterion should be implemented before proceeding with the actions associated with the readiness level associated with the criterion. 
Ideally both the team doing core development and the team doing quality assurance agree that the items in the following checklist have been met at the relevant readiness level.
We also recommend the virtual lab developer to repeat checking the guidelines in this document for each cycle of changes made to an existing virtual lab.

|                                  |                   |                                  | 1 | 2 | 3 | 4 | 5 |                                                                                                                                                                                                                                                                                                                                                        |
|----------------------------------|-------------------|----------------------------------|---|---|---|---|---|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Codebase                         |                   |                                  |   |   |   |   |   |                                                                                                                                                                                                                                                                                                                                                        |
|                                  | Data              | FAIR                             |   | X |   |   |   | Only FAIR data is used in the virtual lab.                                                                                                                                                                                                                                                                                                             
|                                  | Source code       |                                  |   |   |   |   |   | i.e. Notebooks and other code files included in the virtual lab.                                                                                                                                                                                                                                                                                       
|                                  |                   | Secrets are secret               |   | X |   |   |   | Personal tokens for APIs do not end up in version control when a user fills them in. ToDo Vlic: Guideline for secret management https://github.com/QCDIS/projects_overview/issues/276                                                                                                                                                                  
|                                  |                   | Executes without errors          |   | X |   |   |   | The code can be executed without errors: Currently, you can verify this by manually executing all cells in the notebook on a machine on which the code was not developed (to ensure no references are made to local resources).                                                                                                                        |
|                                  |                   | Parallel processing              |   | X |   |   |   | [Parallel processing](https://github.com/QCDIS/lifewatch-notebooks/blob/main/NaaVRE-tutorials/splitting-classic.ipynb) is applied where suitable.                                                                                                                                                                                                      |
|                                  |                   | Unit tests                       |   |   | X |   |   | The codebase has unit tests to verify the behavior of used methods and libraries. There should be a testing guideline, which will be done in this issue [\#274](https://github.com/QCDIS/projects_overview/issues/274).                                                                                                                                |
|                                  |                   | Architecture is described        |   |   |   | X |   | There is a description of the architecture of the virtual lab (e.g. There is a flowchart showing the notebook cells and classes).                                                                                                                                                                                                                      |
|                                  |                   | Community standard data exchange |   |   | X |   |   | The virtual lab reads, writes and exchanges data in a way that meets domain-relevant community standards. [5] <span style="color:green">I think we will need to consult some ecologists to determine these standards. I aditionally emailed Nafiseh. </span>                                                                                           |
|                                  | Code quality      | Clear responsibilities           |   | X |   |   |   | The responsibility of each cell in the notebook is clear and can be described in a single sentence.                                                                                                                                                                                                                                                    |
|                                  |                   | Easy to modify                   |   | X |   |   |   | The code within cells is easily human-readable and others can easily modify it. If methods have side effects, this is clear to the user.                                                                                                                                                                                                               |
|                                  |                   |                                  | 1 | 2 | 3 | 4 | 5 |                                                                                                                                                                                                                                                                                                                                                        |
| Containerized cells and Workflow | Containerization  | Containerizes without erros      |   | X |   |   |   | The notebook cells can be containerized.                                                                                                                                                                                                                                                                                                               |
|                                  | Execution         | Runs without nodifications       |   | X |   |   |   | The containerized cells can run without any modifications.                                                                                                                                                                                                                                                                                             |
|                                  | Input & Output    | Is clear                         |   | X |   |   |   | The input and output of each cell is clear. It is both clear what the structure is (e.g. what data type is used) and what the data content is from a domain perspective.                                                                                                                                                                               |
|                                  | PID               |                                  |   |   | X |   |   | Each containerized cell has a persistent identifier and version number <span style="color:green">(This is currently not a feature in NaaVRE. But might become possible in the future. Added to [potential ToDos](#potential-todos-for-lifewatch-vlic))</span>                                                                                          |
|                                  | Performance       | Is acceptable                    |   |   | X |   |   | The duration of computation, memory usage, and power usage of the container is acceptable. As there is currently no dashboard to monitor resource usage, contact the VLIC team for guidelines.                                                                                                                                                         |
|                                  | Interoperability  |                                  |   |   |   |   | X | The containerized cells and workflow are interoperable with other systems.                                                                                                                                                                                                                                                                             |
| Validation                       | Stability         | Is analysed                      |   |   |   |   | X | It is known how changing the parameters influences the outcome of the workflow.                                                                                                                                                                                                                                                                        |
|                                  | Uncertainty       | Is analysed                      |   |   |   |   | X | It is known how much outcomes vary between various workflow runs.                                                                                                                                                                                                                                                                                      |
|                                  | Fields            | Are all present                  |   |   |   | X |   | All the fields of the metadata standard should be present. ToDo VLIC: Choose a metadata standard.                                                                                                                                                                                                                                                      |
|                                  | Published         | Externally                       |   | X |   |   |   | The metadata is published outside the virtual lab. Tip: Create the metadata in the external catalogue to avoid duplicate effort.                                                                                                                                                                                                                       |
|                                  | Version control   | Is tracked                       |   | X |   |   |   | The description and metadata are tracked by version control, such that the changes to metadata can be viewed by virtual lab users.                                                                                                                                                                                                                     |
|                                  | Citation          | Is possible                      |   | X |   |   |   | It is possible to cite the virtual lab.                                                                                                                                                                                                                                                                                                                |
|                                  | Findable          | Search engine detectable         |   |   |   | X |   | Findable by search engines: Metadata is consumed by search engines.                                                                                                                                                                                                                                                                                    |
|                                  | Dependencies      | Are specified                    |   |   |   | X |   | Dependencies are specified. The dependencies are in the dockerfile, but should be duplicated in the metadata such that a person can in theory also run the source code on their own machine after installing the dependencies manually.                                                                                                                |
|                                  |                   |                                  | 1 | 2 | 3 | 4 | 5 |                                                                                                                                                                                                                                                                                                                                                        |
| Documentation                    | User manual       | Is present                       |   | X |   |   |   | There is a [user manual](#User-manual) for the virtual lab.                                                                                                                                                                                                                                                                                            |
|                                  |                   | Is reviewed                      |   |   | X |   |   | At least one domain scientist who was not involved in the development of the virtual lab has reviewed the user manual. The coding experience of the reviewer of the user manual is similar to the coding experience of the intended user.                                                                                                              |
|                                  | Different Dataset | Is addressed                     |   | X |   |   |   | How to use the virtual lab on a different dataset is explained.                                                                                                                                                                                                                                                                                        |
|                                  | Use case          | Are described                    |   |   | X |   |   | There is a description of use cases. This can be a link to another source (website / publication).                                                                                                                                                                                                                                                     |

#### User manual
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
- Storage location: The description of the virtual lab from an conceptual and mathematical viewpoint is stored on [NaaVRE.net](https://naavre.net/). 

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