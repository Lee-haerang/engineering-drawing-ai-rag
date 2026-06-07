# Sample Schema

This document provides example schemas for detected objects, extracted text, object-text links, relationships, and question-answering results in the Engineering Drawing AI RAG project.

The goal of this schema is to make the project easy to understand, reproduce, and extend for students, researchers, and open-source contributors.

## Overview

Engineering drawings and CAD-derived documents contain both visual elements and text information.

Examples include:

- Pipes
- Valves
- Pumps
- Tanks
- Equipment tags
- Line numbers
- Specifications
- Connection relationships

This project converts those elements into structured data so that they can be used for Knowledge Graph construction, multimodal RAG, natural-language Q&A, and automatic report generation.

## Detected Object Schema

A detected object represents a visual component found in a drawing.

```json
{
  "object_id": "P001",
  "type": "PIPE",
  "tag_no": "L-1001",
  "spec": "100A",
  "bbox": [120, 300, 80, 20],
  "confidence": 0.94
}
```

### Field Description

| Field | Description |
|---|---|
| `object_id` | Unique ID for the detected object |
| `type` | Object category such as PIPE, VALVE, PUMP, or TANK |
| `tag_no` | Equipment tag, line number, or component label |
| `spec` | Specification such as size, pressure rating, or material |
| `bbox` | Bounding box in `[x, y, width, height]` format |
| `confidence` | Detection confidence score |

## Example Detected Objects

```json
[
  {
    "object_id": "PU001",
    "type": "PUMP",
    "tag_no": "P-101",
    "spec": "MAIN",
    "bbox": [100, 200, 60, 60],
    "confidence": 0.96
  },
  {
    "object_id": "P001",
    "type": "PIPE",
    "tag_no": "L-1001",
    "spec": "100A",
    "bbox": [180, 225, 120, 20],
    "confidence": 0.93
  },
  {
    "object_id": "V001",
    "type": "VALVE",
    "tag_no": "V-201",
    "spec": "100A",
    "bbox": [320, 215, 35, 35],
    "confidence": 0.91
  },
  {
    "object_id": "T001",
    "type": "TANK",
    "tag_no": "TK-301",
    "spec": "STORAGE",
    "bbox": [430, 180, 90, 120],
    "confidence": 0.95
  }
]
```

## Extracted Text Schema

Extracted text represents OCR output from the drawing.

```json
{
  "text_id": "TXT001",
  "text": "P-101",
  "type": "EQUIPMENT_TAG",
  "bbox": [105, 180, 50, 15],
  "confidence": 0.98
}
```

### Field Description

| Field | Description |
|---|---|
| `text_id` | Unique ID for the extracted text |
| `text` | Text extracted by OCR |
| `type` | Text category such as EQUIPMENT_TAG, LINE_NUMBER, SPEC, or NOTE |
| `bbox` | Bounding box of the text region |
| `confidence` | OCR confidence score |

## Example Extracted Text

```json
[
  {
    "text_id": "TXT001",
    "text": "P-101",
    "type": "EQUIPMENT_TAG",
    "bbox": [105, 180, 50, 15],
    "confidence": 0.98
  },
  {
    "text_id": "TXT002",
    "text": "L-1001",
    "type": "LINE_NUMBER",
    "bbox": [210, 195, 65, 15],
    "confidence": 0.97
  },
  {
    "text_id": "TXT003",
    "text": "100A",
    "type": "SPEC",
    "bbox": [260, 195, 45, 15],
    "confidence": 0.96
  }
]
```

## Object-Text Link Schema

Object-text links connect detected visual objects with their related OCR text.

```json
{
  "object_id": "PU001",
  "text_id": "TXT001",
  "relation": "HAS_TAG",
  "confidence": 0.95
}
```

## Example Object-Text Links

```json
[
  {
    "object_id": "PU001",
    "text_id": "TXT001",
    "relation": "HAS_TAG",
    "confidence": 0.95
  },
  {
    "object_id": "P001",
    "text_id": "TXT002",
    "relation": "HAS_LINE_NUMBER",
    "confidence": 0.94
  },
  {
    "object_id": "P001",
    "text_id": "TXT003",
    "relation": "HAS_SPEC",
    "confidence": 0.92
  }
]
```

## Relationship Schema

Relationships describe how detected objects are connected to each other.

```json
{
  "source": "PU001",
  "target": "P001",
  "relation": "CONNECTED_TO",
  "confidence": 0.93
}
```

### Common Relationship Types

| Relation | Description |
|---|---|
| `CONNECTED_TO` | One component is physically connected to another |
| `FLOWS_TO` | Flow moves from one object to another |
| `HAS_TAG` | An object has a related equipment tag |
| `HAS_SPEC` | An object has a related specification |
| `HAS_LINE_NUMBER` | A pipe has a related line number |

## Example Relationships

```json
[
  {
    "source": "PU001",
    "target": "P001",
    "relation": "CONNECTED_TO",
    "confidence": 0.93
  },
  {
    "source": "P001",
    "target": "V001",
    "relation": "CONNECTED_TO",
    "confidence": 0.92
  },
  {
    "source": "V001",
    "target": "T001",
    "relation": "FLOWS_TO",
    "confidence": 0.89
  }
]
```

## Example Knowledge Graph

```text
PU001 ── CONNECTED_TO ── P001 ── CONNECTED_TO ── V001 ── FLOWS_TO ── T001
```

## Example Structured Drawing Record

```json
{
  "drawing_id": "DRAWING_SAMPLE_001",
  "drawing_type": "P&ID",
  "objects": [
    {
      "object_id": "PU001",
      "type": "PUMP",
      "tag_no": "P-101",
      "spec": "MAIN",
      "bbox": [100, 200, 60, 60],
      "confidence": 0.96
    },
    {
      "object_id": "P001",
      "type": "PIPE",
      "tag_no": "L-1001",
      "spec": "100A",
      "bbox": [180, 225, 120, 20],
      "confidence": 0.93
    },
    {
      "object_id": "V001",
      "type": "VALVE",
      "tag_no": "V-201",
      "spec": "100A",
      "bbox": [320, 215, 35, 35],
      "confidence": 0.91
    }
  ],
  "relationships": [
    {
      "source": "PU001",
      "target": "P001",
      "relation": "CONNECTED_TO",
      "confidence": 0.93
    },
    {
      "source": "P001",
      "target": "V001",
      "relation": "CONNECTED_TO",
      "confidence": 0.92
    }
  ]
}
```

## Example Questions and Expected Answers

### Question 1

```text
Question:
Which pipe is connected to pump P-101?

Expected Answer:
Pump P-101 is connected to pipe L-1001.
```

### Question 2

```text
Question:
How many valves are in this drawing?

Expected Answer:
There is 1 detected valve in this drawing: V-201.
```

### Question 3

```text
Question:
List all detected equipment tags.

Expected Answer:
The detected equipment tags are P-101, L-1001, V-201, and TK-301.
```

### Question 4

```text
Question:
Generate a short summary of this drawing.

Expected Answer:
This drawing contains a pump P-101 connected to pipe L-1001. The pipe is connected to valve V-201, and the flow continues toward tank TK-301.
```

## Notes

This schema is intentionally simple and readable.

The current schema is designed for an early research prototype. It may be expanded later to support additional drawing types, more detailed CAD metadata, graph database integration, evaluation metrics, and multimodal RAG experiments.
