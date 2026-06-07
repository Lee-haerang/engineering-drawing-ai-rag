# Engineering Drawing AI RAG

Engineering Drawing AI RAG is an open-source research prototype for understanding engineering drawings and CAD-derived documents using object detection, OCR, Knowledge Graph construction, and multimodal RAG-based question answering.

The goal of this project is to convert visual engineering drawings into structured, searchable, and explainable knowledge that can be used for natural-language search, Q&A, component summaries, and automatic report generation.

## Current Status

This repository is currently in an early open-source research-prototype stage.

The project is being developed as part of an undergraduate AI research direction focused on LLMs, multimodal RAG, and practical language-model systems for industrial documents. The initial focus is on building a clean, reproducible baseline that students, researchers, and small engineering teams can study, fork, and improve.

Codex support would help accelerate secure implementation, documentation, testing, refactoring, and reproducible examples.

## Problem Statement

Engineering drawings and CAD-derived documents contain important information such as equipment tags, pipe lines, valves, pumps, tanks, specifications, symbols, and process connections.

However, this information is often difficult to search, reuse, or verify because it is stored visually rather than in a structured format. A human engineer may understand the drawing, but software systems usually cannot directly answer questions such as:

- How many valves are in this drawing?
- Which pipe is connected to pump P-101?
- What equipment tags are shown in the document?
- Are there missing or inconsistent labels?
- Can this drawing be converted into a searchable knowledge structure?

This project aims to bridge that gap by combining computer vision, OCR, Knowledge Graphs, and multimodal RAG.

## Why This Matters

Many students, researchers, and small engineering teams want to experiment with AI-based drawing understanding, but there are few simple and reproducible open-source baselines for this task.

Industrial drawing AI usually requires multiple components working together:

- Object and symbol detection
- OCR-based text extraction
- Object-text linking
- Relationship extraction
- Structured data conversion
- Knowledge Graph construction
- LLM-based natural-language Q&A
- Report generation

This repository is designed to become a student-friendly and research-friendly reference implementation for engineering drawing AI.

## Key Features

Planned features include:

- Object and symbol detection from engineering drawings
- OCR post-processing for equipment tags, line numbers, and specifications
- Object-text relation extraction
- Structured JSON conversion
- Knowledge Graph construction for drawing structure and process flow
- Multimodal RAG-based natural-language search and Q&A
- Automatic report generation for detected components and possible design issues
- Reproducible demo notebooks and evaluation examples
- Beginner-friendly documentation for students and researchers

## Planned Architecture

The planned pipeline consists of the following stages:

```text
Engineering Drawing / CAD-derived Image
        ↓
Object and Symbol Detection
        ↓
OCR Text Extraction
        ↓
Object-Text Linking
        ↓
Structured JSON Conversion
        ↓
Knowledge Graph Construction
        ↓
Multimodal RAG Retrieval
        ↓
Natural-Language Q&A
        ↓
Automatic Report Generation
```

## Example Use Case

A user uploads a P&ID or CAD-derived drawing image and asks:

- "How many valves are in this drawing?"
- "Which pipe is connected to pump P-101?"
- "List all equipment tags and specifications."
- "Generate a summary report of detected components."
- "Find possible missing or inconsistent labels."

The system extracts visual objects and text, links them into structured data, builds a Knowledge Graph, retrieves relevant drawing context, and generates a natural-language answer using multimodal RAG.

## Sample Data Schema

The project will use simple, reproducible schemas so that students and researchers can easily understand and extend the system.

### Detected Object

```json
{
  "object_id": "P001",
  "type": "PIPE",
  "tag_no": "L-1001",
  "spec": "100A",
  "bbox": [120, 300, 80, 20]
}
```

### Detected Equipment

```json
{
  "object_id": "PU001",
  "type": "PUMP",
  "tag_no": "P-101",
  "spec": "MAIN",
  "bbox": [100, 200, 60, 60]
}
```

### Relationship

```json
{
  "source": "PU001",
  "target": "P001",
  "relation": "CONNECTED_TO"
}
```

