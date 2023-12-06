# SmartMeterAdapter

## Overview

The SmartMeterAdapter acts as a bridge between the SmartMeter provided by the energy provider and the Concentrator. It establishes a connection to the SmartMeter, collects essential energy-related data, and transfers this data to the Concentrator for further processing and analysis. The connection method to the SmartMeter is specified by the SmartMeter itself, ensuring compatibility and seamless data retrieval.

## What is the Component About

The SmartMeterAdapter component is responsible for:

- Establishing a connection to the SmartMeter, utilizing the specified connection method.
- Collecting real-time energy data, including current power consumption and injection, as well as total consumption and injection.
- Transmitting the collected data to the Concentrator for further processing.

## Information Flow

Data is collected from the SmartMeter through the M-Bus interface, ensuring a reliable and standardized method of communication.

## Features

- continuously reads energy attributes from a Smart Meter
- long-term storage needed or temporary enough?

### Privacy Concerns

- **Data Minimization:** The SmartMeterAdapter only collects essential energy-related data, minimizing the amount of sensitive information stored.
- **Secure Communication:** Utilizes secure communication protocols to ensure data integrity and confidentiality during transmission.

### Security Concerns

- **Key Confidentiality:** The Smart Meter provides a key for the M-Bus interface, which is essential for the SmartMeterAdapter's communication. This key must be stored confidentially and securely to prevent unauthorized access or tampering.
- **Data Integrity:** Implements measures to verify the integrity of the received data, ensuring that the information collected from the SmartMeter is accurate and reliable.
