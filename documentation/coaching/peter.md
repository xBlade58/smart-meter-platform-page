# Coaching

## Eckdaten

Datum: 07.12.2023 
Beginning: 10:45
End: 11:25
Participants: Peter Reiter, Mert Öztürk, Justin Ströhle, Stefan Beller

## Zu besprechende Themen

- datatypes in use
- Verwendung von timescale db
- Ein household kann mehrere smart meters haben?
- Was macht beim Abfragen der Daten sinn?

## Diskussion

### Architektur

Mert: Inhalt des Coachings - Hexagonale Architektur und Spezifikationsthemen
Vorzeigen von unserer implementierten Architektur
Architecture ist Hexagonal
Erklärungen zur Architektur
Klassen kommentieren
Autoren der Klassen

Peter: Gut das Technische annotationen ausgelagert sind. Timestamp ist für ein Meterreading nicht ausreichend als id. In der Swedish defence documentation ist eine explizite id per meter reading spezifiziert - sollten wir hier dann auch so umsetzen.

Peter: _Timestamp with Timezone Datatype_ wäre sinnvoll zu verwenden.

### Wieviele Smart Meter pro Household?

Peter: Houshold hat mehrere Smart Meter wenn z.B. eingespeist wird und für dies ein zweites SmartMeter verwendet wird.
Household 1 ... n SmartMeter (z.B. PV Anlage --> 2. SM)

### Cloud Interfaces in der Dokumentation

Stefan: Introduction zu CloudInterfaces

Peter: 
Für den Datenzugriff gibts mehrere Möglichkeiten
- FTP Server (nicht unplausiebel)
- Rest schnitstelle
- JDBC Schnitstelle
- Graph QL
- Vorschläge machen, und Beispiele implementieren
- ...

Ein interessantes Buch zum Thema wäre _Data Management at Scale | by Piethein Strengholt_
in der version Best Practices for Enterprise Architecture

Darin beschrieben sind _data access layers_ hier gibt es verschiedene Möglichkeiten und man kann aufgrund dieser infos herausfinden was sinnvoll ist.

Stefan: Würdest du sagen, dass eine spezifikation der REST schnitstelle aus deiner sicht für die Dokumentation sinnvoll ist? Man könnte hier beispielsweise spezifizieren, welche parameter mitgegeben werden können müssen, beispielsweise properties wie region und zeitraum könnten hier interessant sein für eine Abfrage.

Peter: Grundsätzlich eine Möglichkeit, typischerweise ist es wichtig Daten nur mit benötigten feldern für Forscher bereitzustellen. (anm. aktuelles Beispiel aus der Praxis wurde kurz diskutiert) Desweiterne zu beachten: Datenmengen können groß werden und für größeres kann auch sinnvoll sein einen bulk export anzubieten - ggf. csv oder json.

Supabase ist auch eine interessante Technologie die man sich ansehen könnte.

## Resultate der Diskussion

Peter bringt nächste Woche das Buch "Data Management at Scale | by Piethein Strengholt" mit.
