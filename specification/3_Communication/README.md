# Communication

The whole set of defined components is visualized in the following figure. More information about the explicit components and their role in the system can be found in the section [1_SystemOverview](./../1_SystemOverview/README.md). These four components SHOULD be implemented in a Smart Meter Platform.

    +----------+   +-----------------+   +------------+   +-----+
    |SmartMeter|---|SmartMeterAdapter|---|Concentrator|---|Cloud|
    +----------+   +-----------------+   +------------+   +-----+

### Communication Technologies

The communication technologies in this document are not specified strictly. It is specified which basic technology MUST be used and there is an explicit technology defined that SHOULD be used in order to reach the goal of inter-connectivity of different implementations. In some cases it MAY be useful to use other technologies which is fine. The only restriction is to stick to the agreed data formats as defined in [2_DataModel](./../2_DataModel/README.md) and to stick to the topic structure while doing "messaging" as defined in this document.

### Topic Structures

In this document publish-subscribe is used to communicate between different components in order to reach the goal of loose coupling. The structure of topics is always defined in a way that the subscriber can subscribe to the interest without knowing explicit ids. E.g. to all items without knowing the item id, the topic should look like this: `items/[itemId]` where the topic in the brackets is a variable value and more specific areas of the topic can be specified in a more detailed structure.

### Security Concerns

The communication channels used MUST be implemented in a secure way. When a secure version of a communication technology exists, it SHOULD be used e.g. always use MQTTS instead of MQTT. If it is not possible to use an out-of-the-box confidential transportation technology, a confidential solution MUST be implemented.

## Communication between SmartMeter and SmartMeterAdapter

    +----------+   +-----------------+
    |SmartMeter|---|SmartMeterAdapter|
    +----------+   +-----------------+

Communication to a SmartMeter will likely happen through a hardware connection or a infrared interface. The communication method is defined by the SmartMeter. It defines which communication capabilities it offers and how to use them. The SmartMeterAdapter MUST implement the communication method defined by the SmartMeter. Because of this restriction, this specification is not able to define a specific communication method.

## Communication between SmartMeterAdapter and Concentrator

    +-----------------+   +------------+
    |SmartMeterAdapter|---|Concentrator|
    +-----------------+   +------------+

The Concentrator MAY be concentrating in some use-cases multiple SmartMeterAdapterss. In other use-cases it MAY only connect to one SmartMeterAdapter. In the last case it is RECOMMENDED to use the same device to accomplish this tasks. When running on the same device, it MIGHT be useful to use a different communication method than publish subscribe.

The SmartMeterAdapter MUST publish to a publish subscribe architecture where mqtt SHOULD be used. The topic structure MUST look like `smartMeterMessage/[smartMeterId]/[specificTopic]`.

To connect to the SmartMeterAdapter the Concentrator MUST subscribe to the topic `smartMeterMessage/*` in the publish subscribe service.

## Communication between Concentrator and Cloud

    +------------+   +-----+
    |Concentrator|---|Cloud|
    +------------+   +-----+

Because in the SmartMeterPlatform multiple concentrator's will exist, the communication technology SHOULD be based on a publish & subscribe technology. With this approach a loose coupling can be realized and it is also highly scalable.

The Concentrator MUST publish to a publish subscribe architecture where mqtt SHOULD be used. The topic structure MUST look like `concentrator/[concentratorId]/smartMeterMessage/[smartMeterId]/[specificTopic]`.

To connect to the Concentrator, the Cloud MUST subscribe to the topic `concentrator/*` in the publish subscribe service.

## Initial Setup of the System

The initial setup of the system is a manual process at the moment. As in most cases the SmartMeterAdapter is specially designed for the SmartMeter, the setup of this connection MUST be defined by the SmartMeterAdapter. The Cloud MUST provide an interface to create a configuration file to configure the SmartMeterAdapter with all information specified in [1_SystemOverview/SmartMeterAdapter](./../1_SystemOverview/SmartMeterAdapter.md). For all components, the necessary information for connections e.g. publish-subscribe MUST be configured.
