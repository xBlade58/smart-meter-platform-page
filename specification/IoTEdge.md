# IoT Edge Component Specification

The IoT Edge component acts as an intermediary between individual IoT devices attached to smart meters and the optional central cloud system. Its primary function is to transmit relevant information to the cloud. Additionally, it could operate in a detached scenario, ensuring local accessability and processing of data.

## What is the Component About

The IoT Edge component serves the following purposes:

- **Data Collection:** Gathers data from multiple smart meters in close proximity to the hardware smart meter.
- **Cloud Integration:** Transmits collected data and metadata to the central cloud system.
- **Enhancements:**
  - **Data Sharing Module:** Allows local storage of data and provides access through APIs to applications. Can function independently, minimizing reliance on the cloud.
  - **Local Data Analytics Module:** Performs data analytics tasks locally on the device, accessible through APIs.
  - **Event Module:** Generates events related to energy consumption, enabling home automation software integration for custom automations.

## Input Parameters

- Data from multiple smart meters:
  - TBD
- Data from external devices such as photovoltaic panels:
  - TBD
- Configuration data from external applications:
  - Login Data
  - Intervall
  - Definition of data sent to the cloud

## Output Parameters

- **To Cloud:**
  - **Meta Data per Smart Meter:**
    - Household information (Type, number of occupantes)
    - Smart Meter ID
    - Timestamp
    - Intervall
  - **Current Data from Smart Meters:**
    - Current Power Consumption
    - Current Power Injection
    - Current Total Consumption
    - Current Total Injection
- **Through APIs to Application Devices:**
  - Provides data and analytics results to application devices via APIs for further processing and visualization.

## Information Flow

- **Data Collection:**
  - Collects data from SmartMeter-IoT devices.
  - Gathers data from devices within the household.
  - Retrieves data from external APIs, e.g. weather data.
- **Data Transmission:**
  - Sends collected data to the central cloud system.
  - Provides data to visualization applications via APIs for real-time monitoring and analysis.

## Features

### Privacy Concerns

- **Data Segregation:** Ensures data from smart meters is accessible only to the specific household owner, enhancing privacy.
- **Local Processing:** Utilizes local data analytics and processing, reducing the need to transmit sensitive data to external systems.
- **Data Minimization:** Minimizes the data sent to the cloud, reducing the risk of privacy breaches:
  - User defines a custom intervall to merge and send the data (e.g. 1hr means the data collected within one hour is merged and sent to the cloud).
  - User defines the data that is sent.

### Security Concerns

- **Multi-Smart Meter Support:** Supports multiple smart meters on a single edge device, optimizing resource utilization and scalability.
- **Secure Connections:** Utilizes secure communication protocols to protect connections between IoT devices and the edge component.
- **Authentication and Authorization:** Implements robust authentication and authorization mechanisms to ensure only authorized devices can interact with the edge component.

### Detached Scenario

In a detached scenario without a central cloud, the system operates locally, ensuring:

- **Local Functionality:** All functionalities, including data collection, processing, and event generation, work seamlessly within the local environment.
- **Enhanced Data Privacy:** Data remains localized, enhancing privacy as it is not shared among multiple users or external systems.
