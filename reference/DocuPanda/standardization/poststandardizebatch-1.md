---
title: Standardize Documents
excerpt: >-
  Standardize a batch of one or more documents all at once, either by passing a
  list of Document IDs or by passing a dataset name.Use the forceRecompute flag
  to optionally reprocess documents that have already been standardized.


  *Advanced*: You can specify a standardization mode to control how the AI sees
  the document. The options are:

  1. `default` - Automatically determine the best mode based on the document
  content.

  2. `sectionBased` - Represent the document as a list of sections (paragraphs,
  tables, images, etc.), the same ones you see in the document `result` field.

  3. `spatial` - Represent text in the document according to its spatial layout.
api:
  file: openapi (2).json
  operationId: post_standardize_batch
hidden: false
---