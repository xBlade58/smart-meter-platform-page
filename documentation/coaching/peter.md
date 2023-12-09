# Coaching

## Eckdaten

Datum: 07.12.2023 
Beginning: 10:48 
End: 11:25
Participants: Peter Reiter, Mert Ötztürk, Justin Ströhle, Stefan Beller

## Topics to Discuss

- datatypes in use
- use of timescale
- one household could have multiple smart meters?
- calling the data - what makes sense?

## Results of discussion

### Architecture

Mert: Inhalt des Coachings - Architektur und Spezifikationsthemen
Architecture ist Hexagonal
Erklärungen zur Architektur

Peter: Gut das Technische annotationen ausgelagert sind. Timestamp ist für ein Meterreading nicht ausreichend als id. In der Swedish defence documentation ist eine explizite id per meter reading spezifiziert - sollten wir hier dann auch so umsetzen.

Peter: _Timestamp with Timezone Datatype_ wäre sinnvoll zu verwenden.

### Wieviele Smart Meter pro Household?

Peter: Houshold hat mehrere Smart Meter wenn z.B. eingespeist wird und für dies ein zweites SmartMeter verwendet wird.

### Cloud Interfaces in der Dokumentation

Stefan: Introduction zu CloudInterfaces

Peter: 
Daten abholen gibts mehrere Möglichkeiten
- FTP Server (nicht unplausiebel)
- Rest schnitstelle
- JDBC Schnitstelle
- Graph QL
- ...

Ein interessantes Buch zum Thema wäre _Data Management at Scale | by Piethein Strengholt_
in der version Best Practices for Enterprise Architecture

Darin beschrieben sind _data access layers_ hier gibt es verschiedene Möglichkeiten und man kann aufgrund dieser infos herausfinden was sinnvoll ist.

Stefan: Würdest du sagen, dass eine spezifikation der REST schnitstelle aus deiner sicht für die Dokumentation sinnvoll ist? Man könnte hier beispielsweise spezifizieren, welche parameter mitgegeben werden können müssen, beispielsweise properties wie region und zeitraum könnten hier interessant sein für eine Abfrage.

Peter: Grundsätzlich eine Möglichkeit, typischerweise ist es wichtig Daten nur mit benötigten feldern für Forscher bereitzustellen. (anm. aktuelles Beispiel aus der Praxis wurde kurz diskutiert) Desweiterne zu beachten: Datenmengen können groß werden und für größeres kann auch sinnvoll sein einen bulk export anzubieten - ggf. csv oder json.

Supabase ist auch eine interessante Technologie die man sich ansehen könnte.

## todos

Peter bringt nächste Woche das Buch "Data Management at Scale | by Piethein Strengholt" mit.

