# Security Policy

Security is important for Engineering Drawing AI RAG because this project may handle API keys, uploaded files, OCR outputs, prompts, generated reports, and structured engineering data.

This project is currently in an early open-source research-prototype stage, but security-aware development is part of the project direction from the beginning.

## Supported Versions

This repository is currently under early development.

| Version | Supported |
|---|---|
| main branch | Yes |
| experimental branches | Limited |

## Security Goals

The project aims to reduce risks related to:

- Hardcoded API keys or secrets
- Accidental upload of confidential engineering drawings
- Unsafe file handling
- Vulnerable dependencies
- Prompt-injection risks in document Q&A
- Unsafe generated code
- Insecure handling of OCR outputs and generated reports

## Sensitive Data Policy

Please do not upload or commit:

- API keys
- Access tokens
- Private engineering drawings
- Confidential company CAD files
- Internal project documents
- Personal information
- Credentials in notebooks or scripts
- Large unnecessary binary files

Only synthetic, public, simplified, or educational sample data should be used in this repository.

## Recommended Practices

Contributors should:

- Use environment variables for credentials
- Keep `.env` files out of version control
- Review generated code before committing
- Avoid hardcoded secrets
- Use synthetic examples when possible
- Review dependencies before adding them
- Be careful with uploaded file processing
- Consider prompt-injection risks when building RAG workflows

## Prompt Injection Considerations

Because this project may use multimodal RAG and document-based Q&A, prompt injection is an important concern.

Potential risks include:

- Malicious text hidden inside uploaded drawings
- OCR-extracted instructions that try to manipulate the model
- User-uploaded documents containing unsafe prompts
- Generated reports that include untrusted document content

Future work will include testing and documenting prompt-injection defenses for drawing-based Q&A.

## Reporting a Security Issue

If you find a security issue, please open a GitHub issue with a clear description.

Please include:

- What the issue is
- Where it appears
- Why it may be risky
- Suggested mitigation if available

Do not include real secrets, private drawings, or sensitive files in the issue.
