# Open Meter Data Platform Overview

The **Open Meter Data Platform** is a solution designed to standardize a platform to collect smart meter data. This data can be used to optimize consumption and enhance efficiency in residential and commercial settings. 

This specification is helpful for everyone who wants to create a system to collect some kind of meter information. The specification will provide supporting thoughts and guidelines to reach that goal. If it will become interesting to connect to data from other vendors this open approach will support also in this setting.

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