### Example Graph Relationship

```text
PU001 ── CONNECTED_TO ── P001 ── CONNECTED_TO ── V001
```

## Planned Repository Structure

```text
engineering-drawing-ai-rag/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── docs/
│   ├── architecture.md
│   ├── security.md
│   └── roadmap.md
│
├── examples/
│   ├── sample_schema.md
│   ├── sample_objects.json
│   └── sample_relationships.json
│
├── src/
│   ├── ocr/
│   ├── detection/
│   ├── graph/
│   ├── rag/
│   └── reports/
│
├── notebooks/
│   └── demo.ipynb
│
└── tests/
```

## Roadmap

### Phase 1: Project Foundation

- [ ] Define sample drawing data schema
- [ ] Add example object and relationship JSON files
- [ ] Write architecture documentation
- [ ] Prepare initial prompt templates
- [ ] Create a simple demo workflow

### Phase 2: OCR and Object Understanding

- [ ] Build OCR post-processing module
- [ ] Normalize equipment tags, line numbers, and specifications
- [ ] Add object-text linking logic
- [ ] Create simple evaluation examples

### Phase 3: Knowledge Graph Construction

- [ ] Convert detected objects into graph nodes
- [ ] Convert object relationships into graph edges
- [ ] Add graph query examples
- [ ] Document the graph schema

### Phase 4: Multimodal RAG and Q&A

- [ ] Build retrieval pipeline for drawing context
- [ ] Add natural-language question answering
- [ ] Evaluate answers on sample questions
- [ ] Publish prompt templates and evaluation results

### Phase 5: Report Generation and Security

- [ ] Generate automatic drawing summary reports
- [ ] Detect possible missing or inconsistent labels
- [ ] Add tests for unsafe inputs
- [ ] Review dependency and secret-handling practices
- [ ] Improve documentation for open-source contributors

## Security Considerations

This project may handle API keys, uploaded drawing files, OCR outputs, prompts, generated reports, and structured engineering data. Security is important because open-source contributors may add scripts, dependencies, and data-processing modules over time.

Planned security practices include:

- Avoiding hardcoded API keys or secrets
- Using environment variables for credentials
- Reviewing dependencies for vulnerabilities
- Adding safe handling for uploaded files
- Avoiding the upload of confidential company drawings
- Testing prompt-injection risks in document Q&A
- Reviewing generated code before merging changes
- Using Codex Security to help detect unsafe code patterns before they are merged

## How API Credits Would Help

API credits would be used to build and evaluate a multimodal drawing-QA prototype.

Planned API usage includes:

- OCR post-processing experiments
- Object-text relation extraction
- Knowledge Graph and RAG answer generation
- Automatic report generation from sample drawings
- Prompt/version experiments
- Batch evaluation on example questions
- Demo notebooks for reproducible examples

The results, prompts, evaluation examples, and setup guide will be documented in this repository so that others can learn from and reproduce the workflow.

## Open Source Goals

The long-term goal of this repository is to provide a clean and reproducible baseline for engineering drawing understanding.

This includes:

- Beginner-friendly documentation
- Sample data schemas
- Modular code for OCR, detection, KG construction, and RAG
- Reproducible demo notebooks
- Evaluation examples
- Clear contribution guidelines for future collaborators
- Security-aware open-source development practices

## Intended Audience

This project is designed for:

- Undergraduate and graduate students studying AI
- Researchers interested in multimodal RAG
- Developers working with engineering documents
- Small engineering teams exploring AI-assisted drawing search
- Open-source contributors interested in practical LLM systems

## Research Direction

This project is aligned with practical language-model systems, multimodal AI, and retrieval-augmented generation.

Instead of building only a one-time demo, the goal is to create a reusable open-source reference that shows how engineering drawings can be converted into structured knowledge and queried with natural language.

## Disclaimer

This repository is currently an early research prototype.

It does not include confidential company drawings, private engineering documents, or production-ready industrial data. All examples will be synthetic, public, or simplified for educational and research purposes.

## License

This project is licensed under the MIT License.
