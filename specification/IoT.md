# IoT Device Component Specification

## Overview

The IoT Device component acts as a bridge between the SmartMeter provided by the energy provider and the IoT Edge device. It establishes a connection to the SmartMeter, collects essential energy-related data, and transfers this data to the IoT Edge device for further processing and analysis. The connection method to the SmartMeter is specified by the SmartMeter itself, ensuring compatibility and seamless data retrieval.

## What is the Component About

The IoT Device component is responsible for:
- Establishing a connection to the SmartMeter, utilizing the specified connection method.
- Collecting real-time energy data, including current power consumption and injection, as well as total consumption and injection.
- Transmitting the collected data to the IoT Edge device for further processing.

## Input Parameters

- **Current Power Consumption:** Instantaneous power consumption in watts (*Aktueller Stromverbrauch*).
- **Current Power Injection:** Instantaneous power injection in watts.
- **Current Total Consumption:** Total active energy consumption in watt-hours.
- **Current Total Injection:** Total active energy injection in watt-hours.

(*Note: The specified parameters are universally available across all SmartMeter types.*)

## Output Parameters

- **Positive Active Instantaneous Power (A+):**
- **Positive Active Energy (A+) Total:**
- **Negative Active Instantaneous Power (A-):**
- **Negative Active Energy (A-) Total:**
- **Positive Reactive Energy (Q+) Total:**
- **Negative Reactive Energy (Q-) Total:**
- **Sum Active Instantaneous Power (A+ - A-):**
- **Instantaneous Current (I) in Phase L1:** Current in phase L1 in amperes.
- **Instantaneous Voltage (U) in Phase L1:** Voltage in phase L1 in volts.
- **Instantaneous Current (I) in Phase L2:** Current in phase L2 in amperes.
- **Instantaneous Voltage (U) in Phase L2:** Voltage in phase L2 in volts.
- **Instantaneous Current (I) in Phase L3:** Current in phase L3 in amperes.
- **Instantaneous Voltage (U) in Phase L3:** Voltage in phase L3 in volts.
- **Timestamp:** Time at which the data was recorded.

## Information Flow

Data is collected from the SmartMeter through the M-Bus interface, ensuring a reliable and standardized method of communication.

## Features

### Privacy Concerns

- **Data Minimization:** The IoT Device only collects essential energy-related data, minimizing the amount of sensitive information stored.
- **Secure Communication:** Utilizes secure communication protocols to ensure data integrity and confidentiality during transmission.

### Security Concerns

- **Key Confidentiality:** The Smart Meter provides a key for the M-Bus interface, which is essential for the IoT Device's communication. This key must be stored confidentially and securely to prevent unauthorized access or tampering.
- **Data Integrity:** Implements measures to verify the integrity of the received data, ensuring that the information collected from the SmartMeter is accurate and reliable.