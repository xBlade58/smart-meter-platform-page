# DataModel

The Data Transmission Format was inspired by a project from the Swedish Defence Materiel Administration.

The specification comprises a SysML Block that represents the template and an associated Parametric Diagram that defines the templates and Platform specific objects instantiated by the MeterReading template.

[Template MeterReading](http://www.plcs.org/plcslib/plcslib/data/contexts/SwedishDefence/templates/MeterReading/template.html)


The Swedish Defence Materiel Administration provides a diagram of the data structure used in the system. Since the entire structure is too specific and not needed at this level of accuracy, we have reduced it to the following subset that SHOULD be implemented in this system. The following image shows this subset.

![Interesting Part of the Swedish Defence Specification Diagram](images/datastructure.png "Interesting Part of the Swedish Defence Specification Diagram")
[Full Diagram](http://www.plcs.org/plcslib/plcslib/data/contexts/SwedishDefence/dexs/OperationalData/dex_business_information_model.html#Model_Diagrams)

## The components of the data model

The different parts of the suggested subset are described in the next sub chapters. The data model is inspired by the Swedish Defence Platform.

### MeterReading

The _MeterReading_ specifies a specific MeterReading from one _MeterIndividual_. This element MUST consists of an id and the reading time. It SHOULD also contain a faultCode to identify why the reading MAY not be correct. It is RECOMMENDED to follow [RFC 3339](https://www.rfc-editor.org/rfc/rfc3339.html) for the reading time format. 

### PropertyValue

The _PropertyValue_ is a flexible element of this specification and for one _MeterReading_ multiple _PropertyValue's_ MAY exist. A _PropertyValue_ MUST consist of a value and SHOULD also contain a unit if applicable.

### OperationalPropertyDefinition

A single _PropertyValue_ belongs to a overall type, in order to combine the same properties from different meter readings. The _OperationalPropertyDefinition_ MUST define an ID. It MAY specify allowed units and a description.

> [!NOTE]
> The purpose of an OperationalProperty is to make the same values from different sources comparable. Two SmartMeters (e.g. from different manufacturers) measuring a value from the same type should use the same OperationalProperty. So a request to the data do only need to select which type of data should be returned.

To make multiple implementations compatible with each other, operational properties are defined in this specification in the folder `operationalProperties` grouped in files by categories of operational properties. Operational properties relevant to multiple users SHOULD be added to the specification creating a new version of the specification. Properties not relevant to multiple users can be created in the own system. If at some point this special property gets relevant to multiple users and adopted in the specification, the own created property SHOULD be replaced by the specified one. For properties in this specification, it is RECOMMENDED to use a well known standard. E.g. for energy data the well known OBIS codes are used as a base for the creation of the operational properties.

### PhysicalMeterElement

A generation of SmartMeter's from the same Manufacturer offering the same OperationalProperty's SHOULD be considered as one _PhysicalMeterElement_. A _PhysicalMeterElement_ MUST specify the set of _OperationalProperty's_ the _PhysicalMeterElement_ can provide. The _PhysicalMeterElement_ SHOULD also specify meta information about the SmartMeter it represents such as a name and a description.

### MeterIndividual

A _MeterIndividual_ is a actual individual device which can be identified typically as one piece of hardware with a own serial number. It is an instance of a _PhysicalMeterElement_. A _MeterIndividual_ MUST specify the _PhysicalMeterElement_ as it is an instance of it. The _MeterIndividual_ MAY specify meta information about the SmartMeter it represents such as a name and a description.

## Actual Implementation of the data model

In the following document, the MeterReading is visualized as a YAML structure.

![ExampleOfMeterReading](./data/MeterReadingObject.yaml "ExampleOfMeterReading")

With this yaml based structure json structures can be generated, to get a feeling of how data will be available from different smart meter types. 

For the first example consider a electrical smart meter capable of measuring different phases. When different types of devices would support different set's of property values, they would still be comparable due to the grouping of property values by the _OperationalPropertyDefinition_.

<details>
<summary>MeterReading Example with electrical readings</summary>

![MeterReading Example with electrical readings](./data/electricalSmartMeter.json "MeterReading Example with electrical readings")

</details>

The same concept can be used for a water smart meter.

<details>
<summary>MeterReading Example with water readings</summary>

![MeterReading Example with water readings](./data/waterSmartMeter.json "MeterReading Example with water readings")

</details>
