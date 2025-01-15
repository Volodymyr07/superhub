---
title: Generate a Visual Review
excerpt: >-
  This endpoint is used to generate a visual review of the standardization
  results. For every value in the standardization payload, we generate a
  confidence score and a a list of locations, where a location is page number
  and x1,y1,x2,y2 bounding box coordinate on that page, designating the top left
  and lower right corner of the bounding box. This indicates where in the
  doucment the value was found.
api:
  file: openapi.json
  operationId: post_review_batch
hidden: false
---