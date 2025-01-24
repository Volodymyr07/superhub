---
title: Refund Payment
excerpt: >-
  Refunds a payment. First will check if the users wallet has credits to refund
  the payment. If so, will take the

  credits from the users wallet and refund the payment. Otherwise, will transfer
  USDC from the merchants wallet to

  Coinflow's wallet and refund the payment.The amount of USDC transferred will
  the total amount of the payment +

  credit card fees + gas fees.
api:
  file: swagger (2).json
  operationId: RefundPayment
hidden: false
---