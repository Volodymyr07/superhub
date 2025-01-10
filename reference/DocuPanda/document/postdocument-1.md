---
title: Submit a Document for Processing
excerpt: >-
  Use this endpoint to submit documents to DocuPanda for processing. You can
  upload a local file or provide a URL to a remote file. Upon submission,
  receive a unique `documentId` which you may use to retrieve the document's
  results, or apply subsequent workflows on it. Max document size is 500 pages


  *Advanced*: you may also provide a `workflowId` to apply a pre-defined
  workflow to the document.
api:
  file: openapi (2).json
  operationId: post_document
hidden: false
---