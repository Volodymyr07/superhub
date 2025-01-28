---
title: Create a New Sticky Session
excerpt: >
  Create a new sticky session using proxy credentials.


  ## Sticky Ports:

  Geonode provides specific ports for sticky sessions, ensuring a persistent IP
  session:


  - **HTTP/HTTPS:** 10000 - 10900

  - **SOCKS5:** 12000 - 12010


  Use sticky ports when you need a stable IP for session-based activities.


  **Authentication & Proxy Setup:**

  - **Proxy (`-x`)**: `http://premium-residential.geonode.com:10000`

  - **Authorization Header**: Automatically generated from ReadMe authentication
  when username and password are entered.


  **Example `cURL` Request to Create a Sticky Session:**

  ```sh

  curl -x "http://premium-residential.geonode.com:10000" \
       -U "myUsername-country-US-session-random0001:myPassword" \
       --url "http://ip-api.com/json" \
       --header "Accept: application/json"
  ```
api:
  file: country-targeting-18-proxy-enable.yaml
  operationId: get_
hidden: false
---