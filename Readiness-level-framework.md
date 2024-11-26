# Readiness level framework for virtual labs in NaaVRE

This draft version contains some parts with a high level of doubt, which are marked in <span style="color:green">green</span>.

Version 1.0.0   
Published <span style="color:green">current date</span>

The aim of this readiness level framework is to guide virtual lab developers by giving recommendations of what to include in their virtual lab and what to prioritize. 
The document first describes the content of virtual labs in [NaaVRE](https://naavre.net/) and roles to create a common viewpoint of the software and the users.
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

### Virtual lab contributions
NaaVRE aims to be a virtual research environment that enables people with expertise in computational ecology or ecological data analysis,
to create of virtual labs in which users can conduct their research.
Our platform aims at obtaining the following contributions  to enable innovative research methods:
- Virtual research environment development and operations: Creating and maintaining the software in which virtual labs can be created. This is done by LifeWatch.
- Virtual lab core development: The creation of a new virtual lab in NaaVRE. Virtual lab core development is done in a 
co-development process with the DevOps engineers at LifeWatch. 
- Virtual lab development: In personal instances of existing virtual labs users can change the source code to suit their needs.
- Virtual lab use. Researchers couple virtual labs assets, use their own datasets, and set their own parameters to run their own experiments.

In the virtual labs the distinction between development and use is a continuum. How many changes a scientist 
will make to the source code depends on whether the virtual lab already has the necessary assets for the user.

#### Wetlab analogy
If we compare the development of a virtual research environment to the construction of a wetlab, 
the virtual research environment development and operations is the same phase as the construction of a building and rooms that house the wetlabs. 
The core development of a virtual lab would be the same phase as the installation and calibration of the wetlab equipment. 
In order to get the power supply, water supply, ventilation, and drainage pipes in the right locations in the lab,
the equipment installers and construction workers need to coordinate their efforts, like co-development is done for the virtual lab.
Once a lab is finished, the doors of the lab open for researchers to use the equipment in the lab to do their research. 
They can also create custom settings on the lab equipment to suit their needs, likewise a NaaVRE user could do development to change the source code to suit their own research.

### Readiness levels
We discern six readiness levels in the development of a virtual lab. A new virtual lab starts at level 1.

1. Core Development: Core development of the virtual is taking place.
2. Testing: On request of the virtual lab core developer(s) others who were not involved in the development of this specific virtual lab, can review the virtual lab and do suggestions.
3. Golden use: A scientist, who can also be a core developer, can co-develop the lab further with the virtual research environment developers to apply it to their own research question and publish the results.
4. Workshop: The lab can be used by multiple workshop participants under the guidance of an instructor that can point out what the user can safely change and can not change in the lab. 
5. General use: Any ecologist can use the lab for their research. 
6. Policymaker use: The model or pipeline has been verified and validated and outcomes can be used to give policy advise.

For the content of the virtual lab, the following checklists provide guidelines of what to keep in mind during the development 
and what requirements the virtual lab should meet at different levels of readiness. For each stage the requirements from 
the stages with lower numbers apply as well. The numbers between brackets (e.g. "[1]") indicate at which readiness level 
the guideline should be implemented before proceeding with the actions associated with the readiness level. We recommend 
the virtual lab developer to repeat checking the guidelines in this document for each cycle of changes made to an existing virtual lab.

## Assets
For the assets the following checklists describe what a virtual lab would ideally comply to:

### Source code
- Only FAIR data is used in the virtual lab. [3]  
- Source code: i.e. Notebooks and other code files included in the virtual lab.
  - Secrets are secret: Personal tokens for APIs do not end up in version control when a user fills them in. [2] <span style="color:green"> I am now assuming we can easily make this happen by creating a .env file in the jupyter lab, adding an ignore rule to Gitignore for this file and instructing users to reference this file whenever using secrets? IN that case I should make a tutorial for this. </span>
  - A block comment at the top of each cell labels the inputs, outputs, dependencies, and parameters, making it possible for the component containerizer to identify them correctly. [2] <span style="color:green"> [Insert link to block comment tutorial, or create block comment tutorial]</span>
  - The code can be executed without errors: Currently, you can verify this by manually executing all cells in the notebook on a machine on which the code was not developed (to ensure no references are made to local resources). [3]
  - Code quality [3]
    - The responsibility of each cell in the notebook is clear and can be described in a single sentence.
    - The code within cells is easily human-readable and others can easily modify it. If methods have side effects, this is clear to the user.
  - Versioning:
    - The code is available on a repository with version control (e.g. git). [2]
      - The version control tool allows others to suggest changes. [3]
    - The code has a version number. [3]
    - Versions of used software and libraries are explicitly set to prevent compatibility problems. [5]
  - [Parallel processing](https://github.com/QCDIS/lifewatch-notebooks/blob/main/NaaVRE-tutorials/splitting-classic.ipynb) is applied where suitable. [3]
  - Unit tests: Notebook cells, and methods have unit tests to document their behavior. [4]
  - There is a description of the architecture of the virtual lab (e.g. There is a flowchart showing the notebook cells and classes). [5]
  - The virtual lab reads, writes and exchanges data in a way that meets domain-relevant community standards. [5] <span style="color:green">I think we will need to consult some ecologists to determine these standards. I emailed Nafiseh. </span>

### Containerized cells and Workflow
- The notebook cells can be containerized. [2]
- The containerized cells can run without any modifications. [2]
- The input and output of each cell is clear. It is both clear what the structure is (e.g. what data type is used) and what the data content is from a domain perspective. [3]
- Each containerized cell has a persistent identifier and version number <span style="color:green">(This is currently not a feature in NaaVRE. But might become possible in the future. Added to [potential ToDos](#potential-todos-for-lifewatch-vlic))</span> [4]
- The duration of computation, memory usage, and power usage of the container is acceptable. As there is currently no dashboard to monitor resource usage, contact the VLIC team for guidelines. [4]
- The containerized cells and workflow are interoperable with other systems. <span style="color:green">(Is this something that should be possible using the "Export" button in the experiment manager. Does this always result in an exception? Tried looking into the documentation: https://naavre.net/docs/tutorials/#compose-a-workflow , but didn't find it.)</span> [6]
- Validation [6]
    - Stability analysis: It is known how changing the parameters influences the outcome of the workflow.
    - Uncertainty analysis: It is known how much outcomes vary between various workflow runs.

## Documents 
Besides creating assets, virtual lab creators are encouraged to create documentation for their virtual lab to aid others to easily learn to find their way in the virtual lab.

### Metadata
- We encourage creating metadata which at least has the following content: [3] 
  - A persistent identifier. 
  - A first publication date.
  - A last modification date.
  - Where the virtual lab is stored / published <span style="color:green">(Isn't this the same for all virtual labs?)</span>. 
  - By whom the virtual lab is tested.
  - A license. <span style="color:green"> (Should we leave it to the virtual lab developer to choose the license, recommend looking at https://choosealicense.com/ , or should we push for use of the Apache license?) </span>
  - Primary point of contact. 
- The description and metadata are tracked by version control, such that the changes to metadata can be viewed by virtual lab users. [3]
- It is possible to cite the virtual lab. [3]
- Findable by search engines: Metadata is consumed by search engines. [5]
  - [ToDo VLIC](#potential-todos-for-lifewatch-vlic): <span style="color:green">VLIC may need to enable detection by search engines. Can we currently facilitate detection by search engines? See [fair software checklist](https://fairsoftwarechecklist.net/v0.2/).</span>
- Dependencies are specified. <span style="color:green">(Can we easily show the packages we're installed into the flavor? My expectation is that VLIC would currently have to provide a list of dependencies)</span> [5]
- The metadata is stored outside NaaVRE and will remain available should NaaVRE become unavailable. [5]


### Documentation
- There is a [user manual](#User-manual) for the virtual lab. [2]
  - At least one domain scientist who was not involved in the development of the virtual lab has reviewed the user manual. [4]
  - The coding experience of the reviewer of the user manual is similar to the coding experience of the intended user. [4]
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
- There is a tutorial: Virtual lab developers are strongly encouraged to create a tutorial for virtual labs early on in the development. In the simplest case, this is the existing main notebook with a description of the processes that occur during execution.  
  - The tutorial can be done without supervision.
- Known potential pitfalls in using the virtual lab are described.
- There is a description of the standards used for data exchange with application programming interfaces and databases.

## Sources
- These recommendations are partially based on ideas presented in the paper [Introducing the FAIR Principles for research software](https://www.nature.com/articles/s41597-022-01710-x), the [Fair software checklist](https://fairsoftwarechecklist.net/v0.2/), and [fair-software.eu](https://fair-software.eu/recommendations/license).

## Potential ToDos for LifeWatch VLIC
- Create a way to make the virtual lab findable by search engines. See [Metadata](#Metadata).
- Make NaaVRE generate a persistent identifier and version number for containerized cells. See [Containerized cells and Workflow](#containerized-cells-and-workflow).
- Software management plan: Shall we focus on getting a readiness level framework which mentions a software management plan, and work out the details of what should be in the [software management plan](https://zenodo.org/records/7248877) later?

## Feedback
Any feedback on this document is appreciated. Please contact the LifeWatch VLIC team if you have any questions or comments on the document.