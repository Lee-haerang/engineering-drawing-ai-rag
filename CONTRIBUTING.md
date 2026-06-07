# Contributing

Thank you for your interest in contributing to Engineering Drawing AI RAG.

This project is currently in an early open-source research-prototype stage. The goal is to build a clean, reproducible, and student-friendly baseline for engineering drawing understanding, Knowledge Graph construction, and multimodal RAG-based question answering.

Contributions are welcome, especially in documentation, sample schemas, testing, prompt design, security review, and prototype implementation.

## Project Goals

This project aims to help students, researchers, and small engineering teams experiment with AI-based engineering drawing understanding.

The main goals are:

- Extract objects and symbols from engineering drawings
- Extract equipment tags, line numbers, and specifications using OCR
- Link detected objects with extracted text
- Convert drawing information into structured JSON
- Build a Knowledge Graph from detected components and relationships
- Enable multimodal RAG-based natural-language Q&A
- Generate automatic summary reports from drawing data
- Provide clear documentation and reproducible examples

## Good First Contributions

Good first contributions include:

- Improving documentation
- Fixing typos or unclear explanations
- Adding sample schemas
- Adding synthetic example data
- Adding OCR post-processing examples
- Writing simple tests
- Improving prompt templates
- Adding demo notebooks
- Reviewing security issues
- Improving project structure
- Adding beginner-friendly explanations

## Contribution Areas

### Documentation

Documentation is very important for this project because one of the goals is to make engineering drawing AI easier to understand for students and researchers.

Helpful documentation contributions include:

- Architecture explanations
- Setup guides
- Example workflows
- Data schema explanations
- RAG pipeline explanations
- Knowledge Graph examples
- Security notes
- Beginner-friendly tutorials

### Sample Data and Schemas

This project should not use confidential company drawings or private engineering documents.

Good sample data contributions include:

- Synthetic drawing examples
- Simplified object detection results
- Example OCR outputs
- Example object-text links
- Example Knowledge Graph relationships
- Example Q&A pairs
- Evaluation examples

### Code Contributions

Code contributions should be modular, readable, and easy to test.

Planned code modules include:

- OCR post-processing
- Object and symbol detection utilities
- Object-text linking
- Structured JSON conversion
- Knowledge Graph construction
- RAG retrieval
- Question answering
- Report generation
- Evaluation scripts

### Testing

Testing contributions are welcome.

Helpful tests include:

- JSON schema validation tests
- OCR post-processing tests
- Object-text linking tests
- Graph construction tests
- Retrieval tests
- Prompt safety tests
- End-to-end demo tests

## Development Guidelines

When contributing, please try to follow these guidelines:

- Keep changes clear and focused
- Write readable code
- Use meaningful file and variable names
- Add comments when the logic is not obvious
- Avoid unnecessary complexity
- Prefer small and understandable pull requests
- Update documentation when behavior changes
- Add examples when introducing a new feature

## Security Guidelines

Security is important because this project may involve API keys, uploaded files, OCR outputs, prompts, generated reports, and structured engineering data.

Please do not commit:

- API keys
- Access tokens
- Private engineering drawings
- Confidential company files
- Personal information
- Large unnecessary binary files
- Hardcoded secrets
- Credentials in notebooks or scripts

Recommended practices:

- Use environment variables for credentials
- Add secret files to `.gitignore`
- Use synthetic or public sample data
- Review dependencies before adding them
- Be careful with uploaded file handling
- Consider prompt-injection risks in document Q&A
- Review generated code before merging

## Data Policy

This repository should only use data that is safe to share publicly.

Allowed examples include:

- Synthetic drawings
- Public sample documents
- Simplified educational examples
- Manually created JSON examples
- Small mock datasets

Do not upload:

- Company-owned engineering drawings
- Private CAD files
- Confidential project documents
- Personal or sensitive information
- Data that cannot be legally shared

## Commit Message Style

Please use clear commit messages.

Good examples:

```text
Add sample schema documentation
Improve architecture documentation
Add OCR post-processing example
Fix typo in README
Add graph relationship examples
```

Less helpful examples:

```text
update
fix
stuff
final
```

## Pull Request Guidelines

Before opening a pull request, please check that:

- The change has a clear purpose
- The code or documentation is easy to understand
- No secrets or private files are included
- Examples are synthetic or safe to share
- Related documentation is updated
- The change fits the project goals

A good pull request description should explain:

- What was changed
- Why the change is useful
- How it can be tested or reviewed
- Whether it affects documentation, schemas, or examples

## Issue Guidelines

Issues are welcome for:

- Bugs
- Documentation improvements
- Feature ideas
- Security concerns
- Schema design discussions
- RAG evaluation ideas
- Knowledge Graph design suggestions
- Beginner questions

When opening an issue, please include as much context as possible.

Helpful information includes:

- What you expected
- What happened
- Relevant files or examples
- Suggested improvement
- Screenshots or sample outputs if useful

## Project Status

This repository is currently an early research prototype.

The project is not production-ready yet. Contributions that improve clarity, reproducibility, security, documentation, and educational value are especially helpful.

## Maintainer Note

This project is being developed as part of an undergraduate AI research direction focused on LLMs, multimodal RAG, and practical language-model systems for industrial documents.

The long-term goal is to make this repository a useful open-source reference for engineering drawing understanding and natural-language drawing Q&A.
