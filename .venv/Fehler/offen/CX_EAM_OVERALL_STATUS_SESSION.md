# Fehlerbild: `CX_EAM_OVERALL_STATUS_SESSION`

Der Hinweis sagt:

Die Meldung arbeitet mit dem Phasenmodell – der Auftrag aber nicht.
Diese Inkonsistenz verursacht den Dump.


## Kurzbeschreibung
- Betroffene Transaktion: `IW48` (mehrfache Rückmeldungen für Instandhaltungsaufträge)
- Typisches Symptom: ABAP-Dump mit Runtime Error `ITAB_LINE_NOT_FOUND`
- Exception-Klasse im Dump: `CX_EAM_OVERALL_STATUS_SESSION`
- Häufig genannter Programmkontext: `SAPLEAM_ORD_RTPP`

## Gesicherte SAP-Hinweise (offizielle Quellen)
- KBA `3614744`: beschreibt genau den Dump in `IW48` mit `ITAB_LINE_NOT_FOUND` und `CX_EAM_OVERALL_STATUS_SESSION`.
- KBA `3661052`: ähnliches Fehlerbild (gleiche Exception-Klasse) auch in `IW31`.
- Mehrere KBAs zum Phase-Model-/Statusprofil-Kontext nennen Restriktionen und Abhängigkeiten (u. a. Hinweis auf SAP Note `3365558`), z. B. `3417916`, `3209695`, `3153342`, `3355676`.
- SAP-Dokumentation/Enablement beschreibt, dass Overall-Statusprofile im Phase-Model-Kontext sauber zugeordnet sein müssen (inkl. Einschränkungen bei Standardprofilen und Empfehlung, mit Kopien zu arbeiten).


## Wahrscheinliche technische Ursache (Ableitung)
Die Exception deutet auf eine Inkonsistenz in der EAM-Statuslogik hin: Beim Lesen von Phasen-/Overall-Statusinformationen fehlt ein erwarteter Eintrag (daher `ITAB_LINE_NOT_FOUND`). 
Das passt zu Konstellationen, in denen:

- Phase Model aktiv ist, aber Statusprofil-Zuordnung unvollständig oder inkonsistent ist.
- kundeneigene Anpassungen am Overall Status Profile nicht zu den erwarteten Phasen-/Statusübergängen passen.
- Systemstand/Corrections noch nicht alle bekannten Korrekturen für die Status-Session enthält.

## Prüfschritte (technisch/fachlich)
1. In `ST22` den konkreten Dump prüfen (Zeitpunkt, Auftragsart, betroffener User, Include/Methodenpfad).
2. Prüfen, ob für die betroffene Auftragsart das Phase Model aktiv ist.
3. Zuordnung Auftragsart ↔ Overall Status Profile verifizieren (insb. bei kundeneigenen Profilen).
4. Prüfen, ob ein Standardprofil direkt geändert wurde oder eine Kopie verwendet wird.
5. Status-/Phasenkonsistenz im betroffenen Auftrag validieren (Header- vs. Vorgangsstatus; bekannte Meldungen `M7069`/`M7070` als Indikator).
6. Relevante SAP-Korrekturhinweise/Support-Package-Stand gegen KBAs abgleichen.

## Empfohlene Maßnahmen
1. KBA `3614744` als Primärreferenz für das konkrete Fehlerbild verwenden.
2. Customizing für Phase Model + Overall Status Profile in QA systematisch gegenprüfen.
3. Falls reproduzierbar: SAP-Incident mit Dump-Details, Auftragsart, Systemstand und Customizing-Screens eröffnen.
4. Nach Korrekturtransport Regression testen (`IW48`, `IW31`, ggf. Fiori-Auftragsapps).


## Quellen
- SAP KBA 3614744 (Symptom/Primary Match): https://userapps.support.sap.com/sap/support/knowledge/en/3614744
- SAP KBA 3661052 (ähnliche Exception in IW31): https://userapps.support.sap.com/sap/support/knowledge/en/3661052
- SAP KBA 3417916 (Phase Model / Statusprofil-Restriktionen): https://userapps.support.sap.com/sap/support/knowledge/en/3417916
- SAP KBA 3209695 (Aktivierungskontext/fehlende Konfigurationsknoten): https://userapps.support.sap.com/sap/support/knowledge/en/3209695
- SAP KBA 3153342 (Status-/Phasenmeldungen M7069, M7070): https://userapps.support.sap.com/sap/support/knowledge/en/3153342
- SAP KBA 3355676 (Phasenstatus-Verhalten): https://userapps.support.sap.com/sap/support/knowledge/en/3355676
- SAP Learning Journey (Overall Status Profiles konfigurieren): https://learning.sap.com/learning-journeys/configuring-sap-s-4hana-cloud-public-edition-assets-and-service-management/configuring-the-phase-based-maintenance-process
- SAP Blog/Release Context zu Phase Model & Overall Status Profiles: https://community.sap.com/t5/enterprise-resource-planning-blog-posts-by-sap/sap-s-4hana-cloud-for-eam-what-s-new-in-release-2208/ba-p/13574005


## Lösungsvorschlag:
- Items muss die dazugehörige SNOTE einpflegen
- Vermutlich größerer Aufwand wegen einer exception - unabhängig von Oxando
