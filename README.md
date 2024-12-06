# From Elicitation to Management: A Comprehensive Pipeline for Requirements Engineering with Foundation Models

This repository provides a proof-of-concept implementation of the pipeline proposed in the paper "From Elicitation to Management: A Comprehensive Pipeline for Requirements Engineering with Foundation Models". The pipeline leverages foundation models, illustration can be found below, such as large language models and code generators, to support all phases of Requirements Engineering (RE), including elicitation, analysis, documentation, validation, and management.

![MAS-System(2)](https://github.com/user-attachments/assets/947d3990-efd6-467c-85b6-76c8670c991d)

---
Contents:
- Prompts and Patterns: This directory contains the specific prompt patterns and templates designed for each RE phase to guide the LLMs in generating and refining RE deliverables.
- Results: This directory includes sample outputs from the PoC experiment, showcasing the generated RE deliverables across different phases, such as classified requirements, specifications, user stories, tasks, and traceability matrices.

> Note: 
> This repository is intended to provide a starting point for further research and development, rather than a production-ready implementation. The prompts and results provided will inspire and guide future work in this area.

---
## Prompt Pattern & Example Prompts

The prompt pattern involves defining the role and expertise of the user, specifying the task they are to perform, and sometimes providing a template or structure to follow. Each prompt begins by establishing that the user is an "experienced requirements engineer and an expert" in a specific domain, followed by their task, such as creating documents, user stories, tasks, or traceability tables.

````
Fundamental Form:
System-Prompt
                    <Persona><Expertise><Objective/Task><Instructions/Template(if applicable)>

User-Prompt
                    <Instruction><Task> for each <Scope> in the {<Input_File/Previous_Result>}, proceed step-by-step and create <Output_Documentation> based on the template:\n{<Template_File>}.
````

### Elicitation
Stakeholder Interview Transcription Prompts: Prompts used to correct and ensure the accuracy of transcribed text from stakeholder interviews.
````python
SYSTEM_PROMPT_ELICITATION = 'You are a helpful and competent assistant. Your task is to correct all spelling and grammatical errors in the transcribed German text. Only add necessary punctuation marks such as periods, commas and capitalization and only use the given context. Simplify the text by deleting unnecessary words, expressions or sentences without changing the core statements or the given context.'
````

### Analysis
Requirement Classification Prompts: Prompts classify requirements into functional (F) and non-functional (NF) categories.
````python
SYSTEM_PROMPT_ANALYSIS = 'You are an experienced requirements engineer and an expert in analyzing stakeholder requirements. All stakeholder requirements are to be classified into F (functional) and NF (non-functional) requirements by reading and understanding the output of an automatic speech recognition system based on recordings of a meeting. Its task is to extract F and NF requirements and other important information from the transcript.'
    
USER_PROMPT_ANALYSIS   = 'Analyze the document: \n{transcript_file}.\n Classify the requirements into F (functional) and NF (non-functional) requirements. Proceed step by step with your analysis and save it in a requirements template:\n{requirements_template}.'
````

### Documentation
Specification Generation Prompts: Prompts used to generate specifications based on classified functional requirements.
````python
SYSTEM_PROMPT_SPECIFICATION = 'You are an experienced requirements engineer and an expert in writing requirements and functional specifications. Your task is to create a document that describes all functional and non-functional requirements in a requirements or functional specification.'
    
USER_PROMPT_SPECIFICATION   = 'For each functional requirement in the {requirements}, go step-by-step and create specification documentation based on the template:\n{specification_template}.'
````

User Story Generation Prompts: Prompts used to generate user stories with acceptance criteria using a given template.
````python
SYSTEM_PROMPT_USER_STORY = 'You are an experienced requirements engineer and an expert in writing user stories. Based on the following user story template: \n'As a [user type], I want to perform [a task] so that I can achieve [a goal].'\nYour task is to create user stories for all functional requirements.'
    
USER_PROMPT_USER_STORY   = 'For each functional requirement in the {requirements}, think step by step and create a list of user stories based on the template:\n{userStory_template}.'
````

Task Breakdown Prompts: Prompts are used to break down high-level user stories into actionable tasks.
````python
SYSTEM_PROMPT_TASK = 'You are an experienced requirements engineer and an expert in formulating acceptance criteria and tasks based on user stories for software developers. Your task is to break down each user story into small tasks.'
    
USER_PROMPT_TASK   = 'Proceed step-by-step for each user story in the {user_stories} and create acceptance criteria for the individual user stories as well as a list of tasks based on the template:\n{tasks_template}.'
````

### Validation & Management
Traceability Matrix Prompts: Prompts used to generate a traceability matrix, linking all deliverables (requirements, specifications, user stories, and tasks).
````python
SYSTEM_PROMPT_TRACE = 'You are an experienced requirements engineer and expert in tracing documentation by understanding their relationships based on given documents. Your task is to list each requirement with its related specification and user story and the software tasks based on the user story in a table.'
    
USER_PROMPT_TRACE   = 'For each requirement from the {requirements} documentation, as well as the associated {specifications}, {user_stories} and {tasks}, proceed step-by-step and create documentation for the traceability of a requirements work product in the form of a Requirements Traceability Matrix (RTM) based on the template:\n{tracing_template}.'
````

---
## Results
This post presents the first results of a proof-of-concept using a prompting-based approach to facilitate preparatory tasks in all phases of requirements engineering, including elicitation, analysis, documentation, validation, and management, as a precursor to the development of a comprehensive pipeline concept. The presented approach leverages foundation models to support a multi-agent system, demonstrating the potential of AI-driven methods in streamlining and augmenting human capabilities throughout the RE process. 

The results, as shown in the plot below, illustrate the similarity scores achieved by the foundation model in generating relevant content for each RE phase, highlighting the promise of this approach in automating preparatory tasks and enhancing the overall efficiency of requirements engineering.
![sim_plot_all_similarity_final_2](https://github.com/user-attachments/assets/89ef487d-2209-4874-99a8-15212d5d7265)



