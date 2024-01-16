# Coaching

## Eckdaten

Datum: 11.01.2024
Beginning: 10.00
End: 10.45
Participants: Walter Ritter, Mert Öztürk, Justin Ströhle, Stefan Beller

## Zu besprechende Themen

- User experience.
- Dokumentation für den User hilfreich gestalten.

## Diskussion

Wie kann die Dokumentation an Entwickler:innen zur Verfügung gestellt werden und was ist zu beachten bei der Usability?
- Übersicht: Grafik, wie was zusammenhängt als Zusatz. Also wie kann man das grafisch verdeutlichen
- System Overview: 

Für Dokumentation gilt das gleiche wie für SW: **der Anwender will ein Ziel erreichen und die Doku / SW soll ihn dabei unterstützen**
Ohne das Ziel kann man nicht sagen, ob etwas Nutzerfreundlich ist.

Ziel: System implementieren und Entwickler will prüfen, ob die Spezifikation für ihn geeignet ist bzw ob es alles abdeckt, in der weiteren folge, wenn dies interessant ist, will er die Details anschauen --> Übersicht geben, wo man sieht, dass es für den Anwendungsfall passt, mit leichtem Absprung zu den Details.
Overview first (Schnelleinführung mit Grafiken, aber auch konkret werden, Beispielhafte Anwendungen, an wen sich die Spezifikation richtet, aber möglichst kurz, können auch bullet points sein, um die Übersicht zu liefern.)

App definition statement: So etwas für die Spezifikation auch machen: Handlungsaufforderung: Vorteile nennen (nur umsetzen, nicht denken, kompatibilität - Why should i use it?)

Kommt in der Spezifikation auch vor, was beachtet werden muss, was der User machen muss? Also ein standartisiertes UI oder so?

=> Da die UI nicht speziell von uns definiert wird ist dies in unserem konkreten fall nicht zutreffend.

Liniendiagramm macht eigentlich keinen sinn, da es diskrete Werte sind. Die Fläche unter der kurve ist der Energie verbrauch welcher wiederum interessant sein könnte.

Beim App präsentieren: plakativer Usecase, und die App so gestalten, dass es offentsichtlich einfach zu erledigen ist, wenn man sich an die Spezifikation hält.

Stromverbrauch: Energie sparen, unbekannte verbraucher identifizieren
Preis: Geld sparen, Tarifauswahl

Eindrucksvoll wenn Problem und Lösung genau matchen

Dokumentationsmäßig die W3C standards für accessibility einhalten (vor allem bei Grafiken, weil ansonsten macht MD das ganze selbst)
WebAIM contrast checker, Contrast (Mac Anwendung)

Diagramme präsentieren: Welche Anforderungen muss ein Diagramm erfüllen:
- Sinnvolle Achsenbeschriftungen mit zugehöriger Einheit
- Kontraste beachten
- passender Typ verwenden (Flächendarstellung bei Größenvergleich z.B. ungünstig, weil bezieht es sich auf die Fläche, den Radius oder was auch immer) => Darstellungsart sollte zu der Dimensionalität deer Daten passen.
- Titel
- Legende

Bildunterschriften
Verbindung von Grafik zu Text ist ein wichtiges Hilfsmittel
Bei Grafiken direkt darstellen, was man damit aussagen will, ohne interpretationsspielraum.

Es geht also immer darum, was will der Benutzer (sei es der Entwickler oder der App-Nutzer)

Stromkosten und Verbrauch in einem Diagramm darstellen ist gut, wenn es um den direkten Zusammenhang geht, erhöht aber die Komplexität

Positive Sachen wirken immer besser als negative -> z.B. eingespaartes geld wegen gespaartem strom trotz gestiegenem Rechnungsbetrag.

Gamification von erlebnissen mit Anwendungen ist für einige Nutzer interessant.
Nudging vielleicht auch hier betrachten (wöchtenliche Zusammenfassung oder so), Notification
Ebenfalls Abhängig vom Ziel der User
Beispiel PV Anlage: immer auf Handy schauen um nachzuverfolgen, wie viel Strom selbst produziert, wie viel eingekauft
Energiebewusstsein wird höher
Da in einem Haushalt mehrere Personen am Energieverbrauch beteiligt sind, könnte ein Dashboard für alle interessant sein.

## Resultate der Diskussion

Nächste Schritte:
Ziel vom User
Fallbeispiel visualisieren

Dashboard, das den Stromverbrauch zur Vorwoche anzeigt. Die Informationen können dann vom Benutzer im Kontext betrachtet werden.
z.B. 
 - letzte Woche hatten wir eine Geburtstagsfeier, daher wurde mehr strom als gewöhnlich verbraucht.
 - in dieser Woche waren wir im Urlaub, daher haben wir jetzt einen Verhältnissmäßig so hochen Stromverbrauch.
