# Open Meter Data Platform Overview

The **Open Meter Data Platform** is a solution designed to standardize a platform to collect smart meter data. This data can be used to optimize energy consumption and enhance efficiency in residential and commercial settings. Leveraging advanced technologies, this system offers real-time monitoring, data analysis, and visualization capabilities. Here's an overview of the key components and their interconnections:

## Brainstorming

![a picture of the brainstorming platform diagram](images/brainstorming_platform_components.jpeg "brainstorming_platform_components")

## Architecture

There are different approaches to structure the architecture of such a _Open Meter Data Platform_ This part of the document should provide different approaches to structure the application. The most split up option which we call _Completely Divided Architecture_ is provided on this page. Every component, better described in this document is visualized in the following figure.

![Completely Divided Architecture](images/full.png "Completely Divided Architecture")

To get a better understanding of the options and modifications that could be usefull this subsection about [architectural options](ArchitecturalOptions.md) was created.


## Components

### [SmartMeter](SmartMeter.md)
The **SmartMeter**, installed by the energy provider, is the foundation of the system. It measures real-time energy consumption and injection, providing accurate data for billing and analysis.

### [IoT Device](IoT.md) 
The **IoT Device** acts as an intermediary between the SmartMeter and the IoT Edge component. It collects energy data using the M-Bus interface and securely transfers it to the IoT Edge device.

### [IoT Edge](IoTEdge.md) 
The **IoT Edge** component processes data collected from multiple SmartMeters and external devices locally. It offers flexibility through extension modules such as Data Sharing, Local Data Analytics, and Event Modules. The IoT Edge connects to the central cloud system to provide the collected data.

### [Cloud](Cloud.md) 
The **Cloud** component serves as the centralized hub for the entire system. It handles vast amounts of data, provides APIs for querying and data provision, and ensures secure communication with other components.

### [Visualizing Application ](App.md)
The **Visualizing Application** offers an intuitive user interface for end-users. It connects to both the IoT Edge device and the Cloud, enabling users to monitor real-time energy data, access historical usage patterns, and receive alerts.

## System Flow

1. **SmartMeters** measure real-time energy consumption and injection in individual households or apartments.
2. **IoT Devices** collect energy data from SmartMeters via the M-Bus interface and transmit it securely to the IoT Edge component.
3. **IoT Edge** processes the received data, performs local analytics, and sends the processed information to the central **Cloud** system for further analysis and storage.
4. The **Visualizing Application (App)** connects to the IoT Edge device to access real-time data and the central **Cloud** system for historical usage patterns and visualizations.
5. Users interact with the **Visualizing Application** to monitor energy consumption, analyze trends, and receive alerts.

For detailed specifications on each component, please refer to the respective pages linked above.
