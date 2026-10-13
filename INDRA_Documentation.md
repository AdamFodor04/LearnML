# INDRA Documentation

https://www.indra.bio/

This document is a practical reference for INDRA, a Python framework for assembling mechanistic models from biomedical knowledge extracted from text, databases, and structured sources. It is written as a documentation-style introduction rather than as a step-by-step exam answer sheet.

The goal is to help a learner understand what INDRA is, what kinds of problems it is built for, and which parts of the library are worth learning when working on mechanistic modeling or knowledge assembly tasks.

## 1. What INDRA is

INDRA is an open-source Python library for knowledge assembly and model construction in the life sciences. In practical terms, it helps connect several ideas:

- extract biological relationships from natural language and databases
- convert them to a common internal representation
- normalize, filter, and merge them
- assemble them into executable or analyzable models

INDRA is especially useful when the goal is to build a mechanistic model from heterogeneous evidence rather than from a single clean table.

Typical use cases include:

- extracting signaling or causal mechanisms from scientific literature
- integrating knowledge from multiple databases and readers
- assembling a network of protein or pathway interactions
- building a model for downstream simulation, analysis, or visualization
- comparing evidence and resolving contradictions between sources

## 2. Core concepts

### Statements

INDRA uses a common internal representation for biological relations called Statements. A Statement is a structured representation of a biological fact, such as a phosphorylation, activation, inhibition, binding, or regulation event.

Examples of types of biological knowledge INDRA can represent:

- activation
- inhibition
- phosphorylation
- dephosphorylation
- binding
- complex formation
- regulation
- translocation
- mutation effects

The key idea is that different source systems can all be converted into the same Statement format so they can be compared and assembled together.

### Agents and grounding

An Agent in INDRA represents a biological entity such as a protein, gene, complex, or chemical. In practice, INDRA usually tries to ground an agent to a canonical identifier so that different mentions of the same entity can be matched.

Grounding is important because the following might refer to the same biological entity:

- a protein name in the text
- a database entry
- a symbol used in a pathway database
- multiple different synonyms in different sources

INDRA includes tools for grounding and disambiguation when handling heterogeneous information.

### Evidence and belief

Each Statement can carry evidence. This may include provenance from a text source, database source, or other structured input. INDRA may also calculate belief or confidence scores based on the amount and quality of evidence supporting a statement.

This matters because the same relationship can appear in many places, sometimes with contradictory or partial evidence. The library includes logic for:

- redundancy detection
- contradiction detection
- generalization and subsumption
- belief scoring

### Preassembly and assembly

INDRA separates several stages of pipeline work:

- reading or extracting raw facts
- normalizing and mapping groundings
- filtering out low-quality or irrelevant statements
- assembling a model or network from the remaining statements

This makes INDRA useful for both data curation and computational modeling.

## 3. Main INDRA modules

### 3.1 Knowledge sources

The `indra.sources` package contains modules that convert biological knowledge from different sources into INDRA Statements.

Examples from the upstream INDRA README include:

- reading systems such as REACH, Sparser, Eidos, TEES, SemRep, and others
- biological pathway databases such as Signor, BioGRID, OmniPath, DrugBank, CTD, and others
- custom knowledge bases and exchange formats such as NDEx, Hypothesis, Biofactoid, and MINERVA

These source modules let INDRA pull in information from text mining pipelines, experiment databases, and pathway resources.

Useful conceptual categories:

- text mining readers
- pathway database readers
- curated interaction databases
- custom graph or exchange formats

### 3.2 Internal assembly and filtering

The `indra.preassembler` and `indra.tools.assemble_corpus` functionality are central for processing the extracted statements.

These modules can do things like:

- remove hypothetical statements
- map grounding across ontologies
- filter out ungrounded statements
- filter by evidence, source, or semantic role
- resolve duplicated or overlapping statements
- merge similar mechanistic statements

This is the stage where raw biological facts become something more reliable and model-ready.

### 3.3 Model assemblers

The `indra.assemblers` package turns assembled statements into an output representation or model. Several assemblers are available, including:

