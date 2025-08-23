# In MS-Word nutzbare Felder

> [!WARNING]
> Dies sind keine *Feldbefehle* in MS-Word: Alle "Felder" sind Fließtext in Word in der Form {Befehl}.

Felder sind Platzhalter für durch ltr eingesetzte patientenbezogene Variablen. Die Inhalte der Variablen
werden üblicherweise entweder aus der gespeicherten xml-Datei gelesen, oder in der geladenen xslt-Stylesheetdatei definiert.

Jedes Feld hat die Form "{" "Feldname" "}". Diese werden im Fließtext eingefügt (sie sind **keine** MS-Word Felder!).

Felder und deren Ersatz werden mittels der XML-Stylesheet-Dateien unter "styles/"
definiert. Weitere Felder können einfach mittels XMLS-3.0-Syntax hinzugefügt werden.

Die vordefinierten Felder sind:


## Allgemeine Felder


| Feldname     | Inhalt                                      | Kommentar                         |
|--------------|---------------------------------------------|-----------------------------------|
| {vorname}    | Vorname des Patienten                       |                                   |
| {nachname}   | Nachname des Patienten                      |                                   |
| {geburtstag} | Geburtstag des Patienten                    |                                   |
| {alter}      | Alter des Patienten in Jahren               |                                   |
| {addresse}   | Wohnort des Patienten                       |                                   |
| {arbeit}     | Beruf des Patienten                         |                                   |
| {groesse}    | Körpergröße des Patienten in cm             |                                   |
| {gewicht}    | Gewicht des Patienten in kg                 |                                   |
| {puls}       | Puls des Patienten in 1/Min.                |                                   |
| {blutdruck}  | Blutdruck des Patienten in mm/Hg            |                                   |
| {aufnahme}   | Aufnahmedatum                               |                                   |
| {entlassung} | Entlassdatum                                |                                   |
| {ekg_zeit}   | Zeitpunkt des 2. EKGs des Patienten         | Entspricht Aufnahmedatum + 7 Tage |
| {arzt}       | Nachname des behandelnden Arztes            |                                   |
| {psych}      | Nachname des behandelnden Psychotherapeuten |                                   |
| {allergien}  | Bekannte Allergien des Patienten            |                                   |



## Gender-spezifische Felder

Der Inhalt dieser Felder hängt von dem ausgewählten Geschlecht des Patienten ab (männlich/weiblich/divers)


| Feldname      | Inhalt                                                  | Kommentar |
|---------------|---------------------------------------------------------|-----------|
| {anrede}      | Herr;Frau;Herr/Frau                                     |           |
| {anrede_dat}  | Herrn;Frau;Herrn/Frau                                   |           |
| {ersie}       | er;sie;er/sie                                           |           |
| {ersie_cap}   | Er;Sie;Er/Sie                                           |           |
| {seineihre}   | seine;ihre;seine/ihre                                   |           |
| {patient}     | der Patient;die Patientin;der Patient/die Patientin     |           |
| {patient_dat} | dem Patienten;der Patientin;dem Patienten/der Patientin |           |



## Textblöcke

Ob diese Textblöcke angezeigt werden oder nicht, hängt ab, ob die entsprehenden
Diagnosen gefunden wurden.


| Feldname                | Inhalt                                                                    | Kommentar                |
|-------------------------|---------------------------------------------------------------------------|--------------------------|
| {clusterbehandlung}     | Informationen zur Basis- und Akutbehandlung                               | Nur bei G44.0            |
| {clusterneu}            | Vorgehen bei neuer Clusterepisode                                         | Nur bei G44.0            |
| {mitaura_akut}          | Akutbehandlung Migräne mit Aura                                           | Nur bei G43.1            |
| {mitund}                | Fügt "mit und " ein, wenn die Diagnose "Migräne mit Aura" besteht         | Nur bei G43.1            |
| {aura}                  | Textblock bei Diagnose "Migräne mit Aura", ansonsten "keine"              | Nur bei G43.1            |
| {anamnese_aura}         | Beschreibt Migräne mit Aura                                               | Nur bei G43.1            |
| {anamnese_status}       | Beschreibt Status migraenosus                                             | Nur bei G43.2            |
| {empf_vitb2}            | Empfehlung Vitamin B2 und Mg bei Migräne                                  | Nur bei G43.0 oder G43.1 |
| {nach_pause}            | Fügt "(Nach Medikamentenpause)" ein, wenn Diagnose "Übergebrauch" besteht | Nur bei G44.4            |
| {pause_a} und {pause_b} | Anameseblöcke für Übergebrauch                                            | Nur bei G44.4            |
| {pause_entzug}          | "Sowie der Entzugsbehandlung"                                             | Nur bei G44.4            |
| {pause_rebound}         | Information Rebound-Kopfschmerz                                           | Nur bei G44.4            |
| {pause_empfehlung}      | Fortführung Analgetikapause für 4 Wochen                                  | Nur bei G44.4            |
| {pause_def}             | Definition Übergebrauch                                                   | Nur bei G44.4            |
| {pause_abschluss}       | "Nach Abschluss der Pause"                                                | Nur bei G44.4            |
| {pause_cortison}        | Information für Pause mit und ohne Cortison                               | Nur bei G44.4            |



