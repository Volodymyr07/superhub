---
title: Register User
excerpt: >-
  Performs a Know-Your-Customer check for a particular user. Will create  a
  withdrawer record for the user if one does not exist.

  If the user has previously used coinflow to withdraw, the wallet will be added
  to the withdrawer record.

  Note: If `x-coinflow-auth-wallet` in request headers is not associated with a
  user, the wallet will get added to the newly created /existing user withdrawer
  record.
api:
  file: swagger (2).json
  operationId: CreateKyc
hidden: false
---