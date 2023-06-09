---
title: Import postman collection
category: Tools Setup
permalink: tools/import_postman_collection
order: 20
---

When building the REST API for the app, we added all the api routes to a postman collection to share between the teams. So this became a useful collection to list all the required api and their path that we use in the app. It is pretty helpful when debugging the app behaviors and finding bugs.

The Houzi Rest API plugin contains a postman collection, that can be imported to postman to test different apis
You can download here: [Postman Collection](https://raw.githubusercontent.com/booleanbites/houzi-rest-api/main/HouziAppApi.postman_collection.json)

Install and activate.
A normal flow would be login first, get the auth token and use this auth token for everything that requires authentication.
API uses bearer token auth approach.
