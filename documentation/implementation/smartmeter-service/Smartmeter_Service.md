# Smartmeter Service

The `Smartmeter microservice` is one of the essential parts of the Cloud architecture as it is responsible for data about Smart Meter and Meter Readings.

## Core functionality

The core functionality of this service revolves around the following aspects:

- Reliably storing smart meters and meter readings
- Requesting meter readings of a household for a given time interval

## Domain Model

![domain_model](../images/Domain_Model.png)

For modelling the domain, we adhered to the data model as proposed by the specification. One crucial relation is depicted by the `MeterReading` containing multiple `PropertyValues`. Every PropertyValue is defined by a _OperationalPropertyDef_. An example for an identifier of such a property definition would be `52.7.0`, which holds the **Instantaneous voltage in phase L2**.

## Hexagonal Architecture

Our goal was to build the Smartmeter service in a way that enables different external components to interact with our business logic, while keeping the business logic isolated from any external dependencies. So, the decision fell to a `Hexagonal Architecture`, also commonly known as `Ports and Adapters` pattern.

Consequently, we divided the implementation of the Smartmeter service into two parts. The first part is the _application (inner hexagon)_ that handles the business logic through the domain model and ports. The second part is represented by the _adapters (outer hexagon)_ that use the ports to interact with the business logic.

![smartmeter_service_architecture](../images/Smartmeter_Service_Architecture.png)

### Application (inner hexagon)


### Adapter (outer hexagon)
