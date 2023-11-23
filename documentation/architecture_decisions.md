# Architectural Decisions

**Scenario 1: Edge pushes to Cloud via HTTP (synchronous)**

* as soon as IoT Edge receives new data, it pushes to the REST API of the cloud
* data is persisted
* it waits until receiving a response

Pro:

* simple to use
* no need for intermediate broker

Contra:

* availability

**Scenario 2: Edges pushes to Cloud via HTTP (asynchronous)**

* as soon as IoT Edge receives new data, it pushes to REST API of Cloud
* Edge does not block until response is delivered
* Cloud persists data whenenver it is ready
* Afterwards, cloud responds to Edge

Pro:

* non-blocking Edge device


Contra:

* complexity because of knowledge of recipients


**Scenario 3: Communication via Broker**

* Edge publishes messages to a topic managed by a broker
* Cloud subscribes to broker, therefore is notified whenever new messages come in.
* For example MQTT

Pro:

* loose coupling between Edge and Cloud
* availability: Edge does not wait for response from Cloud

Contra:

* Guarenteed delivery challenge

**Scenario 4: Publish/asynchronous responses**

* Edge publishes to a broker
* Cloud is subscribed to the broker, therefore is notified whenever new messages come in
* Cloud responds asynchrounously to Edge after processing the message

Ultimately, we decided to go with a Publish-Subscribe pattern via MQTTS as described in Scenario 3.
