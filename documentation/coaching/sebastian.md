# Coaching

## Eckdaten

Datum: 30.11.2023
Beginning: 9:35
End: 10:15
Participants: Sebastian Hegenbart, Mert Öztürk, Justin Ströhle, Stefan Beller

## Zu besprechende Themen

- Visualisierung von Daten und welche Daten sind sinnvoll
- KI integration in unsere Architektur

## Diskussion

### Was will der Kunde sehen?
- Schwierig - einen Nutzen für den Kunden zu bringen
- ggf. Trends anzeigen
- Mehrverbrauch im Monat

### Visualisierungsarten

- Balkendiagramme
- Diagramme mit Punkten (keine Durchgezogenen Linien)

Ein Diagramm in der form einer Uhr könnte interessant sein um den Stromverbrauch im Kontext darzustellen.

Man könnte eine Animation erstellen auf der am Smartphone in der App durch Tag und Nacht gescrollt werden kann und auf diesem, ein Stromverbrauch angezeigt wird ggf. mit Diagramm am unteren Rand oder auf andere spielerische Weise.

### KI Modelle

Es sollte offen gelassen werden, wo im System ein KI Modell zu platzieren ist, je nach Anwendungsfall macht eine globale Lösung sinn und für lokale Probleme ist auch aus Datenschutzsicht eine lokale Auswertung sinnvoll.

Allgemein kann gesagt werden, es ist abhängig vom Usecase und es sollte im idealfall dort gemacht werden, wo die Daten verfügbar sind.

In der Spezifikation ist ein KI Modell als Processing Component zu sehen, das heißt, die Komponente holt Daten ab und liefert sie ggf. wieder zurück falls das angedacht ist. Wie es in der Komponente verarbeitet wird, ist für das darüberliegende System nicht relevant.

## Resultate der Diskussion

- Daten darstellen die für den Nutzer relevant sind
- Ein KI modell wäre in unserer Spezifikation eine Erweiterung der Cloud also eine Processing Component.
