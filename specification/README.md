# Open Meter Data Platform Overview

The **Open Meter Data Platform** is a solution designed to standardize a platform to collect smart meter data. This data can be used to optimize consumption and enhance efficiency in residential and commercial settings.

This specification is helpful for everyone who wants to create a system to collect some kind of meter information. The specification will provide supporting thoughts and guidelines to reach that goal. If it becomes interesting to connect to data from other vendors this open approach will support also in this setting.

If you are using this specification to create a system, you will also benefit from other systems design for the collection of other meter data. This is especially useful because it will be possible to connect these information. E.g. if you are collecting electricity data and another system is collecting water data, it will be possible to connect these information and create a more detailed view on the consumption of the household.

## Requirements Notation

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC2119](https://www.rfc-editor.org/rfc/rfc2119).

## Parts of the Specification

This specification is divided into a structure containing 4 parts. Each part has a specific role and a small introduction and overview section.

### [System Overview](1_SystemOverview/README.md)

In this chapter the specification will give a small overview over the necessary components for building such a system. Specific implementations of the platform may differ from this recommendations.

### [Data Model](2_DataModel/README.md)

In this section the data model is described. The Data Transmission Format was inspired by a project from the Swedish Defence Materiel Administration.

### [Communication](3_Communication/README.md)

The communication from the SmartMeter to the Cloud is specified in this chapter.

### [Cloud](4_Cloud/README.md)

Which interfaces MUST be available and which of them are just RECOMMENDED is described in this chapter of the specification.

## Implementations of the Specification

The following implementations of this specification are available:

- [Open Energy Meter Data Platform](https://github.com/xBlade58/smart-meter-platform)

If you want to add your implementation to this list, please contact us.

## Contributing

This specification is a community effort. If you want to contribute to this specification, please contact us.