- PySB assembler for executable rule-based models
- PyBEL assembler for causal analysis and network representation
- SIF assembler for network-analysis workflows
- IndraNet for causal graph analysis
- KAMI for Kappa-like modeling support
- Graphviz, Cytoscape JS, CX, SBGN, and other visualization-oriented assemblers
- HTML, TSV, and English assemblers for curation and human-readable output

These assemblers allow INDRA to bridge biomedical knowledge with downstream systems for modeling, visualization, or research workflows.

## 4. Typical INDRA workflow

A common INDRA pipeline looks like this:

1. Retrieve knowledge from a source or database
2. Convert it to INDRA Statements
3. Merge and normalize statements
4. Filter low-confidence or ungrounded information
5. Assemble the cleaned corpus into a model or network
6. Visualize, export, or analyze the assembled result

This is the key principle behind INDRA: not just reading data, but converting data into a reusable mechanistic representation and then assembling a coherent model.

A conceptual pipeline from the upstream docs is:

```python
from indra.tools import assemble_corpus as ac

stmts = <collection of raw statements>
stmts = ac.filter_no_hypothesis(stmts)
stmts = ac.map_grounding(stmts)
stmts = ac.filter_grounded_only(stmts)
```

This example illustrates the sort of internal assembly operations that happen after knowledge is extracted.

## 5. Important libraries and concepts to know

### indra.sources

Use this when you are importing mechanistic knowledge from text mining tools or biological databases.

Examples of concerns here:

- how a source represents the evidence
- how entities are grounded
- whether the source includes statements that need filtering

### indra.preassembler

Use this when you want to normalize and combine knowledge.

Important ideas:

- grounding mapping
- contradiction resolution
- deduplication
- semantic filtering
- ontology-aware assembly

### indra.assemblers

Use this when you need an output format for the assembled knowledge.

Common choices:

- PySB for executable mechanistic models
- Causal graph representations for network analysis
- Graphviz or Cytoscape for visualization
- HTML or TSV for review and curation

### indra.tools.assemble_corpus

This is a practical entry point for building a robust assembly pipeline. It exposes several helpers for processing raw statements into higher-quality statements before model assembly.

## 6. Research use cases

INDRA is especially relevant for research because it can connect literature and pathway knowledge into a common mechanistic framework. It is useful in settings such as:

- disease mechanism discovery
- pathway reconstruction
- network analysis
- model generation from literature
- curation workflows
- mechanistic hypothesis testing

This makes it a strong tool for systems biology, computational biology, and biomedical knowledge integration work.

## 7. Typical scientific workflow

A realistic INDRA-based research workflow is usually:

1. collect text or structured knowledge
2. extract mechanistic events
3. standardize entities and relations
4. assemble a corpus
5. filter by confidence or domain relevance
6. produce a network or executable model
7. inspect results and refine the pipeline

That workflow is different from a standard tabular ML workflow. It is closer to knowledge representation and mechanistic model assembly.

## 8. Learning roadmap

If you want to learn INDRA effectively, a sensible progression is:

1. Learn the basic idea of Statements and evidence
2. Understand grounding and entity normalization
3. Learn how different knowledge sources produce statements
4. Practice filtering and assembly with `assemble_corpus`
5. Explore one or two assemblers, such as PySB or a graph-based assembler
6. Build a small research mini-project using a focused biological topic

## 9. Practical beginner checklist

Before using INDRA in a project, make sure you understand:

- what biological mechanism you want to represent
- which source(s) provide relevant knowledge
- whether entities are grounded correctly
- whether the statements need filtering or deduplication
- which output assembler matches your target result
- how you will evaluate the assembled model or network

## 10. Summary

INDRA is not a tabular ML library. It sits in the intersection of biomedical text mining, knowledge engineering, and systems biology. The major value is in turning noisy biological information into a structured, curated, mechanistic representation that can be assembled into models or networks.

The most useful mental model is:

- knowledge sources produce Statements
- preassembly filters and normalizes them
- assemblers convert them into a usable model or representation

This makes INDRA especially relevant for research-grade mechanistic modeling workflows.
