---
title: Get Job Summary
excerpt: >-
  Get a summary of your jobs broken down by Job Type. For each job type, you
  will see the number of jobs and number of credits consumed. The output
  includes 3 versions of the summary:

  1. All time summary with deleted jobs

  2. All time summary excluding deleted jobs

  2. Summary since start_date (defaults to previous billing date, includes
  deleted jobs)

  You may pass start_date as an optional query parameter in ISO format
  (yyyy-mm-dd).
api:
  file: openapi.json
  operationId: get_job_summary
hidden: false
---