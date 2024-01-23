# Concentrator

The Concentrator component acts as an intermediary between individual SmartMeterAdapter attached to SmartMeters and the optional central cloud system. Its primary function is to transmit relevant information to the cloud and concentrate multiple SmartMeterAdapters if configured.

## What is the Component About

The Concentrator component is the element between the SmartMeterAdapters and the Cloud. It can be configured to act as a Concentrator for multiple SmartMeterAdapters.

### Data Collection

The Concentrator connects to one or more SmartMeterAdapter components. How this connection is established is defined in the section [3_Communication](./../3_Communication/README.md). SmartMeterAdapter components are from the top level view of the concentrator in close proximity to the Concentrator.

### Provide Data to the Cloud

Data is not modified and provided to the Cloud as received from the SmartMeterAdapter component. Communication is established as described in the [3_Communication](./../3_Communication/README.md) section.

> [!NOTE]
> In some cases this functionality will be implemented on the same hardware device as the SmartMeterAdapter. In this specific case, this Concentrator will only connect to one SmartMeterAdapter.
