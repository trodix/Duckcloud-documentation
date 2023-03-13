---
sidebar_position: 2
---

# Search a Document

## Search by node id

```sh
curl --location 'http://localhost:8010/node/5208e2a7-0cf7-4ed9-bb7e-709891ce7b21'
```

This request will return

```json
{
    "uuid": "5208e2a7-0cf7-4ed9-bb7e-709891ce7b21",
    "bucket": "root",
    "directoryPath": "/fruits",
    "versions": 1,
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

## Search by path

```sh
curl --location 'http://localhost:8010/node?path=/fruits'
```

This request will return

```json
[
    {
        "uuid": "5208e2a7-0cf7-4ed9-bb7e-709891ce7b21",
        "bucket": "root",
        "directoryPath": "/fruits",
        "versions": 1,
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
]
```

## Search with a metadata

Search for files with the property `fruit:name` equals to `banana`

```sh
curl --location 'http://localhost:8010/search' \
        --header 'Content-Type: application/json' \
        --data '{
            "term": "properties.fruit:name",
            "value": "banana"
        }'
```

This request will return

```json
{
    "resultCount": 1,
    "items": [
        {
            "identifier": "/fruits",
            "parent": null,
            "value": {
                "uuid": "5208e2a7-0cf7-4ed9-bb7e-709891ce7b21",
                "bucket": "root",
                "directoryPath": "/fruits",
                "contentType": null,
                "versions": 1,
                "type": "cm:content",
                "aspects": [
                    "app-doc:fruit",
                    "app-doc:fish"
                ],
                "properties": {
                    "cm:name": "dummy.pdf",
                    "fruit:name": "banana",
                    "fruit:weight": 50.0,
                    "fruit:reference": 123456789
                }
            }
        }
    ]
}
```

## Search in file content

Search for files with the property `fruit:name` equals to `banana`

```sh
curl --location 'http://localhost:8010/search' \
        --header 'Content-Type: application/json' \
        --data '{
            "term": "cm:content",
            "value": "sugar"
        }'
```

This request will return

```json
{
    "resultCount": 1,
    "items": [
        {
            "identifier": "/fruits",
            "parent": null,
            "value": {
                "uuid": "5208e2a7-0cf7-4ed9-bb7e-709891ce7b21",
                "bucket": "root",
                "directoryPath": "/fruits",
                "contentType": null,
                "versions": 1,
                "type": "cm:content",
                "aspects": [
                    "app-doc:fruit",
                    "app-doc:fish"
                ],
                "properties": {
                    "cm:name": "dummy.pdf",
                    "fruit:name": "banana",
                    "fruit:weight": 50.0,
                    "fruit:reference": 123456789
                }
            }
        }
    ]
}
```
