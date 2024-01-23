# System Overview

The **Open Meter Data Platform** SHOULD consist of at least four different components. These components MAY run on 4 different hardware devices. In some cases it MAY be useful to run some of the components on the same hardware device. More details on that can be found in the detailed description of the components.

The overall structure of these components should look like the following illustration.

    +----------+   +-----------------+   +------------+   +-----+
    |SmartMeter|---|SmartMeterAdapter|---|Concentrator|---|Cloud|
    +----------+   +-----------------+   +------------+   +-----+


## Smart Meter

The SmartMeter is a measuring component that MUST measure a specified set of information with a time component. E.g. a electricity smart meter measuring the energy consumption at the current time-frame.

## Smart Meter Adapter

As different Smart Meters already exist, there MAY be the need for a adapter to convert the gathered information into the expected format. Also some information relevant to the platform MAY be added to the data. E.g. the SmartMeterAdapter MAY add the id of the MeterIndividual to the data.

[More details](SmartMeterAdapter.md)

## Concentrator

As multiple smart meters MAY exist in a small local environment, it MAY be useful to concentrate the data from these different smart meters and provide the aggregated information to the cloud.

[More details](Concentrator.md)

> [!NOTE]
> The SmartMeterAdapter and the Concentrator MAY be the two components which are in smaller environments likely running on the same device.

## Cloud

The Cloud is the component which MUST be responsible for storing the SmartMeter data in a well structured way as specified in the section [2_DataModel](./../2_DataModel/README.md). The cloud MAY also consist of components capable of processing data. Offering ways to query data is also a topic of the cloud component and will be described in more detail in the section [4_Cloud](./../4_Cloud/README.md).

[More details](Cloud.md)

