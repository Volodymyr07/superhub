---
title: Get Checkout Jwt Token
excerpt: |-
  Gets a Checkout Jwt Token for a purchase

  Checkout JWT tokens ensure:
  1. The arguments of the purchase cannot be manipulated
  2. The checkout JWT is only valid for a single purchase
  3. The arguments of the purchase are encrypted to be hidden from the user
   (webhook info, chargebackProtectionData, etc...)
api:
  file: swagger (2).json
  operationId: GetCheckoutJwtToken
hidden: false
---