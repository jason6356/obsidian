## Based on the Analysis on how senior's work

The previous batch create a folder which called `model` to store all the payload templates
when performing API calls for the ACA-PY

For example like Create Definition

```json
    bodyPayloadTemplate: any = {
        "schema_id": "",
        "support_revocation": "",
        "revocation_registry_size": "",
        "tag": ""
    }
```

this is the JSON object the API is expected

However this is how their work when adding these attributes into the JSON Body

```ts
export class NewDefinitions {
  constructor() {}

  updateBodyPayLoadTemplate(
    schemaID,
    supportRevocation,
    revocationRegistrySize,
    tag
  ) {
    this.bodyPayloadTemplate.schema_id = schemaID;
    this.bodyPayloadTemplate.support_revocation = supportRevocation === "true";
    this.bodyPayloadTemplate.revocation_registry_size = parseInt(
      revocationRegistrySize
    );
    this.bodyPayloadTemplate.tag = tag;
    return this;
  }

  bodyPayloadTemplate: any = {
    schema_id: "",
    support_revocation: "",
    revocation_registry_size: "",
    tag: "",
  };
}
```

## Result 

![[Pasted image 20230808132534.png]]

These are the codes they wrote for the payload parsing to satisfy the API Requirements