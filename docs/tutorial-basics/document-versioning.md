---
sidebar_position: 3
---

# Document versionning

You can create multiple versions on a document and go back to the previous one when you need it.

## Create a new version of a document

```sh
curl --location --request PUT 'http://localhost:8010/565f5016-59a9-4830-8b2e-6983705967bc/upload' \
        --form 'file=@"/run/user/1000/doc/3b2bcbdb/dummy.pdf"'
```

This request will return

```json
{
    "uuid": "5208e2a7-0cf7-4ed9-bb7e-709891ce7b21",
    "bucket": "root",
    "directoryPath": "/fruits",
    "versions": 2,
    "type": "cm:content",
    "aspects": [
        "app-doc:fruit",
        "app-doc:fish"
    ],
    "properties": {
        "fruit:harvest-date": "2023-03-12T23:00:00.000+00:00",
        "cm:name": "dummy.pdf",
        "fruit:name": "banana",
        "fruit:weight": 50.0,
        "fruit:reference": 123456789
    }
}
```

## Retrieve a specific version of a document

We created a new version for our document, the document exists in 2 versions.

If we want to display the document for the version 1, we can do:

```sh
curl --location 'http://localhost:8010/node/13f51e28-5afa-4afa-bac0-b7c4ac63ed71/version/1/content'
```

This request will return the file content for the version `1`
