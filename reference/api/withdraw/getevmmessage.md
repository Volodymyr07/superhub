---
title: Get Message (EVM USDC/SBC/EuroE only)
excerpt: |-
  Gets any messages to be signed by the user, the signed message is then passed
  as the `evmPermitMessage` body property into the
  `/api/withdraw/evm/transaction` endpoint.

  This is only necessary for EVM chains.
api:
  file: swagger (2).json
  operationId: GetEvmMessage
hidden: false
---