Create a checklist that describes what we expect from virtual labs to exist at different stages of development.

[The list presented here is based on my own expectations. Literature should still be checked for recommended methods]

**ToDo**
- Add licensing
- Check for secrets
- We should also have a higher level notion of what we offer to the users.
- See how viewpoints are important here.
- Add a glossary with the most important concepts.

**Roles**
The following roles are involved in the development and use of a virtual lab:
- A virtual research environment engineer / scientific software developer at LifeWatch VLIC
- A virtual lab developer / person creating the content of the virtual lab
- A virtual lab user. 
    - A user can do the following:
        - Run the containerized model or pipeline
        - Use components of the virtual lab to create their personalized virtual lab
    - A user can have the following role in an organization:
        - Domain scientists: Uses the virtual lab in their research.
        - Policy consultant / maker: Uses the virtual lab to run a scenario to get information that is used in making decisions.
(Here there is no difference between a domain specialist or policy maker, they can do the same things, but typically a domain specialist will make more changes to the code, while a policy maker will only change the scenario).

**Content of virtual lab**
The following items can be present in a virtual lab:
- Content description / Metadata
- Documentation
- Model / data pipeline & Code
- Containerized cells
- Software management plan: Do we need a virtual lab to specify who is planning to upkeep the virtual lab?

**Content description / metadata**
- Content: globally unique identifier, when written, where stored / published (Isn't this the same for all?), tested by whom
- Findable by search engines: Metadata is consumed by search engines. See [fair software checklist](https://fairsoftwarechecklist.net/v0.2/).
- Dependencies are specified.

**Documentation**
- Readme / user manual for the virtual lab: see user manual.
- Use cases:
     - Description of use cases: This can be a link to another source (website / publication)
     - Tutorial: This can simply be the existing default notebook with a description of the processes that occur during execution.

**Model / data pipeline & Code**
- Data
  - FAIR: The data used in the virtual lab is FAIR data.  
- Code 
  - Code is present: The code is present and accessible through a notebook. 
  - The code has a version number.
  - The code is available on a repository with version control (e.g. git).
  - Executes without errors: The code can be executed without errors.
  - Secrets are secret.
  - Input and output variables of cells are documented (present in the comment block in the top of the cell).
  - Batch processing is applied where necessary.
  - Versions are explicitly set to prevent compatibility problems.
  - Clean virtual lab
    - The architecture of the virtual lab is described (e.g. The is a flowchart showing the classes).
    - The responsibility of each cell in the notebook is clear.
    - The  code within cells is understandable and can be easily modified by others.
    - Making changes to the code does not result in unexpected effects.
- Verification
    - The model implementation is correct.
- Validation
    - Stability analysis: Determine for the parameters how changing them influences the outcome of the simulation or pipeline. 
    - Uncertainty analysis: Determine for outcomes how much they vary for various simulation runs. 

**Containerized cells**
- The notebook cells can be compiled.
- The input and output of each cell is clear. It is both clear what the structure is (e.g. what data type is used) and what the data content is from a domain perspective. 
- Run successfully: The containerized cells can run without any modifications.

**Common requirements**
- Of all documents the user can see what changes have been made.

**User manual**
The following items are quality checks for the documentation of the virtual lab which are subject to the perspective of the user:
- What happens in the the notebook is conceptually clear.
- What happen is the notebook is mathematically clear.
- The parameters are clear.
    - It is clear what the ecological meaning of the parameter is.  
    - It is clear how to change these parameters.
- How to use the virtual lab on a different dataset is clear.
- Known potential pitfalls in using the virtual lab are described.

**Readiness levels**
A virtual lab can be in 6 stages. For each stage the requirements must apply and all requirements from the stages with lower numbers:

1. Development: The lab is being developed by the virtual lab developer(s). It makes no sense for other users to use the virtual lab at this point, like a user would not do an experiment in a lab if instruments and equipment are being installed.
2. Testing: On request by the virtual lab developer(s) other virtual lab developer(s) who are not involved in the development of this specific virtual lab, can review the virtual lab and do suggestions. The lab can be executed with guidance from the virtual lab developer.
3. Quality check: The lab is finished. The developer(s) of the virtual lab can request others to review the lab (using the model created here to check for completeness).
4. Try out: The lab can be used by users under the guidance of an instructor that can point out what the user can change and can not change in the lab. 
5.  Domain specialist use: An ecologist can use the lab for their research.
6. Policy maker use: The model or pipeline has been verified and validated and outcomes can be used to give policy advise.

**Readiness level 1: Development**
The lab exists. No further requirements.

**Readiness level 2: Testing**
- Model / data pipeline & Code: Code is present. 
- Containerized cells: Run successfully.

**Readiness level 3: Quality check**
- Content description / metadata: Is present.
- Documentation: Readme / user manual, use cases, and tutorial are present.

**Readiness level 4: Try out**
- Documentation: Is good enough to be understandable by at least one domain specialist who has not been involved in developing the virtual lab. There is a tutorial which runs.
- Model / data pipeline & Code: 
  - For the tutorial scenario the code runs. 
  - Verified. 
  - There are ideas on how to validate the model.
- Containerized cells: Run successfully.

**Readiness level 5: Domain specialist use**
- Content description / Metadata: Is complete.
- Documentation: Is complete. There is consensus that the user manual is comprehensible (peer review approved?). The tutorial can be walked through without supervision.
- Model / data pipeline & Code.
    - Code: Executes without errors.

**Readiness level 6: Policy maker use**
- Model / data pipeline & Code.
    - Validation: The model has been validated and the validation method is documented.