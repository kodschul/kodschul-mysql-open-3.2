# Lösungen zu den Übungen

## Übung 1: Kontakte einfügen

```sql
INSERT INTO Kontakte (Vorname, Nachname, Firma, EMail)
VALUES ('Anna', 'Schmidt', 'Beispiel GmbH', 'anna.schmidt@example.com');

INSERT INTO Kontakte (Vorname, Nachname, EMail)
VALUES ('Tom', 'Müller', 'tom.mueller@example.com'); -- Ohne Firma

INSERT INTO Kontakte (Vorname, Nachname, Firma, EMail, Aktiv)
VALUES ('Laura', 'Fischer', 'Fischer AG', 'laura.fischer@example.com', FALSE); -- Aktiv = FALSE
```

## Übung 2: Produkte einfügen

```sql
INSERT INTO Produkte (Name, Preis)
VALUES ('USB-Stick', 9.99);

INSERT INTO Produkte (Name, Beschreibung, Preis)
VALUES ('Kabellose Maus', 'Optische Maus, kabellos mit USB-Empfänger', 19.99);

INSERT INTO Produkte (Name, Beschreibung, Preis)
VALUES ('Mechanische Tastatur', 'RGB-Beleuchtung, mechanische Switches', 49.99);

INSERT INTO Produkte (Name, Preis, Verfügbar)
VALUES ('Webcam', 29.99, FALSE); -- Nicht verfügbar
```

## Übung 3: Tests & Fragen

### Versuch ohne Vorname:

```sql
INSERT INTO Kontakte (Nachname, EMail)
VALUES ('Weber', 'weber@example.com');
-- Fehler: NOT NULL Constraint verletzt
```

### Versuch mit doppelter E-Mail:

```sql
INSERT INTO Kontakte (Vorname, Nachname, EMail)
VALUES ('Markus', 'Becker', 'anna.schmidt@example.com');
-- Fehler: UNIQUE Constraint verletzt
```

### Versuch mit negativem Preis:

```sql
INSERT INTO Produkte (Name, Preis)
VALUES ('Fehlerprodukt', -10.00);
-- Technisch möglich, aber fachlich unsinnig. Ein Constraint könnte solche Fälle verhindern.