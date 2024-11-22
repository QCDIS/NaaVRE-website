Create a checklist that describes what we expect from virtual labs to exist at different stages of development.

[The list presented here is based on my own expectations. Literature should still be checked for recommended methods]

### ToDo
- See how viewpoints are important here.
- Add a glossary with the most important concepts.
- Say something about unit testing

### Aim
The aim of the readiness level framework is to guide virtual lab developers with recommendations of what to include in their virtual lab and what to prioritize in order to be able to share the lab with potential users as early on in the process.

### Content of a virtual lab
A virtual lab contains assets that are developed by an initial user which can be shared with others. Currently, a virtual lab can contain two types of assets:
- [Notebook / source code](#Notebook-/-Source-code): Containing workflows, e.g. data processing, data analysis, and/or simulation workflows.
- [Containerized cells and workflow](#containerized-cells-and-workflow).    

Besides assets, we encourage the creator of a virtual lab to support the usability of the assets, by creating the following documents:
- Content description / Metadata.
- Documentation, including a tutorial.
- Software management plan: <span style="color:green">Do we need a virtual lab to specify who is planning to upkeep the virtual lab? Shall we focus on getting a maturity level framework which mentions a software management plan, and work out the details of what should be in the software management plan later? I think a software management plan belongs to a maturity level which no lab will currently reach.</span>

### Roles  
People with different roles will be interacting in different ways with the virtual lab. We discern the roles for people who interact with a virtual lab:
- A virtual research environment developer at LifeWatch VLIC
- A virtual lab developer / person creating the content of the virtual lab
- A virtual lab user. A virtual lab user can be a domain scientist or policy maker.
    - A user can have the following role in an organization:
      - Domain scientists: Uses the virtual lab in their research. Domain scientists are expected to have variable coding experience.
        - Depending on what stage the lab is in, we discern two types of domain scientists:
          - Golden user: Enters the virtual lab in an early stage of development. The use case of the golden user requires changes to the virtual lab. They will co-develop the virtual lab together with the virtual research environment developer.
          - General user: This user enters the virtual lab when it is finished enough for the domain scientists to use the virtual lab on their own.
      - Policy consultant / maker: Uses the virtual lab to run a scenario to get information that is used in making decisions. Policy makers are expected to not make changes to the code.

### Content description / metadata
- Content: 
  - globally unique identifier (Guid), 
  - when written, 
  - where stored / published (Isn't this the same for all?), 
  - tested by whom.
  - license.
  - Primary point of contact. 
- Findable by search engines: Metadata is consumed by search engines. See [fair software checklist](https://fairsoftwarechecklist.net/v0.2/).
  - [ToDo VLIC](#potential-todos-for-lifewatch-vlic): VLIC may need to enable detection by search engines. 
- Dependencies are specified. <span style="color:green">(Can we easily show the packages we're installed into the flavor?)</span>
- Is it possible to cite the virtual lab?
- The metadata is stored outside NaaVRE and will remain available should NaaVRE become unavailable.
- The description and metadata also version control.

### Documentation
- Readme / user manual for the virtual lab: see user manual.
- Use cases:
     - Description of use cases: This can be a link to another source (website / publication)
- Tutorial: At LifeWatch we stress the importance of training in transferring the knowledge needed to use a virtual lab. Virtual lab developers are strongly encouraged to create a tutorial for virtual labs early on in the development. This can simply be the existing default notebook with a description of the processes that occur during execution.

### Notebook / Source code
- Data
  - FAIR: The data used in the virtual lab is FAIR data.  
- Source code 
  - Code is present: The code is present and accessible through a notebook.
  - Executes without errors: The code can be executed without errors. Currently, you can verify this by manually executing all cells in the notebook.
  - Versioning:
    - The code has a version number.
    - Versions of used software and libraries are explicitly set to prevent compatibility problems.
  - The code is available on a repository with version control (e.g. git).
    - The version control tool allows others to suggest changes.
  - Secrets are secret: Personal tokens for APIs are not in the lab and do not end up in version control when a user adds them.
  - <span style="color:green">NaaVRE block comment [Insert link to block comment tutorial, or create block comment tutorial]</span>: A block comment at the top of each cell labels the inputs, outputs, dependencies, and parameters, making it possible for the component containerizer to identify them correctly. 
  - [Parallel processing](https://github.com/QCDIS/lifewatch-notebooks/blob/main/NaaVRE-tutorials/splitting-classic.ipynb) is applied where suitable.
  - Unit tests: Notebook cells, and methods have unit tests to document their behavior.
  - Clean virtual lab / code quality
    - There is a description of the architecture of the virtual lab (e.g. There is a flowchart showing the notebook cells and classes).
    - The responsibility of each cell in the notebook is clear and can be described in a single sentence.
    - The code within cells is easily human-readable and others can easily modify it. If methods have side effects, this is clear to the user.
- Validation
    - Stability analysis: It is known how changing the parameters influences the outcome of the workflow. 
    - Uncertainty analysis: It is known how much outcomes vary between various workflow runs. 

### Containerized cells and Workflow
- The notebook cells can be compiled.
- The input and output of each cell is clear. It is both clear what the structure is (e.g. what data type is used) and what the data content is from a domain perspective. 
- Run successfully: The containerized cells can run without any modifications.
- Each containerized cell has a Guid and version number? (Is this going  to be maintainable?)
- The performance is optimized.
- The cells and workflow are interoperable with other systems.

### User manual
The following items are quality checks for the documentation of the virtual lab which are subject to the perspective of the user:
- What happens in the notebook is conceptually clear.
- What happen is the notebook is mathematically clear.
- The parameters are clear.
    - It is clear what the ecological meaning of the parameter is.  
    - It is clear how to change these parameters.
- How to use the virtual lab on a different dataset is clear.
- Known potential pitfalls in using the virtual lab are described.
- By what standards is data exchanged with application programming interfaces or databases?

### Readiness levels
A virtual lab can be in 6 stages. For each stage the requirements must apply and all requirements from the stages with lower numbers:

1. Development: The lab is being developed by the virtual lab developer(s). It makes no sense for other users to use the virtual lab at this point, like a user would not do an experiment in a lab if instruments and equipment are being installed.
2. Testing: On request by the virtual lab developer(s) other virtual lab developer(s) who are not involved in the development of this specific virtual lab, can review the virtual lab and do suggestions. The lab can be executed with guidance from the virtual lab developer.
3. Quality check: The lab is finished. The developer(s) of the virtual lab can request others to review the lab (using the model created here to check for completeness).
4. Workshop / golden user: The lab can be used by users under the guidance of an instructor that can point out what the user can change and can not change in the lab. 
5. General use: An ecologist can use the lab for their research.
6. Policy maker use: The model or pipeline has been verified and validated and outcomes can be used to give policy advise.

### Readiness level 1: Development
The lab exists. No further requirements.

### Readiness level 2: Testing
- Model / data pipeline & Code: Code is present. 
- Containerized cells: Run successfully.

### Readiness level 3: Quality check
- Content description / metadata: Is present.
- Documentation: Readme / user manual, use cases, and tutorial are present.

### Readiness level 4: Try out
- Documentation: Is good enough to be understandable by at least one domain specialist who has not been involved in developing the virtual lab. There is a tutorial which runs.
- Model / data pipeline & Code: 
  - For the tutorial scenario the code runs. 
  - Verified. 
  - There are ideas on how to validate the model.
- Containerized cells: Run successfully.

### Readiness level 5: Domain specialist use
- Content description / Metadata: Is complete.
- Documentation: Is complete. There is consensus that the user manual is comprehensible (peer review approved?). The tutorial can be walked through without supervision.
- Model / data pipeline & Code.
    - Code: Executes without errors.

### Readiness level 6: Policy maker use
- Model / data pipeline & Code.
    - Validation: The model has been validated and the validation method is documented.

### Sources
- These recommendations are partially based on ideas presented in the paper [Introducing the FAIR Principles for research software](https://www.nature.com/articles/s41597-022-01710-x) and the [Fair software checklist](https://fairsoftwarechecklist.net/v0.2/).

### Potential ToDos for LifeWatch VLIC
- Findable by search engines
- Software management plan: Shall we focus on getting a maturity level framework which mentions a software management plan, and work out the details of what should be in the software management plan later?