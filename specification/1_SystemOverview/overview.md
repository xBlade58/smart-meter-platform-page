# System Overview

The **Open Meter Data Platform** SHOULD consist of 4 different components. These components MUST NOT run on the same device. It is RECOMMENED to think about those components to be able to run on different devices.

The overall structure of these components should look like the following illustration.

    +----------+   +-----------------+   +------------+   +-----+
    |SmartMeter|---|SmartMeterAdapter|---|Concentrator|---|Cloud|
    +----------+   +-----------------+   +------------+   +-----+


## Smart Meter

The SmartMeter is a measuring component that MUST measure a specified set o information with a time component. E.g. a electricity smart meter measuring the energy consumption at the current timeframe.

## Smart Meter Adapter

As different Smart Meters already exist and some of them can not be called smart, there MAY be the need for a adapter to convert the gathered information into the expected format.

[More details](SmartMeterAdapter.md)

## Concentrator

As multiple smart meter's MAY exist in a small local environment, it MAY be usefull to concentrate the data from these different smart meter's and provide this information to the cloud.

[More details](Concentrator.md)

> [!NOTE]
> The SmartMeterAdapter and the Concentrator MAY be the two components which are in smaller environments likely running un the same device.

## Cloud

The Cloud is the component which MUST be responsible for storing the SmartMeter data in a structurized way as specified in the section [2_DataModel](./../2_DataModel/overview.md). The cloud MAY also consist of components capable of processing data. Offering ways to query data is also a topic of the cloud component and will be described in more detail in the section [4_CloudInterfaces](./../4_CloudInterfaces/overview.md).

[More details](Cloud.md)

