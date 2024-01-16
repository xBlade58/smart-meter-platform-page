# Communication

The whole set of defined components is visualized in the following figure. More information about the explicit components and their role in the system can be found in the section [1_SystemOverview](./../1_SystemOverview/overview.md). These four components SHOULD be implemented in a Smart Meter Platform.

    +----------+   +-----------------+   +------------+   +-----+
    |SmartMeter|---|SmartMeterAdapter|---|Concentrator|---|Cloud|
    +----------+   +-----------------+   +------------+   +-----+

### Communication Technologies

The communication technologies in this document are not specified strict. It is specified which basic technology MUST be used and there is a explicit technology defined that SHOULD be used in order to reach the goal of interconnectivity of different implementations. In some cases it MAY be useful to use other technologies which is ok. The only restriction is to stick to the agreed data formats as defined in [2_DataModel](./../2_DataModel/overview.md) and to stick to the topic structure as defined in this document.

### Topic Structures

In this document publish subscribe is used to communicate between different components in order to reach the goal of loose coupling. The structure of topics is always defined in a way that the subscriber can subscribe to the interest without knowing explicit id's. E.g. to all items without knowing the item id, the topic should look like this: `items/[itemId]` where the topic in the brackets is a variable value and more specific areas of the topic can be specified in a more detailed structure.

### Security Concerns

The communication channels used MUST be implemented in a secure way. If of a communication technology a secure version exists this should be used e.g. always use mqtts instead of mqtt. If it is not possible to use a out of the box confidential transportation technology a confidential solution MUST be implemented.

## Communication between SmartMeter and SmartMeterAdapter

    +----------+   +-----------------+
    |SmartMeter|---|SmartMeterAdapter|
    +----------+   +-----------------+

Communication to a SmartMeter will likely happen through a hardware connection or a infrared interface. The communication method is defined by the SmartMeter. It defines which communication capabilities it offers.

## Communication between SmartMeterAdapter and Concentrator

    +-----------------+   +------------+
    |SmartMeterAdapter|---|Concentrator|
    +-----------------+   +------------+

The Concentrator MAY be concentrating in some usecases multiple SmartMeterAdapter's. In other usecases it MAY only connect to one SmartMeterAdapter. In the last case it is RECOMMENDED to use the same device to accomplish this tasks. When running on the same device, it MIGHT be useful to use a different communication method than publish subscribe.

The SmartMeterAdapter MUST publish to a publish subscribe architecture where mqtt SHOULD be used. The topic structure MUST look like `smartMeterMessage/[smartMeterId]/[specificTopic]`.

To connect to the SmartMeterAdapter the Concentrator MUST subscribe to the topic `smartMeterMessage/*` in the publish subscribe service.

## Communication between Concentrator and Cloud

    +------------+   +-----+
    |Concentrator|---|Cloud|
    +------------+   +-----+

Because in the SmartMeterPlatform multiple concentrator's will exist, the communication technology SHOULD be based on a publish & subscribe technology. With this approach a loose coupling can be realised and it is also highly scalable.

The Concentrator MUST publish to a publish subscribe architecture where mqtt SHOULD be used. The topic structure MUST look like `concentrator/[concentratorId]/smartMeterMessage/[smartMeterId]/[specificTopic]`.

To connect to the Concentrator the Cloud MUST subscribe to the topic `concentrator/*` in the publish subscribe service.
