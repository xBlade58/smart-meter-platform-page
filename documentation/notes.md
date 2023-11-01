the main purpose is 
- to collect the informations from multiple smart meters near to the hardware smart meter.
- to provide data to the cloud

it can be enhaced with
- Data Sharing Module 
    - the moudles stores data on the local device
    - the module provides the data through apis to applications
    - such a moudle would only provide a hand full of information to the cloud (it would also be possible to work without a cloud)
- Local Data Analytics Module
    - a local data analytics service can be created
    - data analyttics tasks will be executed on the device itself
    - apis provide access to such data
- event module
    - an event moudle can be equipped with functionality to send events
    - an event can be related to the current energy consumption
        - types of events
            - time triggered
            - value triggered
            - system state triggered
    - a home automation software can subscribe to such events to create own automations