Communication Technologies

The whole set of defined components is visualised in the following figure. These four components SHOULD be implemented in a Smart Meter Platform.

    +----------+   +-----------------+   +------------+   +-----+
    |SmartMeter|---|SmartMeterAdapter|---|Concentrator|---|Cloud|
    +----------+   +-----------------+   +------------+   +-----+


## Communication between SmartMeter and SmartMeterAdapter

    +----------+   +-----------------+
    |SmartMeter|---|SmartMeterAdapter|
    +----------+   +-----------------+

Communication to a SmartMeter will likely happen throug a hardware connection or a infrared interface. The communication method is defined by the SmartMeter. It defines which communication capabilities it offers.

## Communication between SmartMeterAdapter and Concentrator

    +-----------------+   +------------+
    |SmartMeterAdapter|---|Concentrator|
    +-----------------+   +------------+

The Concentrator MAY be concentrating in some usecases multiple SmartMeterAdapter's. In other usecases it MAY only connect to one SmartMeterAdapter. In the last case it is RECOMMENDED to use the same device to accomplish this tasks.

The SmartMeterAdapter MUST publish to a publish subscribe architecture where mqtt SHOULD be used. The topic structure MUST look like `smartMeterMessage/[smartMeterId]/[specificTopic]`.

To connect to the SmartMeterAdapter the Concentrator MUST subscribe to the topic `smartMeterMessage/*` in the publish subscribe service.

## Communication between Concentrator and Cloud

    +------------+   +-----+
    |Concentrator|---|Cloud|
    +------------+   +-----+

Because in the SmartMeterPlatform multiple concentrator's will exist, the communication technology SHOULD be based on a publish & subscribe technology. With this approach a loose coupling can be realised and it is also highly scalable.

The Concentrator MUST publish to a publish subscribe architecture where mqtt SHOULD be used. The topic structure MUST look like `concentrator/[concentratorId]/smartMeterMessage/[smartMeterId]/[specificTopic]`.

To connect to the SmartMeterAdapter the Concentrator MUST subscribe to the topic `concentrator/*` in the publish subscribe service.
