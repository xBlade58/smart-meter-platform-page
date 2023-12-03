# Data Transmission Format

The Data Transmission Format was inspired by a project from the Swedish Defence Materiel Administration.

The specification comprises a SysML Block that represents the template and an associated Parametric Diagram that defines the templates and Platform specific objects instantiated by the MeterReading template.

http://www.plcs.org/plcslib/plcslib/data/contexts/SwedishDefence/templates/MeterReading/template.html

Diagram
http://www.plcs.org/plcslib/plcslib/data/contexts/SwedishDefence/dexs/OperationalData/dex_business_information_model.html#Model_Diagrams


We would introduce the following yaml based structure.

<details>
<summary>Profile structure yaml</summary>

```yaml
MeterReading:
    type: object
    properties:
        meterReadingIdentifier:
        type: string
        format: uuid
        readingTime:
        type: string
        format: datetime
        sequenceNumber:
        type: number
        faultCode:
        type: string
        format: faultCode
        propertyValues:
        type: array
        items:
            # PropertyValues
            type: object
            properties:
            unit:
                type: string
            date:
                type: string
                format: datetime
            nummericalValue:
                type: number
            textValue:
                type: string
            operationalPropertyDefinition:
                type: object
                properties:
                propertyId:
                    type: string
                    format: uuid
                propertyName:
                    type: string
                allowedUnits:
                    type: array
                    items:
                        type: string
        meterIndividual:
            type: object
            properties:
                meterIndividualId:
                    type: string
                    format: uuid
                physicalMeterType:
                    type: object
                    properties:
                        physicalElementId:
                        type: string
                        format: uuid
                        physicalElementName:
                        type: string
                        physicalElementVersionId:
                        type: string
                        physicalElementIsVirtual:
                        type: boolean
                        physicalMeterCategory:
                        type: string
                        enum:
                            - ELECTRICITY
                            - GAS
                            - WATER
                            - HEAT
```

</details>

With this structure the following json can be created for the different profiles e.g. a electrical smart meter:

<details>
<summary>Profile of a Electrical Smart Meter</summary>

```json
{
"meterReadingIdentifier": "a1b2c3d4-e5f6-g7h8-i9j0-k1l2m3n4o5p6",
"readingTime": "2023-11-22T12:00:00Z",
"sequenceNumber": 1,
"faultCode": "FC456",
"propertyValues": [
    {
    "unit": "kWh",
    "date": "2023-11-22T12:00:00Z",
    "numericalValue": 100.5,
    "operationalPropertyDefinition": {
        "propertyId": "123e4567-e89b-12d3-a456-426614174001",
        "propertyName": "Energy",
        "allowedUnits": ["kWh"]
    }
    },
    {
    "unit": "V",
    "date": "2023-11-22T12:00:00Z",
    "numericalValue": 230.0,
    "operationalPropertyDefinition": {
        "propertyId": "123e4567-e89b-12d3-a456-426614174002",
        "propertyName": "Voltage L1",
        "allowedUnits": ["V"]
    }
    },
    {
    "unit": "V",
    "date": "2023-11-22T12:00:00Z",
    "numericalValue": 235.0,
    "operationalPropertyDefinition": {
        "propertyId": "123e4567-e89b-12d3-a456-426614174003",
        "propertyName": "Voltage L2",
        "allowedUnits": ["V"]
    }
    },
    {
    "unit": "V",
    "date": "2023-11-22T12:00:00Z",
    "numericalValue": 240.0,
    "operationalPropertyDefinition": {
        "propertyId": "123e4567-e89b-12d3-a456-426614174004",
        "propertyName": "Voltage L3",
        "allowedUnits": ["V"]
    }
    },
    {
    "unit": "A",
    "date": "2023-11-22T12:00:00Z",
    "numericalValue": 30.0,
    "operationalPropertyDefinition": {
        "propertyId": "123e4567-e89b-12d3-a456-426614174005",
        "propertyName": "Current L1",
        "allowedUnits": ["A"]
    }
    },
    {
    "unit": "A",
    "date": "2023-11-22T12:00:00Z",
    "numericalValue": 28.0,
    "operationalPropertyDefinition": {
        "propertyId": "123e4567-e89b-12d3-a456-426614174006",
        "propertyName": "Current L2",
        "allowedUnits": ["A"]
    }
    },
    {
    "unit": "A",
    "date": "2023-11-22T12:00:00Z",
    "numericalValue": 32.0,
    "operationalPropertyDefinition": {
        "propertyId": "123e4567-e89b-12d3-a456-426614174007",
        "propertyName": "Current L3",
        "allowedUnits": ["A"]
    }
    }
],

"meterIndividual": {
    "meterIndividualId": "123e4567-e89b-12d3-a456-426614174abcd",
    "physicalMeterType": {
        "physicalElementId": "123e4567-e89b-12d3-a456-426614174008",
        "physicalElementName": "Electrical Smart Meter - 3 Phases",
        "physicalElementVersionId": "abcdef12-3456-7890-abcd-ef1234567890",
        "physicalElementIsVirtual": false,
        "physicalMeterCategory": "ELECTRICITY"
    }
}
```
</details>

When there is a change in the requirements or e.g. suddenly a water smart meter should be integrated, it will be possible with the yaml to create a compliant profile that could look like the following:

<details>
<summary>Profile of a Water Smart Meter</summary>

```json
{
"meterReadingIdentifier": "b1c2d3e4-f5g6-h7i8-j9k0-l1m2n3o4p5q6",
"readingTime": "2023-11-22T09:30:00Z",
"sequenceNumber": 1,
"faultCode": "FC789",
"propertyValues": [
    {
    "unit": "m³",
    "date": "2023-11-22T09:30:00Z",
    "numericalValue": 5.8,
    "operationalPropertyDefinition": {
        "propertyId": "123e4567-e89b-12d3-a456-426614174009",
        "propertyName": "Water Consumption",
        "allowedUnits": ["m³"]
    }
    },
    {
    "unit": "°C",
    "date": "2023-11-22T09:30:00Z",
    "numericalValue": 15,
    "operationalPropertyDefinition": {
        "propertyId": "123e4567-e89b-12d3-a456-426614174010",
        "propertyName": "Water Temperature",
        "allowedUnits": ["°C"]
    }
    }
],
"meterIndividual": {
    "meterIndividualId": "123e4567-e89b-12d3-a456-426614174abcc",
    "physicalMeter": {
        "physicalElementId": "123e4567-e89b-12d3-a456-426614174011",
        "physicalElementName": "Water Consumption Meter - Household",
        "physicalElementVersionId": "abcdef12-3456-7890-abcd-ef1234567891",
        "physicalElementIsVirtual": false,
        "physicalMeterCategory": "WATER"
    }
}
}
```
</details>


