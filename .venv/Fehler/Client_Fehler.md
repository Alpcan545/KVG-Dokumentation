# Client Fehler - Oxando XPC

## 1. SQLite Error 5: "database is locked" - 28.01.2026

### Symptome
- Fehlermeldung: **SQLite Error 5: 'database is locked'**
- Fehler tritt beim Laden der Aufträge auf
- Betrifft die Login/Sync-Prozesse der Anwendung

### Kontext
- **Datum**: 28.01.2026
- **Auftragsart**: WS02
- **Auftragsnummer**: 30138490
- **Equipment**: ZUB-CTSM422 - Magnetische Fahrsperre CTSM Fzg. 422
- **Status**: Test aktiv

### Stack Trace
```
at Microsoft.Data.Sqlite.SqliteException.ThrowExceptionForRC(Int32 rc, sqlite3 db)
at Microsoft.Data.Sqlite.SqliteDataReader.NextResult()
at Microsoft.Data.Sqlite.SqliteCommand.ExecuteReader(CommandBehavior behavior)
at Microsoft.Data.Sqlite.SqliteCommand.ExecuteNonQuery()
at Microsoft.EntityFrameworkCore.Storage.RelationalCommand.ExecuteNonQuery(RelationalCommandParameterObject parameterObject)
at Microsoft.EntityFrameworkCore.RelationalDatabaseFacadeExtensions.ExecuteSqlRaw(DatabaseFacade databaseFacade, String sql, IEnumerable`1 parameters)
at OxandoXPC.Applications.Services.SyncProcessService.DoSyncProcess(Boolean initSyncHappened, Boolean isInitSync)
at OxandoXPC.Applications.Pages.ModalPages.LoginPage.LoginPageModel.FinishLoginProcess(Boolean initSyncHappened)
at OxandoXPC.Applications.Helpers.MainThreadHelper.<>c__DisplayClass4_0.<<CheckAndBeginInvokeOnMainThreadAsync>b__0>d.MoveNext()
--- End of stack trace from previous location ---
at System.Threading.Tasks.Task.<>c.<ThrowAsync>b__128_0(Object state)
at Microsoft.UI.Dispatching.DispatcherQueueSynchronizationContext.<>c__DisplayClass2_0.<Post>b__0()
```

### Mögliche Ursachen
- **Datenbank-Lock**: Die SQLite-Datenbank wird bereits von einem anderen Prozess/Thread verwendet
- **Sync-Konflikt**: Mehrere gleichzeitige Sync-Vorgänge könnten auf die Datenbank zugreifen
- **Nicht geschlossene Verbindungen**: Offene Datenbankverbindungen aus vorherigen Operationen

### Betroffene Komponenten
- `Microsoft.Data.Sqlite`
- `Microsoft.EntityFrameworkCore`
- `OxandoXPC.Applications.Services.SyncProcessService`
- `LoginPageModel.FinishLoginProcess`

### Screenshot

### Status
- **Offen**
- Weitere Analyse erforderlich
- Prüfen ob das Problem nach Systemspiegelung (26.-28.01.2026) noch auftritt

### Nächste Schritte
- Reproduzierbarkeit prüfen
- Datenbankzugriffe während Sync-Prozess analysieren
- Prüfen ob mehrere parallele Datenbankzugriffe stattfinden
- Connection-Handling im SyncProcessService überprüfen

---

## 2. Erweiterte Suche funktioniert nicht - iOS - 29.01.2026

### Symptome
- **Erweiterte Suche** funktioniert nicht im iOS-Gerät
- Betroffene Plattform: **iOS**
- Funktion ist nicht erreichbar oder gibt keine Ergebnisse zurück

### Kontext
- **Datum**: 29.01.2026
- **Plattform**: iOS (Mobile)
- **Version**: Maui 1.0.14454.1 / iOS 1.0.78
- **Szenario**: VTS (getestet im VTS-Szenario)

### Schritte zum Reproduzieren
1. Home Page öffnen
2. Auf **"AUFTRAG"** klicken
3. In die **Auftrags-Liste** navigieren
4. Oben auf das **Lupe-Symbol** (Suche) klicken
5. Auf **"Erweiterte Suche"** klicken
6. **Button reagiert nicht** - Erweiterte Suche öffnet sich nicht

### Fehlerbeschreibung
- Der Button für "Erweiterte Suche" ist **nicht funktional**
- Es gibt **keine Fehlermeldung**, der Button antwortet einfach nicht auf Klicks
- Die erweiterte Suche kann daher nicht verwendet werden
- **Funktioniert weder vertikal noch horizontal ** - Problem tritt in beiden Orientierungen auf

### Screenshot
![alt text](Screenshots/iOSerweiterteSuche_Fehler.jpg)

### Status
- **✅ Erledigt**
- Problem wurde nach Customizing-Verteilung behoben
- Erweiterte Suche funktioniert wieder korrekt

### Nächste Schritte
- ~~Reproduzierbare Schritte ermitteln~~
- ~~Logs vom iOS-Gerät sammeln~~
- ~~Überprüfen der Suche-Implementierung in XAML/Code-Behind (iOS-spezifisch)~~
- Problem gelöst durch Customizing-Verteilung

---

## ==3. List Navigation funktioniert nicht wie im Customizing - 29.01.2026==

### Symptome
- **List Navigation** funktioniert nicht mehr gemäß Customizing-Einstellungen
- Navigation-Logik wird nicht korrekt angewendet

### Erwartetes Verhalten (Customizing)
- **0 Einträge**: Navigation soll auf das **Anlegen** gehen
- **1 oder mehrere Einträge**: Navigation soll auf die **Liste** gehen

### Aktuelles Verhalten
- Navigation funktioniert nicht entsprechend der Customizing-Konfiguration
- Falsche Navigation wird angezeigt

### Kontext
- **Datum**: 29.01.2026
- **Version**: Maui 1.0.14454.1 / iOS 1.0.78
- **Betroffener Bereich**: List Navigation Logik

### Screenshot
![alt text](Screenshots/SQLLiteError5.png)

### Status
- **Offen**
- Bug in der aktuellen Version

### Nächste Schritte
- Customizing-Einstellungen im System überprüfen
- Navigation-Logik im Code analysieren
- Reproduzierbare Testfälle erstellen (0 Einträge vs. 1+ Einträge)
- Regression testen (in welcher Version funktionierte es zuletzt?)
- Fix implementieren und testen

---

## 4. Übersetzungsfehler in Checkliste - VTR - 29.01.2026

### Symptome
- **Übersetzungsfehler** in der Prüfer-Auswahl
- Titel erscheint auf **Englisch** statt Deutsch: **"Assign Reviewer"**
- Sollte auf Deutsch lauten: **"Prüfer zuweisen"** oder **"Auswahl Prüfer"**

### Kontext
- **Datum**: 29.01.2026
- **Szenario**: VTR (Checkliste)
- **Betroffener Bereich**: Prüfmerkmal schließen → Auswahl Prüfer
- **Anzeige**: Dialog-Titel zeigt "Assign Reviewer" statt deutscher Übersetzung

### Schritte zum Reproduzieren
1. VTR Szenario öffnen
2. Checkliste aufrufen
3. Prüfmerkmal schließen
4. Dialog "Auswahl Prüfer" erscheint mit englischem Titel

### Screenshot
![alt text](Screenshots/Checkliste_AssignReviewer.png)

### Status
- **Offen**
- Übersetzungsfehler (Lokalisierung)

### Nächste Schritte
- Resource-Datei für Lokalisierung prüfen (de-DE)
- "Assign Reviewer" durch deutsche Übersetzung ersetzen
- Alle weiteren englischen Strings im VTR-Bereich überprüfen
- Testen mit deutscher Sprache
