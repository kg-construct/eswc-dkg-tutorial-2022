# Example request


POST https://proxy-pre-production.onlim.com/api/rck/api/v1/map

Content-Type: application/json

x-api-key: ...
```json
{
  "mappingConfig": {
    "compress": {
      "@vocab": "https://schema.org/"
    },
    "functions": {
      "http://myfunc.com/asEnum": "(([str]) => {\n        return {\"@id\": 'https://schema.org/' + str };\n    })",
      "http://myfunc.com/asTime": "(([str]) => {\n        return {'@type': 'http://www.w3.org/2001/XMLSchema#time', '@value': str + ':00' };\n    })",
      "http://myfunc.com/asDateTime": "(([str]) => {\n        return {'@type': 'http://www.w3.org/2001/XMLSchema#dateTime', '@value': new Date(str).toISOString() };\n    })",
      "http://myfunc.com/orEmptyString": "(([str]) => {\n        return typeof str === 'string' ? str : '';\n    })"
    }
  },
  "description": "RocketRML Demo Mapping",
  "name": "RocketRML Demo Mapping",
  "testDataSet": [
    {
      "id": null,
      "value": "...",
      "type": "json"
    }
  ],
  "mappingFileType": "yarrrml",
  "mappingFile": "..."
}```