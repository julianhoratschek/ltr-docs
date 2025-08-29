# Formulare

## Formulartab erstellen

Formulartabs können mittles toml-Format erstellt werden. Eine automatische Integration der Daten des Formulares erfolgt in die exportierte xml-Datei. Sobald eine Datei exportiert wurde, wird versucht, die Formulare bei erneutem Laden der Patientendaten aus der zugehörigen xml zu laden.

Ein Beispiel für ein Formular kann [hier](bdi2.toml) eingesehen werden.
Pro Formular muss eine neue toml-Datei erstellt werden, ein Formular kann
jedoch mehrere Felder enthalten.


## Auf exportierte Formulardaten zugreifen

Formulare werden in der Patienten-xml in folgendem Format exportiert:

```xml
<field name="field_id">
    <value>Value 1</value>
    <value>Value 2</value>
    ...
</field>
```

Da die Patienten-xml automatisch für die xslt-Stylesheet-Datei geladen wird, kann auf die Daten mittels

```xml
<xsl:value-of select="$data//field[@name='field_id']/value"/>
```

zugegriffen werden.


## Formular-Definition

Formulare werden im toml-Format erstellt. Jedes Formular benötigt einen Namen,
der als Tab-Überschrift angezeigt wird. Ein "&" vor einem Buchstaben in dem Namen
erstellt automatisch einen Shortcut ([Alt] + [Buchstabe]), um das Formular
aufzurufen:

```toml
name = "&Neues Formular"    # Erstellt Shortcut [Alt] + [N]
```

Jedes Formular kann mehrere Felder beinhalten. Die Felder stellen die Dateneingabe
für das Formular dar. Felder werden - je nach Typ - verschieden definiert.

Die grundlegende Definition eines Feldes erfolgt mit:

```toml
[[field]]
caption = "Überschrift des Feldes"
id = "eindeutige_id"
field_type = "feld_typ"     # Siehe unten
```

Anschließend müssen für einige Feld-Typen Inhalte zur Auswahl definiert werden.


## Feld-Definition

### xbox

Stellt ein Feld aus Auswahlboxen dar. Eine Mehrfachauswahl ist möglich.

```toml
[[field]]
caption = "Hauptstädte"
id = "capitals"
field_type = "xbox"
rows = 5               # Maximal 5 Auswahlboxen werden pro Spalte angezeigt
values = [
    "Kiel", "Schwerin", "Hamburg", "Hannover", "Potsdam", "Magdeburg", "Düsseldorf", "Erfurt", "Dresden", "Wiesbaden", "Mainz", "Saarbrücken", "Stuttgart", "München", "Berlin*"
]
```

Enthält eine der Optionen ein Stern (\*), so wird diese Option - auch wenn sie ausgewählt wird - nicht übernommen (Im Beispiel: Berlin).

Die Felder können vom Benutzer entweder per Maus oder per Tastaturfokus angesteuert werden.
Durch die Taste "x" kann das aktuelle Feld ausgewählt werden, durch die Taste "y" kann
das aktuelle Feld ab- (oder nicht-aus-) gewählt werden. Auch Tab/Shift Tab oder die Pfeiltasten zum springen
zwischen den Feldern kann verwendet werden.

Jedes xbox-Feld wird mit einem Button zur Umkehr der gesamten Auswahl generiert.

### split_line

Stellt eine Eingabefläche für Zahlen dar. Die Zahlen können durch nicht-numerische
Zeichen getrennt werden, wird kein Trennzeichen gefunden, werden die einzelnen
Ziffern der Eingabe als einzelne Zahlen gewertet (z.B. 35123 -> 3, 5, 1, 2, 3).

```toml
[[field]]
caption = "Meine Liebglingszahlen"
id = "fav_numbers"
field_type = "split_line"
max_entries = 10            # Weitere Eingaben werden ignoriert
```


Werden nicht genügend Einträge durch den Benutzer gestellt, werden die fehlenden
Einträge durch 0 aufgefüllt.


### eval_line

Stellt den komplexesten Feldtypen dar. Erfordert die Eingabe von Zahlen, die
jeweils für einen Wert eines Postens stehen.

```toml
[[field]]
caption = "Menüauswahl"
id = "food_menu"
field_type = "eval_line"
start = 1                   # Der Benutzer gibt als niedrigsten Wert "1" ein, hier wird aber mit 0 begonnen

# Erster Posten: z.B. Vorspeise
[[field.values]]
0 = "Tagessuppe"
1 = "Carpaccio"
2 = "Bruschetta"

# Zweiter Posten: z.B. Hauptgang
[[field.values]]
0 = "Steak mit Ofenkartoffel"
1 = "Fisch des Tages"
2 = "Ravioli"

# Dritter Posten: z.B. Nachtisch
[[field.values]]
0 = "Eisvariation"
1 = "Creme Brulee"
2 = "Käseselektion"
```

Die Benutzereingabe "231" würde in diesem Beispiel der Auswahl:

"Carpaccio", "Ravioli", "Eisvariation"

entsprechen. Allen Ziffern des Benutzers muss in diesem Beispiel 1 abgezogen
werden, da die Option "start = 1" gesetzt wurde.
