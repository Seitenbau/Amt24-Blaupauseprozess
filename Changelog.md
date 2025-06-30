# Changelog

Dieses Dokument listet alle für Nutzer der Blaupause / des Blaupauseassistenten relevante Änderungen. (D.h. rein interne Änderungen wie Refactoring werden hier nicht genannt).
Des Weiteren wird das Release-Datum, an dem die Änderungen auf dem Amt-24-Dev-System ausgerollt werden genannt.

## Version 1.6

Deployt am: 2025-06-30

- Der Wortlaut wurde im Blaupauseassistenten und in der Blaupause generalisiert (Statt "Antrag" wird nun "Online-Dienst" oder "Anliegen" verwendet.).
- Beim Blaupauseassistenten wurden die .xml und .csv Antragszusammenfassung um Metadaten erweitert. Nun sind zusätzlich folgende Daten vorhanden: `PostfachhandleId` (aus BundID & MUK), `Formularname und Formularversion`, `Generierungszeitpunkt` (im ISO-8601 Format) und die `PDF Antragszusammenfassung` (als Base64-codierter String). 
  - Durch die Erweiterung der Metadaten kommt es bei der generierten .xml Datei zu einer Umstrukturierung der Elemente. Die folgenden Beispiele zeigen die Änderungen: 

  Vorher:
  ```
  <serviceportal-fields>
  <blaupauseGroup>
  <instance_0>
  <multiupload/>
  <testField>Testfield</testField>
  </instance_0>
  </blaupauseGroup>
  </serviceportal-fields>
  ```
  Nachher:
  ```
  <serviceportal>
  <metadata>
  <formId>6000663:Blaupause-Testformular:v1.0</formId>
  <postfachHandleId>Id des PostfachHandles</postfachHandleId>
  <pdfApplicantFormBase64>Base64 codierter String</pdfApplicantFormBase64>
  <creationDate>aktuelles Datum</creationDate>
  </metadata>
  <serviceportal-fields>
  <blaupauseGroup>
  <instance_0>
  <multiupload/>
  <testField>Testfield</testField>
  </instance_0>
  </blaupauseGroup>
  </serviceportal-fields>
  </serviceportal>
  ```
- Im Blaupauseassistenten können nun in Bereich Datenschutzerklärung unter der Angabe zur "Verpflichtung zur Datenbereitstellung" individuelle Texte angegeben werden.

## Version 1.5

Deployt am: 2025-04-07

- Es können nun auch neue Versionen eines bestehenden Prozesses (statt nur neue Prozesse) erstellt werden. (Hierbei wird eine nächste Majorversion erzeugt (z.B. Update von Prozessmodell mit Version "v1.1" erhält die Version "v2.0").)
- Beim Erstellen eines Blaupause-Prozesses kann nun gewählt werden, wie Nutzer sich authentifizieren müssen. Dabei muss mindestens eine der beiden Optionen `Mein Unternehmenskonto` oder `BundId` ausgewählt werden. Mögliche verschickte Nachrichten werden in das jeweilige Postfach der Authentifizierungsoption gesendet.
- Falls das angebundene Formular Daten auf Vertrauensniveaus abfragt, können diese nun beim Erstellen des Blaupause-Prozesses angegeben werden. Dadurch werden die Metadaten des Prozesses entsprechend gesetzt, was eine doppelte Loginaufforderung verhindert.

## Version 1.4

Deployt am: 2024-11-15

- In der Nachricht an die sachbearbeitende Person wird nun die antragstellende Person als Absender vermerkt. Dies erlaubt es, die "Antworten"-Funktion zu nutzen, um in Kontakt mit der antragstellenden Person zu kommen.

## Version 1.3

Deployt am: 2024-08-12

- Es kann nun gewählt werden, ob das Präfix der übertragenen Dateien, weiterhin automatisch aus dem Dateinamen ermittelt, oder händisch auf einen Wert gesetzt, werden soll. ([SBW-29751 - Blaupause um einen individuellen Präfix für Antragszusammenfassung und Anhänge erweitern](https://jira.pmp.seitenbau.com/browse/SBW-29751))
- Beim Erstellen eines Blaupause-Prozesses kann nun gewählt werden, wie Nutzeruploads im Prozess benannt werden. Eine Option ist es den Dateinamen aus Präfix, PiId und Feld-ID automatisch zu generieren (bisheriges Verhalten). Die andere Option ist den Dateinamen vom Dateisystem des Nutzers zu übernehmen. ([SBW-29754 - Blaupause um eine automatische Übernahme der Dateinamen von Anhängen erweitern](https://jira.pmp.seitenbau.com/browse/SBW-29754))
- Auf der Zusammenfassungs-Seite wird die PDF nun über einen Download-Button (bisher: Ein disabled Upload-Feld) den Nutzern angeboten. ([SBW-27673 - Zusammenfassungs-Download in der Blaupause durch Typ "Download" ersetzen](https://jira.pmp.seitenbau.com/browse/SBW-27673))
- Hinweistexte auf der Zusammenfassungs-Seite und der Datenschutzerklärung-Seite wurden leicht angepasst, um die Verständlichkeit der nächsten Schritte zu verbessern. ([SBW-28373 - Text auf Zusammenfassungsseite (der Blaupause) und in der Datenschutzerklärung (des Assistenten) aktualisieren](https://jira.pmp.seitenbau.com/browse/SBW-28373))
- [Bugfix]: Prozesse, die mit dem Blaupause-Assistenten erstellt wurde und deren Formular ein Placeholder-Feld beinhaltet, werfen keinen Fehler mehr, wenn eine XML-Datei erstellt wird. Das Placeholder-Feld erscheint nicht mehr im XML-Output. ([SBW-29442 - Verwendung/Anpassung von Platzhaltern in der Blaupause](https://jira.pmp.seitenbau.com/browse/SBW-29442))

## Version 1.2

Deployt am: 2024-02-12

- Das Formular des Blaupause-Assistenten läd das Teaser-Bild nun von GitHub, statt einer SEITENBAU-Website, damit die Website unabhängig von der Blaupause aktualisiert werden kann.

## Version 1.1

Deployt am: 2023-11-28

- Der Blaupause-Assistent verwendet nun die öffentliche [Scripting-API v1](https://doku.pmp.seitenbau.com/display/DFO/Scripting-API+v1) anstelle von internen Klassen.
- Für einen Prozess kann die Bezahlung aktiviert werden.
  - So erstellte Prozesse verfügen über die neuen Prozessparameter `ePayBL-keystore`, `ePayBL-keystorePassword`, `ePayBL-mandant`, `ePayBL-bewirtschafter`, `ePayBL-haushaltsstelle`, `ePayBL-objektnummer`, `ePayBL-kennzeichenMahnverfahren`, `ePayBL-frist`, `ePayBL-betrag` und `ePayBL-verwendungszweck`
- Das "Review"-Formular verfügt über eine extra Hint-Box, welche die nächsten Schritte beschreibt (Bezahlung oder Einreichung des Antrags direkt).
- Bugfix: Uploads aus Multiupload-Felder werden korrekt in die Anhänge der Servicekonto-Nachrichten hinzugefügt. 

## Version 1.0

Deployt am: 2023-08-04

- Initiales Release des Blaupause-Assistenten mit folgenden Features:
  - Erstellen eines neuen Prozesses
  - Auswahl eines Formulars
  - Auswahl des Datenübertragungsformats (XML, CSV und PDF)
  - Ausfüllen der Datenschutzerklärung
