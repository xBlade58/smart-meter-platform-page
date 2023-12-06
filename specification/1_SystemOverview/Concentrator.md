# Concentrator

The Concentrator component acts as an intermediary between individual SmartMeterAdapter attached to smart meters and the optional central cloud system. Its primary function is to transmit relevant information to the cloud. 

## What is the Component About

The Concentrator component serves the following purposes:

- **Data Collection:** Gathers data from multiple smart meters in close proximity to the hardware smart meter.
- **Cloud Integration:** Transmits collected data and metadata to the central cloud system.


## Privacy Concerns

- **Data Segregation:** Ensures data from smart meters is accessible only to the specific household owner, enhancing privacy.
- **Local Processing:** Utilizes local data analytics and processing, reducing the need to transmit sensitive data to external systems.
- **Data Minimization:** Minimizes the data sent to the cloud, reducing the risk of privacy breaches:
  - User defines a custom intervall to merge and send the data (e.g. 1hr means the data collected within one hour is merged and sent to the cloud).
  - User defines the data that is sent.

## Security Concerns

- **Multi-Smart Meter Support:** Supports multiple smart meters on a single edge device, optimizing resource utilization and scalability.
- **Secure Connections:** Utilizes secure communication protocols to protect connections between SmartMeterAdapter and the edge component.
- **Authentication and Authorization:** Implements robust authentication and authorization mechanisms to ensure only authorized devices can interact with the edge component.
