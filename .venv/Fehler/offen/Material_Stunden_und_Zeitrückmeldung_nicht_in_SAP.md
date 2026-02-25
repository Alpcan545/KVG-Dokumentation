# Fehler: Material- und Stundenbuchung kommt nicht in SAP an

## Meldung
Der Kollege **Hinrichs-Stark Calvin** meldet folgenden Vorfall:

- Material und Stunden wurden in Oxando gebucht.
- In SAP kommt die Buchung nicht an.
- Eine Synchronisation wurde durchgeführt.
- Im Connector ist kein Fehler sichtbar.
- Zusätzlich ist die Buchung in Oxando lokal nicht sichtbar („bei mir auf Oxando sehe ich es auch nicht“).

## Aktueller Stand
- Problem ist reproduziert/meldbar laut Support-Hinweis.
- Keine Fehlermeldung im Connector vorhanden.
- Datenfluss Oxando -> SAP scheint unvollständig oder inkonsistent.

- Trace für User im PA1 aktiviert
- SAP Daten angefordert

## Betroffene Person
- Calvin Hinrichs-Stark
- User: HINRICHS-SAC

## Hinweise aus der Meldung
- Screenshot aus Oxando-Auftrag wurde mitgeliefert.
- Es handelt sich um eine Buchung von Material und Arbeitsstunden.

## Nächste Schritte
- [x] Buchung im betroffenen Auftrag in Oxando direkt prüfen (Existenz, Status, Zeitstempel).
- [ ] Sync-Log für den betroffenen Zeitraum prüfen.
- [ ] SAP-Eingang auf Filter/Fehler in der Zielbuchung prüfen.
- [ ] Connector-Protokolle trotz „kein Fehler“ auf Warnungen prüfen.
- [ ] Ergebnis und Ursache dokumentieren.

