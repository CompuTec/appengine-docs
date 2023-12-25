# Simple Views

## What is CompuTec AppEngine Simple View?

Odata v4-based tool providing a unified data consumption method (directly from the database).

### Features

- simplified data consumption in Web API client or UI

- supports OData V4

- supports SAP HANA and Microsoft SQL Server.

![Custom Views](./media/simple-views/custom-views.png)

### Request

Request URL

```json
http://{ae_url}/odata/CustomViews/Views.Custom(Id='<plugin identifier>:<view identifier>')
```

## Example

### Request

Curl

```json
curl -X GET --header 'Accept: application/json' 'http://localhost:54000/odata/CustomViews/Views.Simple(DataSource='OITM')?$select=ItemCode%2C%20ItemName%2C%20OnHand&$top=1'
```

Request URL

```json
http://localhost:54000/odata/CustomViews/Views.Simple(DataSource='OITM')?$select=ItemCode%2C%20ItemName%2C%20OnHand&$top=1
```

Response body

```json
{ "@odata.context": "http://localhost:54000/odata/$metadata#Simple", "value": [ { "No": 1, "ItemCode": "Active-Item-03", "ItemName": "Active-Item-03", "OnHand": 950 } ] }
```