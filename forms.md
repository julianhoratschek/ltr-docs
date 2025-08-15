# Formulare

## Formulartab erstellen

Formulartabs können mittles toml-Format erstellt werden. Eine automatische Integration der Daten des Formulares erfolgt in die exportierte xml-Datei. Sobald eine Datei exportier wurde, wird versucht, die Formulare bei erneutem Laden der Patientendaten aus der zugehörigen xml zu laden.


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