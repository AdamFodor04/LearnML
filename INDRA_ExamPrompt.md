# INDRA Practical Exam Prompt

Create a practical, beginner-to-intermediate exam assignment for a student who has a working understanding of Python and basic biological or biomedical concepts. The assignment should focus on INDRA and should be designed so the student learns how to use INDRA to process mechanistic biological knowledge, assemble a model, and interpret the output.

The assignment should be realistic, research-oriented, and grounded in a real scientific workflow rather than a toy example.

## 1. Learning goal

The student should learn how to:

- understand the core concepts behind INDRA
- work with biological statements and evidence
- assemble a curated knowledge corpus
- apply filtering and grounding steps
- use an output assembler to generate a model or network
- interpret the assembled result in a meaningful way

The exam should test practical understanding rather than memorization.

## 2. Recommended difficulty level

This should be appropriate for a student who knows:

- Python basics
- dictionaries, lists, loops, functions, and classes
- Pandas is helpful but not strictly required
- basic molecular biology or systems biology concepts
- how to read and interpret scientific statements about genes, proteins, or pathways

The assignment should be realistic for someone beginning to learn knowledge modeling or systems biology workflows.

## 3. Dataset / input requirements

The exam should use a small, curated set of biological knowledge sources or statements rather than a full-scale literature corpus.

The student should be given one of the following:

- a small set of natural-language sentences describing signaling or regulatory mechanisms
- a curated list of statements or interactions in a text file or JSON-like format
- a small extracted dataset from a biological source such as a pathway database or mechanism summary
- a set of mechanisms involving a small number of genes, proteins, or chemicals

The input should be small enough to inspect manually but rich enough to require filtering, normalization, and assembly.

The data should include:

- at least one protein or gene entity
- at least one mechanism relationship such as activation, inhibition, phosphorylation, or binding
- some evidence or provenance information
- at least one ambiguous or duplicated relationship, so the student has to do assembly/filtering

Do not require the student to use a huge dataset or a full literature-scale extraction pipeline.

## 4. Required sections

Structure the exam in numbered tasks divided into logical sections such as:

1. Setup and installation
2. Understanding the biological problem
3. Reading or loading source data
4. Converting raw information into INDRA statements
5. Normalizing and filtering knowledge
6. Internal assembly and evidence handling
7. Model output assembly
8. Interpretation and reporting

## 5. Concrete task requirements

Each task should be objectively assessable. The student should implement or explain specific actions such as:

### Section 1: Setup and installation

- install the required INDRA dependencies in the environment
- verify the package imports correctly
- explain the purpose of INDRA in one or two sentences

### Section 2: Biological problem definition

- define a small mechanism or signaling pathway of interest
- identify the main biological entities involved
- describe the likely interaction types to be extracted
- explain why a standardized representation is useful

### Section 3: Source loading and statement extraction

- load the provided biological statements or natural-language inputs
- inspect the raw entities and relations
- identify whether the source data is structured, semi-structured, or text-based
- explain how these inputs would be converted into INDRA Statements

### Section 4: Statement conversion and normalization

- map entities to normalized names or biological identifiers where possible
- determine whether the data contains duplicates, inconsistent naming, or ambiguous references
- explain how grounding or normalization improves model assembly

### Section 5: Filtering and assembly

- apply at least one assembly or filtering step from the INDRA workflow
- remove or ignore ungrounded, hypothetical, or low-confidence statements
- describe the effect of the filtering step on the final corpus
- generate a processed statement list or assembled knowledge graph

### Section 6: Model output assembly

- pick one suitable output assembly format from the INDRA assemblers
- assemble the cleaned statements into a model or network representation
- justify the chosen assembler based on the problem goal
- if applicable, export the result in a human-readable or structural format

### Section 7: Interpretation

- summarize the resulting mechanism or pathway
- identify the most central genes, proteins, or interactions
- explain how evidence supports the assembled result
- describe a limitation or source of uncertainty

### Section 8: Reflection

- compare the original raw knowledge with the assembled model
- explain why knowledge assembly is needed in biomedical research
- discuss at least one plausible use of the assembled result in downstream analysis or modeling

## 6. Required evaluation criteria

The assignment should be judged on:

- correct installation and import use
- correct understanding of INDRA concepts
- thoughtful handling of groundings and evidence
- sensible filtering and assembly choices
- a logical explanation of the assembled mechanism
- proper interpretation of the model output
- ability to explain limitations and uncertainties

## 7. Recommended small project themes

Choose a theme that is narrow and manageable, such as:

- a small signaling pathway
- a cancer-related signaling mechanism
- inhibition/activation between a receptor and downstream kinase
- a drug-target or pathway interaction example
- a known mechanism with a small number of key proteins

Avoid overly broad topics or large-scale literature mining tasks for a beginner-level exam.

## 8. Output expectations

The final output should be a complete practical exam that includes:

- a short project description
- the biological problem statement
- clear numbered tasks
- required Python tooling and relevant INDRA concepts
- realistic assessment criteria
- a brief expected workflow description

The exam should not merely ask the student to recite INDRA terminology. It should ask them to use the framework in a realistic research workflow.

## 9. Suggested final structure

The exam should begin with a short section like:

### Project title
A small mechanistic modeling exercise with INDRA

### Research problem
Use INDRA to extract and assemble a small mechanistic network from a curated set of biomedical statements.

### Data
A small input corpus of statements describing a signaling pathway or molecular interaction network.

### Deliverables
- a cleaned and assembled set of statements
- a model or network assembled using an INDRA assembler
- a short written interpretation of the mechanism

The final result should be a practical assignment the student can complete in a notebook or script environment with realistic biomedical analysis goals.