## Iterationsfelder

Diese Felder iterieren über einen Datensatz und fügen entsprechend Listen oder Tabellen ein


| Feldname                | Inhalt                                                                    | Kommentar                                                                       |
|-------------------------|---------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| {diagnosen}             | Liste der gefunden ICD10-Diagnosen                                        |                                                                                 |
| {vorbehandlungen}       | Kommaseparierte Liste aller Vorbehandlungen                               |                                                                                 |
| {medizinische_vorbehandlungen} | Kommaseparierte Liste medizinischer Vorbehandlungen                |                                                                                 |
| {andere_vorbehandlungen} | Kommaseparierte Liste nicht-medizinischer Behandlungen                   |                                                                                 |
| {symptome}              | Kommaseparierte Liste häufig auftretender Symptome                        |                                                                                 |
| {chronisch}             | Kommaseparierte Liste durch Schmerzen entstehender Alltagseinschränkungen |                                                                                 |
| {akutmedikation_zuvor}  | Kommaseparierte Liste der zuvor verwendeten Akutmedikamente               |                                                                                 |
| {akutmedikation_aufnahme} | Akutmedikation, die bei Aufnahme eingesetzt wurde ||
| {akutmedikation}        | Tabelle mit Akutmedikationvorschlägen                                     | Zeilen werden abhängig von Diagnosen eingefügt (s.u.)                           |
| {basismedikation_zuvor} | Kommaseparierte Liste der zuvor verwendeten Prophylaxemedikation          |                                                                                 |
| {basismedikation_aufnahme} | Basismedikation, die bei Aufnahme eingesetzt wurde ||
| {basismedikation}       | Tabelle mit gefundenen Prophylaxemedikamenten                             | Medikamentenhinweise werden abhängig von gefunden Medikamenten eingefügt (s.u.) |
| {sonstigemedikation}    | Tabelle mit gefundener nicht-schmerztherapeutischer Medikation            |                                                                                 |



## Score-Felder

Diese Felder lesen in Formularen eingegebene Daten aus und fügen entsprechend Textblöcke ein


| Feldname | Inhalt       | Kommentar                                                                               |
|----------|--------------|-----------------------------------------------------------------------------------------|
| {midas}  | Midas-Score  | Definiert selbstständig die Schwere der Beeinträchtigung. Lässt Zeilen mit 0-Werten aus |
| {whodas} | Whodas-Score | Lässt Zeilen mit 0-Werten aus                                                           |
| {bdi_ii} | BDI-II Score | Lässt normwertige Felder aus                                                            |



# Tabellenformate


## Akutmedikation

Tabellenzeilen des {akutmedikation}-Befehles werden abhängig von gefundenen ICD10-Diagnosen eignefügt. Bekannte Diagnosen sind:

- Medikamentenübergebrauch
- Migräne (mit und) ohne Aura
- Status Migraenosus
- Clusterkopfschmerz
- Kopfschmerz vom Spannungstyp

## Basismedikation

Je nach gefundenen Medikamenten werden im Rahmen des {basismedikation}-Befehles Listenpunkte als Information für den Patienten eingefügt.
Bekannte Medikamente sind:

- CGRP-Antikörper (Erenumab, Fremanezumab, Galcanezumab)
- Venlafaxin
- Trizyklika (Amitriptylin, Trimipramin, Doxepin)
- Etoricoxib
- Duloxetin
- Escitalopram
- Mirtazapin
- Opipramol
- Pregabalin
- Topiramat
- Candesartan
- Blutdruckmedikation (Bisoprolol, Metoprolol, Amlodipin)
- Magnesium und Vitamin B2
- Sertralin
- Clomipramin
- Carbamazepin
- Gabapentin
- Tizanidin
- Flunarizin
- Atosil/Promethazin
- Lamotrigin
- Opioide (Tramal, Tilidin, Oxycodon, Tapentadol, MST)

Weiterhin wird bei der Diagnose "chronische Migräne" ein Hinweis auf Botox sowie Atogepant eingefügt.
