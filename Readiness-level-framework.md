# Readiness level framework for virtual labs in NaaVRE

This draft version contains some parts with a high level of doubt, which are marked in <span style="color:green">green</span>.

Version 1.0.0   
Published <span style="color:green">current date</span>

The aim of this readiness level framework is to guide virtual lab developers by giving recommendations of what to include in their virtual lab and what to prioritize. 
The document first describes the content of virtual labs in NaaVRE and roles to create a common viewpoint of the software and the users.
Next it describes six readiness levels in which the virtual lab can be. It then proceeds with checklists that guide
virtual lab creators to get their virtual lab to the next readiness level.

### Content of a virtual lab
A virtual lab in NaaVRE can contain two types of assets:
- [Source code](#Source-code).
- [Containerized cells and workflow](#containerized-cells-and-workflow).    

Besides assets, we encourage the creator of a virtual lab to support the usability of the assets, by creating the following documents:
- [Metadata](#Metadata).
- [Documentation](#Documentation), including a tutorial.
- Software management plan <span style="color:green">(Do we need a virtual lab to specify who is planning to upkeep the virtual lab? Shall we focus on getting a readiness level framework which mentions a software management plan, and work out the details of what should be in the software management plan later? I think a software management plan belongs to a readiness level which no lab will currently reach.)</span>

Currently, NaavRE is mostly used for scientific Workflows e.g. data processing, data analysis, and simulation. 

### Roles  
People with different roles will be interacting in different ways with the virtual lab. We discern the following roles for people who interact with a virtual lab:
- A virtual research environment developer / NaaVRE developer working at LifeWatch VLIC.
- A virtual lab developer / person creating the content of the virtual lab. This document is aimed to be a guideline for people with this role.
- A virtual lab user. A virtual lab user can be a domain scientist or policy maker.
  - Domain scientists: Uses the virtual lab in their research. Domain scientists are expected to have at least some coding experience.
    - Depending on what stage the lab is in, we discern two types of domain scientists:
      - Golden user: Enters the virtual lab in an early stage of development. The use case of the golden user requires changes to the virtual lab. They will co-develop the virtual lab together with the virtual research environment developer.
      - General user: This user enters the virtual lab when it is finished enough for the domain scientists to use the virtual lab on their own.
  - Policy maker: Uses the virtual lab to run a scenario to get information that is used in making decisions. Policymakers are expected to not make changes to the code.

### Readiness levels
We discern six readiness levels in the development of a virtual lab, where each new virtual lab starts at level 1.

1. Development: The lab is being developed by the virtual lab developer(s). It makes no sense for other users to use the virtual lab at this point, like a user would not do an experiment in a lab if instruments and equipment are being installed.
2. Testing: On request by the virtual lab developer(s) other virtual lab developer(s) who are not involved in the development of this specific virtual lab, can review the virtual lab and do suggestions. The lab can be executed with guidance from the virtual lab developer.
3. Golden user: A scientist who can co-develop the lab further with the virtual research environment developers (and the virtual lab developer) to apply it to their own research question and publish the results.
4. Workshop: The lab can be used by multiple workshop participants under the guidance of an instructor that can point out what the user can change and can not change in the lab. 
5. General use: An ecologist can use the lab for their research.
6. Policymaker use: The model or pipeline has been verified and validated and outcomes can be used to give policy advise.

For the content of the virtual lab, the next paragraphs provide guidelines of what to keep in mind during the development 
and what requirements the virtual lab should meet at different levels of readiness. For each stage the requirements from 
the stages with lower numbers apply as well. The numbers between brackets (e.g. "[1]") indicate at which readiness level 
the guideline should be implemented before proceeding with the actions associated with the readiness level. We recommend 
the virtual lab developer to repeat checking the guidelines in this document when sharing a change to a virtual lab with others.

## Assets
For the assets the following checklist describes what a virtual lab would ideally contain:

### Source code
- Only FAIR data is used in the virtual lab. [3]  
- Source code (Notebooks and other code files included in the virtual lab)
  - The code can be executed without errors. Currently, you can verify this by manually executing all cells in the notebook. [2]
  - Secrets are secret: Personal tokens for APIs do not end up in version control when a user adds them. [2] <span style="color:green"> I am now assuming we can easily make this happen by creating a .env file in the jupyter lab, adding an ignore rule to Gitignore for this file and instructing users to reference this file whenever using secrets? IN that case I should make a tutorial for this. </span>
  - <span style="color:green">NaaVRE block comment [Insert link to block comment tutorial, or create block comment tutorial]</span>: A block comment at the top of each cell labels the inputs, outputs, dependencies, and parameters, making it possible for the component containerizer to identify them correctly. [2]
  - Clean virtual lab / code quality [3]
    - There is a description of the architecture of the virtual lab (e.g. There is a flowchart showing the notebook cells and classes).
    - The responsibility of each cell in the notebook is clear and can be described in a single sentence.
    - The code within cells is easily human-readable and others can easily modify it. If methods have side effects, this is clear to the user.
  - Versioning:
    - The code is available on a repository with version control (e.g. git). [2]
      - The version control tool allows others to suggest changes.
    - The code has a version number. [3]
    - Versions of used software and libraries are explicitly set to prevent compatibility problems. [5]
  - [Parallel processing](https://github.com/QCDIS/lifewatch-notebooks/blob/main/NaaVRE-tutorials/splitting-classic.ipynb) is applied where suitable. [3]
  - Unit tests: Notebook cells, and methods have unit tests to document their behavior. [4]
  - The virtual lab reads, writes and exchanges data in a way that meets domain-relevant community standards. [5] <span style="color:green">I think we will need to consult some ecologists to determine these standards. I emailed Nafiseh. </span>
- Validation [6]
    - Stability analysis: It is known how changing the parameters influences the outcome of the workflow.
    - Uncertainty analysis: It is known how much outcomes vary between various workflow runs.

### Containerized cells and Workflow
- The notebook cells can be containerized. [2]
- Run successfully: The containerized cells can run without any modifications. [2]
- The input and output of each cell is clear. It is both clear what the structure is (e.g. what data type is used) and what the data content is from a domain perspective. [3]
- Each containerized cell has a Guid and version number <span style="color:green">(This is currently not a feature in NaaVRE. But might become possible in the future. Added to [potential ToDos](#potential-todos-for-lifewatch-vlic))</span> [4]
- The duration of computation, memory usage, and power usage of the container is acceptable. Whenever in doubt, contact the LifeWatch VLIC team. [4]
- The containerized cells and workflow are interoperable with other systems. <span style="color:green">Is this something that should be possible using the "Export" button in the experiment manager. Does this always result in an exception? Tried looking into the documentation: https://naavre.net/docs/tutorials/#compose-a-workflow , but didn't find it.</span> [6]

## Documents 
Besides creating assets, virtual lab creators are encouraged to create documentation for their virtual lab to aid others to easily understand and find their way in the virtual lab.

### Metadata
- Metadata is encouraged and should eventually at least have the following content: [3] 
  - A globally unique identifier (Guid). 
  - An indication of when the virtual lab has been developed. 
  - Where the virtual lab is stored / published <span style="color:green">(Isn't this the same for all virtual labs?)</span>. 
  - By whom the virtual lab is tested.
  - license. <span style="color:green"> Should we leave it to the virtual lab developer to choose the license. Or should we push for use of the Apache license? </span>
  - Primary point of contact. 
- The description and metadata are also tracked by version control, such that the changes to metadata can be viewed by virtual lab users. [3]
- It is possible to cite the virtual lab. [3]
- Findable by search engines: Metadata is consumed by search engines. See [fair software checklist](https://fairsoftwarechecklist.net/v0.2/). [5]
  - [ToDo VLIC](#potential-todos-for-lifewatch-vlic): <span style="color:green">VLIC may need to enable detection by search engines. Can we currently facilitate detection by search engines?</span>
- Dependencies are specified. <span style="color:green">(Can we easily show the packages we're installed into the flavor? My expectation is that VLIC would currently have to provide a list of dependencies)</span> [5]
- The metadata is stored outside NaaVRE and will remain available should NaaVRE become unavailable. [5]


### Documentation
- There is a [user manual](#User-manual) for the virtual lab. [2]
  - At least one domain scientist who was not involved in the development of the virtual lab has reviewed the user manual. [4]
- How to use the virtual lab on a different dataset is clear. [3]
- There is a description of use cases. This can be a link to another source (website / publication). [4]

#### User manual
The following guidelines can be used to determine the completeness of a user manual. 
- What happens in the workflow is explained from the following viewpoints:
  - A conceptual viewpoint. There is an intuitive description of what happens.
  - A mathematical viewpoint. How the real world system relates to the used mathematical algorithm is clear.
- The parameters are clear.
    - It is clear what the ecological meaning of the parameter is.  
    - It is clear how to change these parameters.
- There is a tutorial: Virtual lab developers are strongly encouraged to create a tutorial for virtual labs early on in the development. In the simplest case this is the existing main notebook with a description of the processes that occur during execution.  
  - The tutorial can be done without supervision.
- Known potential pitfalls in using the virtual lab are described.
- There is a description of the standards used for data exchange with application programming interfaces and databases.

## Sources
- These recommendations are partially based on ideas presented in the paper [Introducing the FAIR Principles for research software](https://www.nature.com/articles/s41597-022-01710-x) and the [Fair software checklist](https://fairsoftwarechecklist.net/v0.2/).

## Potential ToDos for LifeWatch VLIC
- Findable by search engines. See [Metadata](#Metadata).
- Containerized cells get a Guid and version number. See [Containerized cells and Workflow](#containerized-cells-and-workflow).
- Software management plan: Shall we focus on getting a readiness level framework which mentions a software management plan, and work out the details of what should be in the [software management plan](https://zenodo.org/records/7248877) later? See [content of a virtual lab](#content-of-a-virtual-lab).

## Feedback
Any feedback on this document is appreciated. Please contact the LifeWatch VLIC team.