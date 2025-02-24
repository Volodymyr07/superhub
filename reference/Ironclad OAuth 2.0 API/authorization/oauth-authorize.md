---
title: Initiate an Authorization Transaction
excerpt: >-
  This endpoint is used to request authorization from a user to access their
  Ironclad data on their behalf. This is the initial request of an Authorization
  Code grant flow. The client application generally initiates the authorization
  flow, where a user will be redirected to Ironclad to log in and grant the
  requested permissions. The user is then redirected back to the client
  application redirect URI with an authorization code. See endpoint
  [specification](https://datatracker.ietf.org/doc/html/rfc6749#section-3.1).
api:
  file: openapi-oauth.json
  operationId: oauth-authorize
hidden: false
---