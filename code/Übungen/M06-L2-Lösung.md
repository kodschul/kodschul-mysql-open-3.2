# Lösungen zu den Übungen

## Übung 1: Aktualisierungen

```sql
-- E-Mail Adresse für Kontakt Müller aktualisieren
UPDATE Kontakte SET EMail = 'mueller@beispiel.de' WHERE Nachname = 'Müller';

-- Preis auf 0 setzen für nicht verfügbare Produkte
UPDATE Produkte SET Preis = 0.00 WHERE Verfügbar = FALSE;

-- Firmenname auf 'Privatkunde' setzen, wenn leer
UPDATE Kontakte SET Firma = 'Privatkunde' WHERE Firma IS NULL;
```

## Übung 2: Aktualisierungen

```sql
-- Preise unter 0 auf NULL setzen
UPDATE Produkte SET Preis = NULL WHERE Preis < 0;

-- Ungültige E-Mail-Adressen korrigieren
UPDATE Kontakte SET EMail = 'ungültig@example.com' WHERE EMail NOT LIKE '%@%';

-- Kontakte mit Nachnamen 'Mustermann' deaktivieren
UPDATE Kontakte SET Aktiv = FALSE WHERE Nachname = 'Mustermann';
```

## Übung 3: Änderungen & Aktualisierungen

```sql
-- Neue Spalte 'GeaendertAm' hinzufügen
ALTER TABLE Produkte ADD COLUMN GeaendertAm TIMESTAMP;

-- Verfügbarkeit für Produkte vom März 2024 deaktivieren
UPDATE Produkte SET Verfügbar = FALSE WHERE EingestelltAm LIKE '2024-03%';

-- Preise um 5% erhöhen für Produkte mit 'Buch' im Namen
UPDATE Produkte SET Preis = Preis * 1.05 WHERE Name LIKE '%Buch%';