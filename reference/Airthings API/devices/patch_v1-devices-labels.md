---
title: Set device labels
excerpt: >-
  Set labels on one or more devices, creating labels that do not exist and
  updating labels that do exist.

  Labels can only be set for devices that have an active segment. If the active
  segment for a device ends

  (becomes inactive), the labels set by this endpoint will be cleared, and
  labels will have to be set 

  again. This endpoint is idempotent provided that none of the devices operated
  on have their active segment

  changed between requests.
api:
  file: ext-apiairthingscom-v1api-docsbusiness.json
  operationId: patch_v1-devices-labels
hidden: false
---