# Basiskonfiguration

## Aufsuchen von config.toml

- Konfiguration erfolgt über die Datei config.toml
- ltr sucht zunächst im Verzeichnis [Benutzerpfad]/.ltr/config.toml
- Pfade in den Dateien werden relativ zu der config.toml, aus der sie gelesen werden, gehandhabt
- Windows Umgebungsvariablen (z.B. "%USERPROFILE%") werden in Pfaden expandiert
- Falls dort keine Datei gefunden wird, sucht ltr im Verzeichnis, in dem
  die ausgeführte ltr.exe liegt nach config.toml

## Aufbau config.toml

- In der standard [config.toml](config.toml) finden sich alle unterstützten Schlüssel mit
  Erklärung
