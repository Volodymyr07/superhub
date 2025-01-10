---
title: Analyze Data
excerpt: >-
  Analyze multiple documents all at once, either by passing a list of Document
  IDs or by passing a dataset name. If both are pased, we will use the
  intersection of the two. Analysis works by passing a list of questions in
  natural language. If a schemaId is passed, the AI will first use the
  standardizations of those documents under the provided schema to narrow down
  which documents are relevant. Only then, it will analyze the documents and
  provide answers to the questions, along with confidence scores and citations.

  If a schemaId is not passed, the AI will manually examine all documents, with
  a limit of 50.
   When schemaId is passed, the AI can optionally also perform database queries for statistical calculations and         answer the questions based on those results.
api:
  file: openapi-(2).json
  operationId: post_analyze_data
hidden: false
---