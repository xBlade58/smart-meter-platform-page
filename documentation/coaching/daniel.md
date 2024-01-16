# Coaching

## Eckdaten

Datum: 14.12.2023
Beginning: 10:05
End: 11:25
Participants: Daniel Rotter, Mert Ötztürk, Justin Ströhle, Stefan Beller

## Topics to Discuss

- Architektur von der data processing component
- Household service / Meter Service
- Ways of communication

## Discussion

Vorzeigen vom aktuellen Stand

### Spezifikation

**Problemstellung der Spezifikation:**

Die Spezifikation sollte sich auf die Lösung von Kompatibilitäts- und Austauschbarkeitsproblemen konzentrieren. Möglicherweise ist es ratsam, bestimmte Standards wie MQTT oder Formatvorgaben in der Spezifikation festzulegen. Bei der Festlegung der Spezifikation gibt es einen schmalen Grat zwischen Freiheiten und Einschränkungen. Wir sollten uns darauf konzentrieren, welches Problem die Spezifikation lösen soll. Es ist entscheidend, Szenarien durchzudenken, in denen die Spezifikation unterstützen soll, insbesondere auch bei der Implementierung eines neuen Smart Meter Adapters.

**Publish-Subscribe-Ansatz**
Die Anpassung des Folgelayers ist akzeptabel, vorausgesetzt, sie abstrahiert den weiteren Folgelayer. Bei der Formulierung der Spezifikation ist die Verwendung von "must", "should", etc. gemäß RFC 2119 zu berücksichtigen. Eine Frage, die aufkommt, ist, ob wir uns in Richtung des ISO-OSI-Modells bewegen möchten. Es könnte sinnvoll sein, die Spezifikation auf einem bestimmten Detailniveau zu gestalten oder so präzise wie das HTTP-Protokoll. Wir müssen die Gültigkeitsdauer der Spezifikation berücksichtigen, da sie ansonsten bei Einführung neuer Technologien obsolet werden könnte. Die Einbindung einer REST API wirft wiederum Fragen auf, insbesondere in Bezug auf die Verbindung mit zusätzlichen Systemen.

Eine gute Austauschbarkeit erfordert möglicherweise eine konkretere Definition der Technologien oder zumindest eine spezifische Implementierung auf einer Ebene.

_Zusammenfassung: Es ist wichtig festzulegen, wie hoch der Abstraktionsgrad der Spezifikation sein soll._

**Referenzimplementierung**
Diskussion um die hexagonale Architektur. Die Definition der Ports erfolgt durch das Modell. Das Repository Interface sollte im Model definiert werden, wobei das Domain Layer die Abfragen vorgibt. Die Application-Schicht bildet die Use Cases ab und behandelt klassischerweise Sicherheitsaspekte. Die Diskussion, ob Ports ins Domain Model gehören, führte zu dem Schluss, dass sie dort hingehören, um eine klare Trennung zu ermöglichen.

Es besteht die Debatte, ob bestimmte Services als Domain oder Application Service betrachtet werden sollten. Die Domänenlogik sollte klar im Domain Layer bleiben, während die Anwendungsschicht sich um Aspekte wie die Handhabung von Frameworks kümmert.

**Services**
Es wird diskutiert, ob DTOs als Rückgabetyp verwendet werden sollten, wobei die praktische Anwendbarkeit gegenüber rein akademischen Ansätzen abgewogen wird.

## Results of Discussion

- Festlegen, wie die Abstraktionsebene der Spezifikation definiert wird.
- Klären, welche Services als Domain oder Application Service eingestuft werden sollen.
- Repository Interfaces in den Domain Layer
