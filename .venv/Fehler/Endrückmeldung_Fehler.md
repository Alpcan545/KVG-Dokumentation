# Fehler beim Verbuchen – Reihenfolge der Prozesse

## Fehlerbeschreibung
Beim Verbuchen von Rückmeldungen werden nicht alle Informationen ins SAP-System transportiert, wenn die **Endrückmeldung vorab gesetzt** ist und der **Langtext nachträglich geändert** wird.

---

Szenario VTS

## Ablauf (aktuell – fehlerhaft)

1. **Zeitrückmeldung anlegen**
2. **Endrückmeldung** sofort setzen / vermerken
3. **Speichern**
5. **Langtext** der Rückmeldung verändert (nachträglich)
6. **Sync**
7. Transport ins SAP-System → ⚠️ **Informationen gehen verloren**

### Problem
Die Daten werden verbucht, bevor der Langtext vollständig transportiert ist. Falls die Endrückmeldung bereits gesetzt ist, werden Textänderungen möglicherweise **nicht mitgenommen** oder **überschrieben**.

Aktuell kommt es vor, dass die Reihenfolge der Verbuchung umgekerhrt ist, dann ist aber die Materialbuchung aufrund Des Abschlusses nicht mehr möglich ist 
---

## Ablauf (korrekt – gewünscht)

1. **Zeitrückmeldung anlegen**
2. **Langtext** vollständig eingeben/transportieren
3. **Endrückmeldung** setzen
4. Alle Daten konsistent ins SAP-System verbuchen → ✓ **Alle Informationen übertragen**

---

## Ursachenanalyse
- **Abhängigkeit**: Die Endrückmeldung triggert möglicherweise einen vorzeitigen Transport/Validierungsprozess, der den (noch fehlenden) Langtext nicht berücksichtigt.
- **Datenintegrität**: Nur wenn Langtext vor Endrückmeldung vollständig vorliegt, werden alle Felder korrekt verbucht.

---

## Lösungsvorschläge

### 1. **Prozess-Steuerung** (bevorzugt)
- Endrückmeldung-Flag erst setzen, nachdem Langtext vollständig eingegeben und validiert wurde.
- Prüfung: Vor dem Transport der Endrückmeldung prüfen, ob alle Text-Felder gefüllt sind.

### 2. **Code-Logik überprüfen**
- Transport-Reihenfolge in der Applikation: Sicherstellen, dass Langtext **vor** der Endrückmeldung verbucht wird.
- Ggf. Batch-Prozess/Transaction so strukturieren: erst Text-Update, dann Flag-Update.

### 3. **Validierung stärken**
- Vor dem Verbuchen prüfen: Alle erforderlichen Textfelder sind gefüllt?
- Fehlermeldung werfen, wenn Endrückmeldung ohne kompletten Langtext gesetzt werden soll.

---

## Nächste Schritte
- [ ] Code-Review: Ablauf beim Verbuchen (Transport-Reihenfolge) überprüfen
- [ ] Test: Rückmeldung mit Langtext **vor** Endrückmeldung verbuchen → Ergebnis prüfen
- [ ] Test: Rückmeldung mit Langtext **nach** Endrückmeldung verbuchen → Fehler reproduzieren
- [ ] Fix umsetzen (je nach Ursache aus Punkt 1 oder 2)
- [ ] Regressionstests durchführen


