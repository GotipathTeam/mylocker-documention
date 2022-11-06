<p align="center"><a href="https://gotipath.com" target="_blank"><img src="./logos/issuer.png" width="200"></a></p>

## Work Flow for Issuer Side Process

## How to Push Document through API
- Register on Issuer Poratal
- Add Document Type
- Create Access Token
- Document Format.
## Push API Request Flow
Required parameters
| Name   |     Format      |  Description |
|----------|:-------------:|------:|
| API Acess token |  Authorization: Bearer <token> | API Token generated from the Issuer Profile 'API Tokens' page |

### Get Document Required Fields
```bash
  GET https://mylocker.stage.mygov.bd/api/issuers/fields/{document_id}
```
```json
{
    "message": "Issuer Documents upload all fields.",
    "data": {
        "citizen_info": {
            "citizen_id": "required",
            "nid": "required"
        },
        "issuer_info": {
            "name": "required",
            "office_id": "required",
            "ministry_name": "required",
            "email": "required|email"
        },
        "document_type": "required",
        "document_id": "required",
        "document_category": "required|personal|business",
        "file": "required|mime:png,jpg,pdf",
        "payload": {
            "institution_name": "nullable",
            "business_type": "nullable",
            "name": "required"
        }
    }
}
```

### Create Single Document
```bash
  POST https://mylocker.stage.mygov.bd/api/issuers/import
  //request body
  {
    "citizen_info": {
        "citizen_id": "317321731",
        "nid": "391231391932"
    },
    "issuer_info": {
        "name": "NID",
        "office_id": "NID_31318",
        "ministry_name": "NID",
        "email": "nid@mygov.com"
    },
    "document_type": "DBID",
    "document_id": "050340e3-c15a-49e9-bbcb-fd275a8cd5be",
    "document_category": "personal",
    "file": "", //multipart/form-data
    "payload": {
        "institution_name": "Xysx",
        "business_type": "xyz",
        "name": "test"
    }
}
```
