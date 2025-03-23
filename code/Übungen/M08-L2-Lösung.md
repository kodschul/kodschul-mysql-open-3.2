## Gegebene Tabellen erstellen

```sql
CREATE TABLE Abteilungen (
  AbteilungID INT,
  Name VARCHAR(100)
);

CREATE TABLE Mitarbeiter (
  MitarbeiterID INT,
  Name VARCHAR(100),
  AbteilungID INT
);
```

## Übung: Tabellenänderungen und Constraints

```sql
-- Primärschlüssel für Tabelle Abteilungen setzen
ALTER TABLE Abteilungen ADD PRIMARY KEY (AbteilungID);

-- Primärschlüssel für Tabelle Mitarbeiter setzen
ALTER TABLE Mitarbeiter ADD PRIMARY KEY (MitarbeiterID);

-- Fremdschlüssel in Mitarbeiter auf Abteilungen setzen
ALTER TABLE Mitarbeiter
ADD FOREIGN KEY (AbteilungID) REFERENCES Abteilungen(AbteilungID);

-- Name in Abteilungen eindeutig setzen
ALTER TABLE Abteilungen ADD UNIQUE (Name);
```
