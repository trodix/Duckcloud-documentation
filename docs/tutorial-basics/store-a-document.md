---
sidebar_position: 1
---

# Store a Document

Send a POST request

```sh
curl --location --request POST 'http://localhost:8010/upload' \
        --form "file=@/home/daffyduck/banana_salmon_recipe.pdf" \
        --form "directoryPath=/fruits" \
        --form "aspects=app-doc:fruit, app-doc:fish" \
        --form "properties[fruit:name]=banana" \
        --form "properties[fruit:weight]=50" \
        --form "properties[fruit:harvest-date]=2023-03-13" \
        --form "properties[fruit:reference]=GUYABANA123"

```

The response will be

``` json
{
    "uuid":"b459f5b4-1f51-4ab4-9e0d-62a5fc44afb4",
    "bucket":"root",
    "directoryPath":"/fruits",
    "versions": 1,
    "type":"cm:content",
    "aspects":[
        "app-doc:fruit",
        "app-doc:fish"
    ],
    "properties":{
        "fruit:harvest-date":"2023-03-13",
        "fruit:name":"banana",
        "fruit:reference":"GUYABANA123",
        "fruit:weight":"50",
        "cm:name":"banana_salmon_recipe.pdf"
    }
}
```
