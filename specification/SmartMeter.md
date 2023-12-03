# SmartMeter Component Specification

## Overview

The SmartMeter serves as the central controller component for communication technology in energy management systems. It is provided and installed by the energy provider, typically assigned to individual households and apartments. Smart Meters are essential for measuring and managing energy consumption efficiently.

## What is the Component About

The SmartMeter, installed by the energy provider, is designed to:

- Measure and monitor energy consumption and injection in households and apartments.
- Ensure precise calculation of energy usage needed for billing.
- Support communication with external devices through standardized interfaces, such as the M-Bus.

## Input Parameters

Smart Meters measure a variety of parameters related to energy consumption, including:

- **Current Power Consumption:** Instantaneous power consumption in watts.
- **Current Power Injection:** Instantaneous power injection in watts.

> [!NOTE]
> Smart Meters may measure additional parameters based on specific configurations and requirements.

## Output Parameters

The [M-Bus](https://m-bus.com/) interface is a standardized communication protocol used by Smart Meters to transmit data about energy consumptions of households. Examples of output parameters include:

- **Current Power Consumption:** Instantaneous power consumption in watts.
- **Current Power Injection:** Instantaneous power injection in watts.
- **Current Total Consumption:** Total active energy consumption in watt-hours.
- **Current Total Injection:** Total active energy injection in watt-hours.

Additional Parameters

- **Instantaneous Current (I) in Phase L1:** Current in phase L1 in amperes.
- **Instantaneous Voltage (U) in Phase L1:** Voltage in phase L1 in volts.
- **Instantaneous Current (I) in Phase L2:** Current in phase L2 in amperes.
- **Instantaneous Voltage (U) in Phase L2:** Voltage in phase L2 in volts.
- **Instantaneous Current (I) in Phase L3:** Current in phase L3 in amperes.
- **Instantaneous Voltage (U) in Phase L3:** Voltage in phase L3 in volts.


Other forms of output
- P1
- IR

## Information Flow

The SmartMeter communicates data through standardized interfaces. The specific information flow details, including the format of data transmission and frequency, should be defined in the technical documentation and varies between protocols and communication methods.

## Features

### Privacy Concerns

- **Data Confidentiality:** Smart Meters should ensure that individual energy usage data is confidential and accessible only to authorized parties, typically the occupants and the energy provider.
- **Anonymization:** Implement techniques to anonymize personal data, ensuring privacy while still providing accurate usage information.

### Security Concerns

- **Secure Connection:** The connection between the Smart Meter and peripheral devices, such as IoT Devices, should be secured in accordance with relevant laws and regulations.
- **M-Bus Interface Key:** The Smart Meter defines a unique key for the M-Bus interface, which is provided to authorized peripheral devices. This key must be stored securely to prevent unauthorized access or tampering.
- 
