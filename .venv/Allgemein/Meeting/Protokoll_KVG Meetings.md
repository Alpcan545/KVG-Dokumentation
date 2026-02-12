# Protokoll – 13.01.2026

- Uhrzeit: 13–15 Uhr

## Thema / Anlass
Status-Update zum Maui-Rollout und aktuellen Entwicklungsständen.

## Rollout-Planung
- Rollout Maui: **Ende Januar / Anfang Februar** vorgesehen. 02.03.26
- Nächste Systemspiegelung am 26.01.
- Leistungsarten sind noch nicht für 2026 noch nicht eingeplant - deswegen Roll-Out erst nach Spiegelung
- 
- **Konkretes Datum steht noch nicht fest** (wird nachgereicht).

## Aktuelle Updates (Maui-Versionen)
- **Berichtsausgabe (Häkchen)**: Umsetzung **noch in Arbeit**.
- **Pfeile**: Funktionieren aktuell **nur in VTR**.
- **Backend-Transport nach KA1**: Wird **weiterhin getestet**.
- Mini Sync in VTR ohne Probleme
  

## Offene Punkte
- Finales Rollout-Datum festlegen und kommunizieren. - 02.03.26
- Abnahme/Validierung der Berichtsausgabe inkl. Häkchen nach Fertigstellung. - Absprache mit der Entwicklung
- Klärung/Umsetzung, dass Pfeile auch außerhalb VTR funktionieren (Zielsysteme definieren). - Absprache erfolgt, in Zukunft wird es in VTS auch Checklisten mit mehreren Checklisteneinträgen geben wird
- Testergebnisse Backend-Transport nach KA1 dokumentieren (inkl. ggf. Fixes/Retests). - Absprache erfolgt 
- Zwei verschiedene Clients - Xamarin wird nicht mehr nach Maui Rollout verwendet 
- LKW Rückmeldung VTV - Fehlermeldung in der LKW Buchung - wird noch von KVG verbucht - nächste Woche Mail an Leona zur Absprache
- Oxando friert ein - und lädt dann hinterher weiter > Stuttering Problem - Möglicherweise Performance Problem - Absprache mit Phil/ Klaus
- Berechtigungen IW33, ST22
- Statusabfrage bei Vorgangserstellung erzeugt Problem in Oxando: Auftrag Nr. 30094535

## Nächste Schritte
- Terminfindung Rollout (Ende Jan/Anfang Feb) + Abstimmung mit Stakeholdern. - Finaler Termin 02.03. für das Rollout
- > Februar als Testzeitraum
- Weiterentwicklung Berichtsausgabe (Häkchen) und anschließender Test. - Neue Version wird aktuell von Marc gebaut
- Analyse, warum Pfeile derzeit nur in VTR funktionieren; Fix bzw. Konfigurationsanpassung ableiten.
- Fortsetzen der KA1-Transporte inkl. Testprotokoll und Freigabeentscheidung.

---

# Protokoll – 19.01.2026

## Offene Punkte
- Zeitrückmeldungen - Problem wurde mit Moritz und Carla reproduziert. Möglicherweise Zusammenhang mit Backend Transport. Problem befindet sich im KA1 und wird von Moritz bearbeitet (ggf. mit Phil). - Weitere Absprachen folgen

## Geplante Aktivitäten
- Nächste Systemspiegelung: 26.01. – 28.01.2026
---

# Protokoll – 20.01.2026

## Tickets / Updates
- **KEM-232**: Fehlende grüne Häkchen im generierten Bericht
  - Status: Von Marc bearbeitet, **bereit zum Testen**
  - Maßnahme: Testphase kann beginnen
  - Nach Absprache mit Carla sind keine weiteren Punkte für eine neue Version offen
  - Version muss noch gebaut und in den Verteiler / Testflight eingespielt werden

---

# Protokoll – 28.01.2026

## Thema / Anlass
Fortsetzung des Status Updates zur Systemspiegelung und ausstehenden Fehlerbehebungen.

## Systemspiegelung
- Status: **Abgeschlossen**
- Leistungsarten sind im **KA1 freigeschaltet**

## Entwicklung / Tests
- Neue Version erscheint **heute von der Entwicklung**
- **Maui Version 1.0.14454.1 / iOS 1.0.78** beinhaltet:
  - **KEM-237**: Langtext wird nicht verbucht
  - **KEM-234**: Fehlende Farben – Auftrag Statusabweichung
  - **KEM-232**: Fehlende Ergebnis-Icons in Checklisten-Report
  - **KEM-235**: Abstürze bei interaktivem Formular
  - **KEM-233**: Löschen-Button Vorgang
