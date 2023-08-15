
## Idea

Connection contains metadata to store any information we want on the connection.

The Best Idea for the implementation is we use the 

![[Pasted image 20230813031059.png]]

## API Endpoint

> /connections/{conn_id}/metadata 

### Get Method

-> Retrieve the Connection Image Icon by performing the query of image_url key

### Post Method

-> Update the Metadata by sending a payload in this format

```json
{
	"metadata": {}
}
```

This ensures what we have to put this into the connection

#### Further Implementation

