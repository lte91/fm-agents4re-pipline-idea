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
## Example Prompts

### Elicitation
Stakeholder Interview Transcription Prompts: Prompts used to correct and ensure the accuracy of transcribed text from stakeholder interviews.
````python
SYSTEM_PROMPT_ELICITATION = ''
````

### Analysis
Requirement Classification Prompts: Prompts classify requirements into functional (F) and non-functional (NF) categories.
````python
SYSTEM_PROMPT_ANALYSIS = 'You are a skilled requirements engineer. The requirements should be categorized as F (functional), NF (Non-Functional). You read the output of an automatic speech recognition system based on recordings from a meeting session. Your task is to extract requirements and other important information from the transcript and store it in a text file.'
    
USER_PROMPT_ANALYSIS   = 'Analyze the document: \n {transcript_file}. \n Classify the requirements into functional and non-functional requirements and store them in a list.'
````

### Documentation
Specification Generation Prompts: Prompts used to generate specifications based on classified functional requirements.
````python
SYSTEM_PROMPT_SPECIFICATION = ''
    
USER_PROMPT_SPECIFICATION   = ''
````

User Story Generation Prompts: Prompts used to generate user stories with acceptance criteria using a given template.
````python
SYSTEM_PROMPT_USER_STORY = ''
    
USER_PROMPT_USER_STORY   = ''
````

Task Breakdown Prompts: Prompts are used to break down high-level user stories into actionable tasks.
````python
SYSTEM_PROMPT_TASK = ''
    
USER_PROMPT_TASK   = ''
````

### Validation & Management
Traceability Matrix Prompts: Prompts used to generate a traceability matrix, linking all deliverables (requirements, specifications, user stories, and tasks).
````python
SYSTEM_PROMPT_TRACE = ''
    
USER_PROMPT_TRACE   = ''
````

---
## Results
This post presents the first results of a proof-of-concept using a prompting-based approach to facilitate preparatory tasks in all phases of requirements engineering, including elicitation, analysis, documentation, validation and management, as a precursor to the development of a comprehensive pipeline concept.

![sim_plot_all_similarity_final_2](https://github.com/user-attachments/assets/89ef487d-2209-4874-99a8-15212d5d7265)



