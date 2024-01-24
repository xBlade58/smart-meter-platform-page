# SmartMeterAdapter

## Overview

The SmartMeterAdapter acts as a bridge between the SmartMeter provided by the energy provider and the Concentrator. It establishes a connection to the SmartMeter, collects essential energy-related data, and transfers this data to the Concentrator for further processing and analysis. The connection method to the SmartMeter is specified by the SmartMeter itself, ensuring compatibility and seamless data retrieval.

## What is the Component About

The SmartMeterAdapter component is the first controllable component. This means, that this component is the first one this specification is able to specify because the SmartMeter devices offer different connection methods, are already existing and "hard" to replace.

### Missing information

It is not given that every smart meter is able to deliver every information our platform needs. For this abstraction in general there are possibilities to create profiles containing different sets of operational properties per smart meter type. But there is also information that the smart meters typically do not know, such as "household size". If this level of details is necessary, the SmartMeterAdapter MUST add these information to the data object.

#### Configuration of Information

If additional information (e.g. household size) needs to be added, the SmartMeterAdapter MUST provide an option to configure these details. The exact way of reaching this goal is not part of this specification. It MAY be possible by using special operational properties for this purpose.

### Connecting to the SmartMeter

The connection to the SmartMeter has to be implemented individually because it differs from the type of the given SmartMeter and therefore is also not part of this specification. It MUST be ensured, that the connection method to the SmartMeter is as reliable as possible.

#### Configure Mapping

The mapping of values collected from the SmartMeter to values conform to the operational properties SHOULD also be configured in the SmartMeterAdapter. This is the case because the SmartMeterAdapter is the first component that is able to know the exact mapping of the values. The exact way of reaching this goal is not part of this specification.

### Transmitting Data to the Concentrator

The data which is collected MUST be transmitted to the Concentrator component as described in [3_Communication](./../3_Communication/README.md) and SHOULD contain the data described in [2_DataModel](./../2_DataModel/README.md).

### Security Concerns

Storing configuration data MUST be possible in a way to guarantee confidentiality and integrity. Confidentiality is especially relevant to data that is relevant for the users privacy and the system security.

### Initial Setup

The SmartMeterAdapter SHOULD be setup initially with a configuration file. The configuration file MUST specify the MeterIndividualId, it MUST contain information about which mapping to consider for OperationalPropertyValues and SHOULD contain information to connect to the cloud system and establish integrity and authenticity of the data provided.
