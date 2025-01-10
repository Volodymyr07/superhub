---
title: Create a Workflow
excerpt: >-
  Use this endpoint to create a workflow that triggers when a document is
  submitted.


  The workflow can be configured to either:

  1. Always run the specified schema(s) on the document, set via the
  `standardizeStep` input.

  2. Conditionally run one or more schemas based on the document's `classId`,
  set via the `classifyStandardizeStep` input.


  Note: You must provide one of these inputs, but not both.


  To run the workflow, use the `POST /document` endpoint with the `workflowId`
  that gets returned from this endpoint. 
api:
  file: openapi (2).json
  operationId: post_workflow_on_submit_document
hidden: false
---