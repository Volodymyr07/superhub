---
title: Request a Token
excerpt: >-
  This endpoint is used to request a token from the authorization server. If requesting an initial token in the Authorization Code grant, an authorization code, client ID, and client secret must be provided. If requesting to refresh an existing token in the Authorization Code grant, a refresh token, client ID, and client secret must be provided. If requesting a token via the Client Credentials grant, a client ID and secret must be provided. See endpoint [specification](https://datatracker.ietf.org/doc/html/rfc6749#section-3.2).
api:
  file: openapi-oauth.json
  operationId: oauth-token
hidden: false
---
