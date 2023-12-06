
TODO

Kommunikationwege von SmartMeter zu Cloud
    - (Publish & Subscribe darf man z.B. reinschreiben, also was verwendet werden sollte)

---

CLOUD
## Information Flow

The information flow within the smart meter system involves five distinct types of data transmissions:

- **From IoT Devices to Cloud:** Data from smart meters is transmitted to the cloud component. Examples include raw power consumption data, meter metadata, and status information.
- **From Cloud to Visualizing Applications:** Processed and aggregated data is sent to visualization applications for user interfaces. Examples include real-time power consumption graphs, historical usage trends, and meter status updates.
- **From Visualizing Applications to Cloud:** User commands and queries from visualization applications are sent back to the cloud for processing. Examples include user requests for specific consumption data or setting preferences.
- **To Processing Application:** Relevant data can be queryed by specialized processing applications for in-depth analysis. Examples include data sets for machine learning algorithms or anomaly detection.
- **From Processing Application to Cloud:** Analytical results and insights from processing applications are sent back to the cloud for storage and further distribution. Examples include anomaly detection alerts or predictive maintenance suggestions.

---

concentrator


## Information Flow

- **Data Collection:**
  - Collects data from SmartMeter-IoT devices.
  - Gathers data from devices within the household.
  - Retrieves data from external APIs, e.g. weather data.
- **Data Transmission:**
  - Sends collected data to the central cloud system.
  - Provides data to visualization applications via APIs for real-time monitoring and analysis.
