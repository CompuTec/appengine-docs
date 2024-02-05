# Custom Views

## What is CompuTec AppEngine Custom View?

CompuTc AppEngine provides a mechanism for encapsulating complex database queries as simple structures.

### Features

- simplified data consumption in Web API client or UI

- supports OData V4

- supports SAP HANA and Microsoft SQL Server

- supports CompuTec AppEngine Plugins

- The CustomViews folder is available in the AE installation directory, and ProgramData/CompuTec/AppEngine.

![Custom View](./media/custom-views/core-odata.webp)

:::note
Note that the Custom View ID will be extended with the plugin ID during plugin initialization
`<plugin identifier>:<view identifier>`
:::

## Custom View Definition from Plugin Dir

`<file name>.customview.json`

```json
{
  "Id": "<view identifier>",
  "Description": "<view description>",
  "Source": {
    "Hana": "<SAP Hana query>",
    "MsSql": "<MsSQL query>"
  }
}
```

## Request

Request URL

```json
http://{ae_url}/odata/CustomViews/Views.Custom(Id='<plugin identifier>:<view identifier>')

```

## Example

### View definition

File: BusinessPartnerPaymentTerms.customview.json

```json
{
  "Id": "BusinessPartnerPaymentTerms",
  "Description": "Business Partners and their assigned payment terms",
  "Source": {
    "Hana": "
        SELECT
            \"OCTG\".\"PymntGroup\", \"OCRD\".\"CardCode\", \"OCRD\".\"CardName\"
        FROM OCRD
        LEFT OUTER JOIN OCTG ON \"OCRD\".\"GroupNum\" = \"OCTG\".\"GroupNum\"
        ",
     "MsSql": "
        SELECT
            \"OCTG\".\"PymntGroup\", \"OCRD\".\"CardCode\", \"OCRD\".\"CardName\"
        FROM OCRD
        LEFT OUTER JOIN OCTG ON \"OCRD\".\"GroupNum\" = \"OCTG\".\"GroupNum\"
        "
  }
}
```

### Request

Curl

```json
curl -X GET --header 'Accept: application/json' 'http://localhost:54000/odata/CustomViews/Views.Custom(Id='MYPLUGIN:BusinessPartnerPaymentTerms')'
```

Request URL

```json
http://localhost:54000/odata/CustomViews/Views.Custom(Id='MYPLUGIN:BusinessPartnerPaymentTerms')
```

Response Body

```json
{
  "@odata.context": "http://localhost:54000/odata/$metadata#Custom",
  "value": [
    {
      "No": 1,
      "PymntGroup": "- Cash Basic -",
      "CardCode": "00001",
      "CardName": "ABC Inc"
    },
    {
      "No": 2,
      "PymntGroup": "- Cash Basic -",
      "CardCode": "00002",
      "CardName": "Hanks Deliveries"
    },
    {
      "No": 3,
      "PymntGroup": "- Cash Basic -",
      "CardCode": "TEST",
      "CardName": ""
    }
  ]
}
```

## Example with parameters

### View definition

File: request.customview.json

```json
{
  "Id": "RequestView",
  "Description": "Fetch request from database",
  "Source": {
    "Hana": "SELECT * FROM CTLABEL.CT_LP_REQUESTDETAILS WHERE \"REQUESTID\" = @RequestId",
    "MsSql": "SELECT * FROM CTLABEL.dbo.CT_LP_REQUESTDETAILS WHERE REQUESTID = @RequestId"
  }
}
```

### Request

Curl

```json
curl -X GET --header 'Accept: application/json' 'http://localhost:54000/odata/CustomViews/Views.CustomWithParameters(Id='CTLabel%3ARequestView',Parameters=[%22RequestId%3D61%22],paramType=Default.ParamType'Custom')'
```

Request URL

```json
http://localhost:54000/odata/CustomViews/Views.CustomWithParameters(Id='CTLabel%3ARequestView',Parameters=[%22RequestId%3D61%22],paramType=Default.ParamType'Custom')
```

Response Body

```json
{
  "@odata.context": "http://localhost:54000/odata/$metadata#Custom",
  "value": [{}]
}
```
