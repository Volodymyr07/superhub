---
title: Add a device to a location
excerpt: >-
  Add a new device to a location. The `serialNumber` and `id` can be found on
  the back of the device.

  Note that the `id` in this context is not the `serialNumber`, as it can be
  when requesting resources

  in other Airthings APIs. To use this endpoint, make sure your API client has
  the `write:device` scope

  enabled in the dashboard and that the `write:device` scope is added to your
  access token

  when requesting a token from the token endpoint.
api:
  file: ext-apiairthingscom-v1api-docsbusiness.json
  operationId: post_v1-locations-locationid-devices
hidden: false
---