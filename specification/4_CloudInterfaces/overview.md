# Cloud

In this chapter the minimal required interfaces of the Cloud component are described. Especially which interfaces MUST be available and which of them are just RECOMMENDED is described in this chapter of the specification.

Data is stored inside the cloud system like described in [2_DataModel](./../2_DataModel/overview.md). The interfaces MUST consist of a ingress component and a interface to query data.

## Ingress

Data for the cloud component MUST be provided through the ingress interface.

The Cloud ingress is a Publish Subscribe interface subscribing to a topic. More details on that can be found in the chapter [3_Communication](./../3_Communication/overview.md).

Data received on this ingress channel is stored in a internal storage component of the cloud component. Data is structured as described in [2_DataModel](./../2_DataModel/overview.md). Incoming data is also structured as described in [2_DataModel](./../2_DataModel/overview.md).

## Data Query Interface

The meter data can be queried by providing different options as json encoded http post request body. A list of options and the parameters is given in the following section.

There MUST be the option to return the result of the query as a response in a json object structure or as a url to a bulk download. The application SHOULD define own limits for the json response and return a bulk download instead. There MUST be an option to select the preferred download method. Bulk download should be possible with every request and json response MAY be the default option.

Querying the MeterReadings can be done by sending a post request with the following request body to the endpoint `[HOSTNAME]/[OPTIONAL_PATH]/v1/meterReadings`. 

```
 content:
  application/json:
    schema:
      type: object
      properties:
        readingTimeStart:
          type: string
          format: date-time
          description: Start of the meter reading time range.
          required: false
        readingTimeEnd:
          type: string
          format: date-time
          description: End of the meter reading time range.
          required: false
        maxRows:
          type: integer
          description: Maximum number of rows to return in whole request.
          required: false
        pageNumber:
          type: integer
          description: Page number for pagination.
          required: false
        pageSize:
          type: integer
          description: Number of rows per page.
          required: false
        operationalProperties:
          type: array
          required: false
          items:
            specificOperationalProperty:
              type: object
              properties:
                specificPropertyName:
                  type: string
                  required: false
                  description: Specific operational property to filter.
                numericalValueGreaterThan:
                  type: number
                  required: false
                  description: Filter by numerical value greater than a specified amount.
                numericalValueLessThan:
                  type: number
                  required: false
                  description: Filter by numerical value smaller than a specified amount.
                numericalValueEqualTo:
                  type: number
                  required: false
                  description: Filter by numerical value equal to a specified amount.
                textValueEqualTo:
                  type: string
                  required: false
                  description: Filter by textual value equal to a specified amount.
```

As a response you will receive:

```
type: object
properties:
  linkToBulk:
    type: string
    required: false
  page:
    type: number
    required: false
  content:
    required: false
    type: array
    items:
        type: object
        properties:
          readingTime:
            type: string
            format: date-time
            description: Timestamp for reading time.
          meterId:
            type: string
            format: uuid
            description: Identifier for the meter.
          propertyValues:
            type: array
            items:
              type: object
              properties:
                propertyName:
                  type: string
                  description: Name of the property.
                numericalValue:
                  type: number
                  description: Numerical value for the property.
                  required: false
                textValue:
                  type: string
                  description: Textual value for the property.
                  required: false
                unit:
                  type: string
                  description: Unit of measurement for the property.
```

## Securing the Endpoint

For the security of the endpoint from confidentiality perspective, it is the RECOMMENDED option to use a token based access solution like OAuth2 OIDC.

## Data Protection

The data query interface SHOULD not return less than 20 data rows. If less than 20 rows are in the result the request SHOULD be denied. The system MUST follow data minimization principles, collecting only essential customer data defined for specific purposes.

## Cleaning Data

As a logged-in user with rights to delete data entries, a user MUST have the ability to delete collected MeterReadings.

The deletion interface is a http delete endpoint with the id of the MeterReading to delete as a parameter.

`DELETE [HOSTNAME]/[OPTIONAL_PATH]/v1/meterReadings?id={MeterReadingId}`
  
