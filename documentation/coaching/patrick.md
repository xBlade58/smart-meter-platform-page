# Coaching

## Eckdaten

Datum: 30.11.2023
Anfang: 10:35
Ende: 11:25
Teilnehmer: Patrick Ritschel, Wolfgang Auer, Ralph Hoch, (Peter Reiter), Mert Ötztürk, Justin Ströhle, Stefan Beller

## Zu besprechende Themen

- Datastructure / Message Structure
    - Meter Reading
    - Commands??
- Naming of Components
    - New names as in overview.md
- QoS for MQTT
    - Mqtt settings??

## Resultate der Diskussion

### Namensgebung für Komponenten

Das Problem mit den bisherigen wordings war, dass die Schichten vermischt wurden. (Patrick)

Es sollen nun Begriffe gefunden werden, die die Aufgaben einer Komponente wiederspiegeln und nicht die Physische struktur beschreiben. Es soll möglich sein, mehrere Komponenten auf dem selben physichen Gerät zu betreiben.

#### Smart-Meter
Meter Component sagt nichts über die Funktionalität aus
Data Acquisition Node sagt bereits was über die Funktionalität aus, vielleicht macht es noch mehr als nur das
wäre ein "Device under ..." (siehe DuT)
Kann auch (Smart) Meter bleiben (Ralph, Patrick)

Einigung: **SmartMeter**

#### IoT Device:
- Meter Data Abstraction Component (MDAC)
- Data Aggregator - Nicht so nennen, weil das IoT Edge Device eher ein Data Aggregator ist
- sollte Data Collector sein
- Daten müssten möglicherweise transformiert werden
- (Smart) Meter Data Processor (kann Daten transformieren, oder auch nicht) (Ralph) (Patrick sagt nein)
((Smart) Meter) Adapter (Wolfgang) (Patrick und Ralph sagen ja)

Einigung: **SmartMeterAdapter**

#### IoT Edge Device:
- sollte Data Aggregator sein
- Local Data Hub (Ralph)
- In ZigBee würde es Concentrator heißen (Patrick) (Patrick und Ralph sagen ja)
- Concentrator oder Aggregator
((Smart) Meter) Concentrator (Stefan) (Ralph sagt semi-nein) (Patrick sagt man kann mehrere Adapter anhängen, also wird das Präfix nicht benötigt)

Einigung: **Concentrator**

#### Cloud:
- Data (Collection) Hub (2.0) (Weil mir sammeln nur Daten, und die weiteren Funktionalitäten hängen da dran) (Ralph) (Ohne Collection zu generisch für Ralph) (2.0 kommt von Wolfang)
- Even Bigger Data Hub (Peter)
- Yet Another Data Hub
- "uf die größe kuts ne druf a" - Patrick
- Cloud ist kein schlechter Name (Wolfgang)

Einigung: **Cloud**


#### Mobile App

Einigung: Wird als Applikation betrachtet, die an die Cloud angeschlossen werden kann, daher wird dies **in der Spezifikation nicht näher beschrieben**.

### Struktur der Spezifikation

- Teil1: Systemübersicht
- Teil2: Datenmodell
- Teil3: Kommunikationwege von SmartMeter zu Cloud
    - (Publish & Subscribe darf man z.B. reinschreiben, also was verwendet werden sollte)
- Teil4: Cloud-Service-Schnittstellen
    - Die Services selber sind nicht mehr Teil davon, also die Dienste nicht beschreiben (Ralph)
    Daten die von sonstigen Quellen reinkommen auch nicht spezifizieren (Ralph)
    Schnittstelle zum bereinigen der Daten braucht man schon (Patrick)
    Schnittstelle definiert entweder die Kommandos oder z.B. SQL und man gibt an wie die Queries ankommen und zurückkommen, GraphQL


### QoS 

QoS definieren für Spezifikation kein Sinn, weil dies von Usecase zu Usecase anders ist
Bei unserer Implementierung kann man die QoS schon vorgeben.

Um für unsere konkrete Umsetzung die Richtige einstellung für QoS zu finden sind folgende Fragen zu beantworten:
- Können wir mit Datenverlust leben?
- Reicht uns nur Zugestellt? 
- Können wir die Daten verarbeiten?
- Wird eine nachricht nach einer Zeit irrelevant? Z.b. Stromverbrauch
- TTL - ggf. relevant?

=> Zeitstempel vom erstellen der Daten ist immer relevant!

## ToDos

- Für konkrete Implementierung fragen für QoS beantworten
- Das wording in den Dokumenten und im System ändern. Das ändern des wordings sollte im Ticket #22 erledigt werden.
