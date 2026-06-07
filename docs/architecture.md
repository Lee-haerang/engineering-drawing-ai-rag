# Architecture

This document describes the planned architecture for the Engineering Drawing AI RAG project.

## Overview

The goal of this project is to convert engineering drawings and CAD-derived documents into structured, searchable, and explainable knowledge.

The planned system combines object detection, OCR, object-text linking, Knowledge Graph construction, multimodal RAG, and natural-language Q&A.

## Pipeline

The planned pipeline consists of the following stages:

1. Drawing Input
2. Object and Symbol Detection
3. OCR Text Extraction
4. Object-Text Linking
5. Structured JSON Conversion
6. Knowledge Graph Construction
7. Multimodal RAG Retrieval
8. Natural-Language Q&A
9. Report Generation

## Pipeline Diagram

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

## Components

### 1. Drawing Input

The input may be an engineering drawing image, a scanned P&ID, or a CAD-derived image.

### 2. Object and Symbol Detection

This module detects visual elements such as pipes, valves, pumps, tanks, symbols, and other engineering components.

### 3. OCR Text Extraction

This module extracts text from drawings, including equipment tags, line numbers, specifications, and labels.

### 4. Object-Text Linking

This module links detected text to nearby or related visual objects.

### 5. Structured JSON Conversion

Detected objects and relationships are converted into a structured JSON format.

### 6. Knowledge Graph Construction

Objects become graph nodes, and connections between objects become graph edges.

### 7. Multimodal RAG Retrieval

Relevant drawing context is retrieved using both visual and structured information.

### 8. Natural-Language Q&A

Users can ask questions about the drawing using natural language.

### 9. Report Generation

The system generates summary reports about detected components, relationships, and possible inconsistencies.

## Current Status

This architecture is currently planned for an early open-source research prototype.
