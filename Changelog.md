# Changelog

Dieses Dokument listet alle für Nutzer der Blaupause / des Blaupauseassistenten relevante Änderungen. (D.h. rein interne Änderungen wie Refactoring werden hier nicht genannt).
Des Weiteren wird das Release-Datum, an dem die Änderungen auf dem Amt-24-Dev-System ausgerollt werden genannt.

## Version 1.1

Deployt am: voraussichtlich Ende November 2023

- Der Blaupause-Assistent verwendet nun die öffentliche [Scripting-API v1](https://doku.pmp.seitenbau.com/display/DFO/Scripting-API+v1)  anstelle von internen Klassen.
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
