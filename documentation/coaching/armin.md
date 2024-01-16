# Coaching

## Eckdaten

Datum: 07.12.2023
Start: 10:00
End: 10:43
Participants: Armin Simma, Mert Öztürk, Justin Ströhle, Stefan Beller

## Topics to Discuss

Security Considerartions
Connections of the Platform
Dataprotection -> what to consider (anonymization)

## Discussion

Die Secure Varianten sollten immer verwendet werden, z.B. MQTTs.
Allgemein kann man sagen, dass es speziell bei verbindungen überlegungen zur security gibt und beim Speichern von daten geht's um Privacy. Privacy hat aber immer auch implikationen auf die Security!

Für unsere Spezifikation und Umsetzung könnte **Differential Privacy** interessant sein -> d.h. identifizierende attribute werden entfernt. Quasi identifizierende werden basierend darauf, ob sie in ausreichender zahl in der abfrage vorkommen "anonymisiert". Annonymisiert heißt dass adas attribut entweder randomisiert oder weglassen wird. Es ist auch möglich anfragen komplett abzulehnen die zu wenige daten enthalten würden.

Wenn man als beispiel die Daten einer kleinen gemeinde abfragen würde und in den Daten die Anzahl kinder zurückgegeben würde, wäre die Familie mit 7 Kindern schnell identifiziert. Daher würde dann das Attribut Kinder annonymisiert werden. Die Annonymisierung sollte aber auch zweckmäßig sein, das heißt man würde nicht davon ausgehen, dass jemand aufgrund der solareinspeisungswerte den standort herausfinden könnte, das wäre zu abstrakt.

Es muss möglich sein, dass die Besitzer:in von Daten alle nicht anonymisierten Daten löschen kann.

Die Daten dürfen allerdings auch nicht soweit anonymisiert werden, dass diese keiner Besitzer:in zugeordnet werden könnte.

Allgemein ist das Verschlüsseln von daten immer eine einfache und effektive Methode. Die Frage die immer geklärt werden muss, ist wer den schlüssel bekommt.

Daten grundsätzlich verschlüsseln, wer hat zugriff auf welche Daten?

Ein noch neues aber spannendes Thema bzw. Technologie ist: Attribute based encryption.

Großes Problem -> wo ist der Schlüssel gespeichert? Lösung kann sein dies in einem HSM abzulegen. Die Software Vault kann auch interessant sein.

Wenn Daten verschlüsselt gespeichert sind, ist die "Schwachstelle" der User der ggf. sein Passwort verliert. Hier kann MFA sinnvoll sein, allerdings ist der Betreiber nicht haftbar zu machen wenn user daten durch unachtsammes handeln verlieren.

## Results of Discussion

- im datenmodell die beforzugte variante der speicherung angeben.
- was sollte bei der Afrage bzgl. anonymisierung möglich sein? Das sollte im Interface Dokument spezifziert werden.
- nur notwendige daten erfassen.

