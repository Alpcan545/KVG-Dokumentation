## Erinnerungen
- 26.02.: Rüdiger zum Geburtstag gratulieren

Für Morgen: 
- Termin transport for go live
  - Customizingtransport für alle
  - Wann genau soll Maui für alle Verfügbar
  - Backendtransport Reihenfolge und zeitliche Einteilung mit Items
  - Workbench- und Customizingtransporte in PA1
  - Customizingverteilung (+ Stammdatenverteilung)

  - Bugfix betrifft 
    - Meldugnserstellung wurde gefixt -> SAP Nachricht - Meldung wurde im Hintergrund gespeichert
    - Problem: Bei der Verteilung wurden die Vorgangsdaten gelöscht. Diese wurden nicht über das Verteilkriterium 20 verteilt - Wird dieser Auftrag im Backend durchgesichert, werden dem User alle Vorgänge zum Auftrag entzogen obwohl diese eine gültige Expiry haben, der Auftragskopf erhält ein Update.
    - Lösung nach Backend Transport: 


Wird ein Auftrag für Online geholt, der nicht für mich relevant (nicht relevant weil nicht über den Planner verteilt) ist und die Verteilkriterien für den User haben eine Vorgangsbeschränkung (z.B: 20 OTP etc) dann erhält der User beim Onlinerequest den kompletten Auftrag mit allen Daten.

  - Wenn es nicht gut sein sollte dass ein User alle Vorgänge sieht, können wir dafür sorgen dass der User den gesamten Auftrag nicht mehr online holen kann - man kann das nicht Vorgangsspezifisch machen

  - Beispiel: Wenn Auftrag 5 Vorgänge und Checkliste, und User soll nur 1 Vorgang - nicht möglich!
  - User Bekommt entweder gesamten Auftrag oder wir entziehen ihm den Auftrag

  - Wenn Aufträge auf dem Client zunächst fehlen sollten diese Online geholt werden

## Automatischer Log-Off
- **Konzept**: Ähnlich wie in Bank-Apps automatischen Log-Off implementieren
- **Trigger**: Log-Off nach Inaktivität (letzte Anmeldung vor 15 Stunden)
- **Funktionalität**: Automatischer Log-Off mit gleichzeitigem Sync
- **Test-Szenario**: Mit 15-Stunden-Inaktivitäts-Schwelle testen
- **Vorteile**: Erhöhte Sicherheit, automatische Datensynchronisation
- **Absprache mit Entwicklung**: Aktuell gibt es keine Funktion, die nach einer bestimmten Zeit einen Log-Off erzwingt. Muss eingebaut und mit Customizing verbunden werden, um eine feste Zeit anzugeben, wann der Log-Off mit Sync stattfinden soll. Aufwand gesch?tzt 2 Tage.

## Neue Szenarien VTI / VTF - Erforderliche Daten
- **Auftragsarten**: Benötigt für VTI und VTF
- **Selektionsvarianten**: Benötigt für VTI und VTF

## Rollout Maui
- **Start-Datum**: 02.03.2026
- **Verfügbarkeit am Start-Datum**: Nicht verfügbar am 02.03. - Rollout beginnt erst ab diesem Datum


## Xamarin / Backend-Update Test (iPad)
- **Hinweis**: Xamarin-Version auf dem iPad muss auf Kompatibilit?t mit dem neuen Backend-Update getestet werden.
- **Aktueller Stand (VTS)**: Anmeldung m?glich; St?rung erfassen (Auftrag angelegt); Zeitr?ckmeldung im Vorgang; Materialr?ckmeldung; Sync funktioniert; Checklisten (2-Augen-Prinzip); Mini Sync durchgef?hrt; Navigation nach Mini Sync funktioniert; Interaktive PDFs funktionieren.
- **Aktueller Stand (VTR)**: Mini Sync (4-Augen-Prinzip) funktioniert.
- **LKW R?ckmeldung**: Im Szenario wurde die LKW R?ckmeldung getestet. Diese funktioniert.
- **LKW R?ckmeldung**: Die mobile T?tigkeitsart bleibt nach dem Sync leer.
