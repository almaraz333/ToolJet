---
sidebar_position: 1
---

# Airtable


ToolJet can connect to your Airtable account to read and write data. **Airtable API key** is required to create an Airtable data source on ToolJet. You can generate API key by visiting [Airtable account page](https://airtable.com/account). 

<div style={{textAlign: 'center'}}>

![ToolJet - Data source - Airtable](/img/datasource-reference/airtable/airtableds.gif)

</div>

:::info
Airtable API has a rate limit, and at the time of writing this documentation, the limit is five(5) requests per second per base. You can read more about rate limits here **[Airtable API]( https://airtable.com/api )**.
:::

:::tip
This guide assumes that you have already gone through [Adding a data source](/docs/tutorial/adding-a-datasource) tutorial.
:::

## Supported queries

- **[Listing records](#listing-records)**
- **[Retrieving a record](#retrieving-a-record)**
- **[Creating a record](#creating-a-record)**
- **[Updating a record](#updating-a-record)**
- **[Deleting a record](#deleting-a-record)**

### Listing records

This query lists all the records in a table. The results are paginated and each page can have upto 100 records. 

#### Required parameters: 

- **Base ID:** To find the Base ID, first visit **airtable.com/api**. Select from the list of bases the base whose ID you'd like to find out. Example Base ID: `appDT3UCPffPiSmFd`
- **Table name:** Enter the table name whose data you want to fetch.

#### Optional parameters: 

- **Page size:** The number of records returned in each request. Must be less than or equal to 100. Default is 100.
- **offset:** If there are more records, the response will contain an offset. To fetch the next page of records, include offset in the next request's parameters.

<div style={{textAlign: 'center'}}>

![ToolJet - Data source - Airtable](/img/datasource-reference/airtable/airtable_list.png)

</div>

Example response from Airtable: 

```json
{
    "records": [
        {
            "id": "recu9xMnUdr2n2cw8",
            "fields": {
                "Notes": "sdfdsf",
                "Name": "dsfdsf"
            },
            "createdTime": "2021-05-12T14:30:33.000Z"
        },
        {
            "id": "recyIdR7bVdQvmKXa",
            "fields": {
                "Notes": "sdfdsf",
                "Name": "dfds"
            },
            "createdTime": "2021-05-12T14:30:33.000Z"
        },
        {
            "id": "recAOzdIHaRpvRaGE",
            "fields": {
                "Notes": "sdfsdfsd",
                "Name": "sdfdsf"
            },
            "createdTime": "2021-05-12T14:30:33.000Z"
        }
    ],
    "offset": "recAOzdIHaRpvRaGE"
}
```

### Retrieving a record

#### Required parameters: 

- **Base ID**
- **Table name** 
- **Record ID**

<div style={{textAlign: 'center'}}>

![ToolJet - Data source - Airtable](/img/datasource-reference/airtable/airtable_retrieve.png)

</div>

Example response from Airtable: 

```json
{
    "id": "recu9xMnUdr2n2cw8",
    "fields": {
        "Notes": "sdfdsf",
        "Name": "dsfdsf"
    },
    "createdTime": "2021-05-12T14:30:33.000Z"
}
```

### Creating a record

#### Required parameters:
- **Base ID**
- **Table name**
- **Records**

<div style={{textAlign: 'center'}}>

![ToolJet - Data source - Airtable](/img/datasource-reference/airtable/airtable_create.png)

</div>

#### Example Records:

```json
[
    {
        "fields": {
            "Notes": "sdfdsf",
            "Name": "dsfdsf"
        }
    },
    {
        "fields": {
            "Notes": "note1",
            "Name": "dsfdsf"
        }
    }
]
 

```


Click on the `run` button to run the query.

:::info
NOTE: Query must be saved before running.
:::

Example response from Airtable:
```json
{
    "records": [
        {
            "id": "rec5RuZ1COoZGtGDY",
            "fields": {
                "Notes": "sdfdsf",
                "Name": "dsfdsf"
            },
            "createdTime": "2022-02-07T20:25:27.000Z"
        },
        {
            "id": "recaYbFPonNNu6Cwj",
            "fields": {
                "Notes": "note1",
                "Name": "dsfdsf"
            },
            "createdTime": "2022-02-07T20:25:27.000Z"
        }
    ]
}
```

### Updating a record

#### Required parameters:
- **Base ID**
- **Table name**
- **Record ID**

<div style={{textAlign: 'center'}}>

![ToolJet - Data source - Airtable](/img/datasource-reference/airtable/airtable_update.png)

</div>

#### Example body:

<div style={{textAlign: 'center'}}>

![ToolJet - Data source - Airtable](/img/datasource-reference/airtable/airtable-update-example-body.png)

</div>

Click on the `run` button to run the query.

:::info
NOTE: Query must be saved before running.
:::

Example response from Airtable:
```json
{
    "id": "recu9xMnUdr2n2cw8",
    "fields": {
        "Notes": "Example Notes",
        "Name": "change"
    },
    "createdTime": "2021-08-08T17:27:17.000Z"
}
```

### Deleting a record

#### Required parameters:
- **Base ID**
- **Table name**
- **Record ID**

<div style={{textAlign: 'center'}}>

![ToolJet - Data source - Airtable](/img/datasource-reference/airtable/airtable_delete.png)

</div>


Click on the `run` button to run the query.

:::info
NOTE: Query must be saved before running.
:::

Example response from Airtable:

```json
{
    deleted: true
    id: "recIKsyZgqI4zoqS7"
}
```