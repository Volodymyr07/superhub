---
title: 'Recalculate Expense Review Process '
excerpt: >-
  Endpoint to recalculate the `ExpenseReviewProcess` a transaction is included
  into. This is particularly useful in case a change made on an
  `ExpenseReviewProcess` configuration should be applied to already existing
  transactions. In case a recalculated transaction is included into the same
  `ExpenseReviewProcess`, the transaction will remain assigned to the same
  approval step. This endpoint supports up to 100 transactions per single
  request.
api:
  file: soldo-bapi-v2_4.24.0-SNAPSHOT.json
  operationId: expense-review-process-recalculate
hidden: false
---