- Testphase: **Carla und Alpcan** testen die Version
- **02.03.2026**: Maui Starttermin (Rollout)

## Offene Punkte / Fehler
- **THIELET Fehlermeldung** (Mehmet):
  - Status: **Noch nicht behoben**
  - Carla hat bereits Daten vom SAP angefordert
  - Maßnahme: Wird fortgesetzt nach Datenbereitstellung
  - **Holger** muss nach der Fehlermeldung mit dem SNOTE gefragt werden

## Material löschen / Stunden stornieren 
- Status: Muss noch **mit Mehmet getestet** werden

## LKW-Buchung
- **Storno bei LKW Buchung**: Muss über die **KW21N** gehen (nicht über normale Buchung)
- **Stundenbuchung LKWs**: Geht über die **KW21N** (nicht über normale Buchung)
- LKW muss von **KVG nochmal in MAUI getestet** werden, sonst Problem in RBK
- Wenn Auftrag im RBK Bereich ist: **Auftragsart W02A muss verwendet sein** – Prüfen erforderlich

## Störungen / Netzwerk
- **VTB Netz**: Noch keine Störung angelegt
- **VTE und VTV**: Funktioniert bereits
- **VTS**: Mehmet sieht im Menü nicht die Benutzerinfo

## Transportaufträge & Testphase
- **Transportaufträge**: Müssen erneut ins **KA1 transportiert** werden
- **Anschließende Tests**:
  - Zeitrückmeldung
  - LKW Rückmeldung
  - Checklisten (2 Augen und 4 Augen Prinzip)
  - Materialbuchung
  - Interaktive PDFs
  - Mobile Berichte generieren

## Nächste Schritte
- Klärung der Fehlermeldung THIELET nach Verfügbarkeit der SAP-Daten durch Carla
- **Schulungsunterlagen** (Word Dokument für Mehmet) abschließen

## Test Storno bei LKW Rückmeldung
- **LKW Rückmeldung** storno testen - VTE und VTV

## Tickets
- **KEM-239**: Storno-Button bei Zeitrückmeldung (Details → siehe notes.md)
- **KEM-XXX**: Material-Buchung Löschen-Button (Details → siehe notes.md)

---

# Protokoll – 10.02.2026

## Neue Szenarien VTI und VTF
- **Status**: Im KA1 angelegt
- **Störungserfassung**: Nicht erforderlich
- **Auftragsquelle**: Aufträge aus dem Backend, Zuordnung über Planner
- **Verteilschlüssel**: 20 oder 3 (muss angelegt werden)
- **Materialrückmeldungen**: Nicht vorgesehen
- **Selektionsvarianten**: Keine Variante für TP und EQ erforderlich
- **Rückmeldungstyp**: Nur Stundenrückmeldungen > Endrückmeldung nicht sichtbar

## Customizing & Konfiguration (VTI / VTF)
- **Auftragsart-Steuerung**: WD02
- **Leistungsarten**: ✓ Bereits erledigt
- **Mobile Tätigkeitsart**: ✓ Angepasst
- **User**: ✓ Vorhanden
- **Selektionsvariante**: ✓ Angepasst
- **Planner**: Muss noch angelegt werden

## UI-Einstellungen (Auftragsübersicht)
- **Kalender**: Kann ausgeblendet werden
- **Favoriten**: Bleiben erhalten
- **Anzeige**: Nur Aufträge und Favoriten sollen angezeigt werden
- **Bekanntes Problem**: Favoriten verschwinden bei einigen Szenarien vorher

## Backend Transport
- **Ursprünglicher Zweck**: Pfeile in den Checklisten
- **Nebeneffekt**: Führte zu einem Bug in der Zeitrückmeldung
- **Status**: Bug wurde mit den neuen Backend Transporten gefixt


---

# Protokoll ? 24.02.2026

## Offene Punkte
- Automatischer Log-Off: Aktuell keine Funktion fuer zeitgesteuerten Log-Off. Muss implementiert und mit Customizing verbunden werden, um eine feste Zeit fuer den Log-Off mit Sync festzulegen. Aufwand geschaetzt 2 Tage.
