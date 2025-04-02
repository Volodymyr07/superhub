---
title: Update EasySecure user photo.
excerpt: >-
  The gdprConsent property of the ESUser needs to be set to true before calling
  this endpoint. The user needs to be presented with a GDPR approval form first
  before uploading any photo to EasySecure.The request body needs to be a
  multipart request. The photo should be added as a part with the name file.
  Only photos with extensions JPG and PNG can be uploaded to EasySecure.
api:
  file: posting-api.json
  operationId: post_integration_easysecure_users_photo
hidden: false
---