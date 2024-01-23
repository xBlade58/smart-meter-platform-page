# Adapter & Concentrator

As already mentioned we decided to put the Adapter and Cocnentrator functionalities on the same device (or application).

## Core functionality

This component acts as a MQTT subscriber as well as MQTT publisher by fulfilling the following functionalities:

- Listens for meter readings arriving at a topic in the form of `SHRDZM/8CAAB550F854/8CAAB550F854/sensor`. The messages are mapped to our standardised data format. Expand to see an example of a formatted message.

    <details>
    <summary> Example of a formatted meter reading</summary>

    ```json
    {
            "readingTime":"2023-05-06T11:18:30+01:00",
            "meterId":"bf17c6a0-82ce-4214-adbd-5a7e4ecdb0ff",
            "propertyValues":[
                {
                    "propertyName":"1.7.0",
                    "numericalValue":"133",
                    "unit":"kW"
                },
                {
                    "propertyName":"1.8.0",
                    "numericalValue":"1136784",
                    "unit":"kWh"
                },
                {
                    "propertyName":"2.7.0",
                    "numericalValue":"0",
                    "unit":"kWh"
                },
                {
                    "propertyName":"2.8.0",
                    "numericalValue":"0",
                    "unit":"kWh"
                },
                {
                    "propertyName":"3.8.0",
                    "numericalValue":"3837",
                    "unit":"kWh"
                },
                {
                    "propertyName":"4.8.0",
                    "numericalValue":"717736",
                    "unit":"kvarh"
                },
                {
                    "propertyName":"16.7.0",
                    "numericalValue":"154",
                    "unit":"kW"
                },
                {
                    "propertyName":"31.7.0",
                    "numericalValue":"0.99",
                    "unit":"A"
                },
                {
                    "propertyName":"32.7.0",
                    "numericalValue":"229.40",
                    "unit":"V"
                },
                {
                    "propertyName":"51.7.0",
                    "numericalValue":"0.42",
                    "unit":"A"
                },
                {
                    "propertyName":"52.7.0",
                    "numericalValue":"228.80",
                    "unit":"V"
                },
                {
                    "propertyName":"71.7.0",
                    "numericalValue":"0.17",
                    "unit":"A"
                },
                {
                    "propertyName":"72.7.0",
                    "numericalValue":"230.20",
                    "unit":"V"
                }
            ]
    }

    ```

</details>

- The formatted message is then sent to the MQTT broker in the Cloud. The topic structure is: `concentrator/[concentratorId]/smartMeterMessage/[smartMeterId]/readings`

## Implementation Details

Here is a code snippet where the message is formatted and sent to the MQTT broker in the Cloud.

```python
def subscribe(client_sub: mqtt_client.Client, client_pub: mqtt_client.Client):
    def on_message(client_sub, userdata, msg):
        msg = json.loads(msg.payload.decode())
        final_msg = adapt(msg) # formats message
        json_msg = json.dumps(final_msg)
        print('Sedning final msg: \n', json_msg)
        result = client_pub.publish(topic, json_msg)
        status = result[0]
        if status != 0:
            print(f'Failed to send message to cloud')

```

In regard to choosing the technology for the MQTT broker, we decided to go with [EMQX](https://www.emqx.io/). In our evaluation, we considered brokers like HiveMQ, Mosquitto, RabbitMQ. EMQX, however, stood out thanks to its high performance and scalability benchmarks.

TODO: add links to sources
