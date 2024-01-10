# SmartMeterAdapter

## Overview

The SmartMeterAdapter acts as a bridge between the SmartMeter provided by the energy provider and the Concentrator. It establishes a connection to the SmartMeter, collects essential energy-related data, and transfers this data to the Concentrator for further processing and analysis. The connection method to the SmartMeter is specified by the SmartMeter itself, ensuring compatibility and seamless data retrieval.

## What is the Component About

The SmartMeterAdapter component is the first controllable component. This means, that this component is the first one this specification is able to specify because the SmartMeter devices offer different connection methods and are already existing and "hard" to replace.

### Missing information

It is not given that every smart meter is able to deliver every information our platform needs. For this abstraction in general there are possibilities to create profiles containing of different sets of operational properties per smart meter type. But there are also informations that the smart meters typically do not know like size of a household. If such informations are necessary, the SmartMeterAdapter MUST add these informations to the data object.

#### Configuration of Information

If data needs to be added like houssehold size, the SmartMeterAdapter MUST provide an option to configure these details. The exact way of reaching this goal is not part of this specification.

### Connecting to the SmartMeter

The connection to the SmartMeter is to be implemented individually because it differs from the type of the given SmartMeter and therefore also not part of this specification. It MUST be ensured, that the connection method to the SmartMeter is as reliable as possible.

#### Configure Mapping

The mapping of values collected from the SmartMeter to values conform to the operational properties should also be configured in the SmartMeterAdapter.

### Transmitting Data to the Concentrator

The data which is collected needs to be transmitted to the Concentrator component as described in [3_Communication](./../3_Communication/overview.md) and should contain the data descibed in [2_DataModel](./../2_DataModel/overview.md).

### Security Concerns

Storing configuration data MUST be possible in a way to guarantee confidentiality and integrity.
