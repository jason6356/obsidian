
We can skip through the process of issuing credential

```json

{
  "auto_issue": true,
  "auto_remove": true,
  "comment": "string",
  "connection_id": "95a802fc-3323-44b4-801c-4ad0b4baae20",
  "credential_preview": {
    "@type": "issue-credential/2.0/credential-preview",
    "attributes": [
      {
        "name": "merit",
        "value": "bad"
      },
      {
        "name": "cgpa",
        "value": "4"
      },
      {
        "name": "course name",
        "value": "skipped the proposal"
      }
    ]
  },
  "filter": {
    "indy": {
      "cred_def_id": "NypRCRGykSwKUuRBQx2b9o:3:CL:44:diploma",
      "issuer_did": "NypRCRGykSwKUuRBQx2b9o",
      "schema_id": "NypRCRGykSwKUuRBQx2b9o:2:diploma:1.0",
      "schema_issuer_did": "NypRCRGykSwKUuRBQx2b9o",
      "schema_name": "diploma",
      "schema_version": "1.0"
    }
  },
  "trace": true
}
```

