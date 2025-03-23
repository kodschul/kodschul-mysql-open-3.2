## Modul 8: Primär- und Sekundär-Schlüssel

### Lab 8.2: Erstellung und Verwaltung von Schlüsseln

#### Tabelle `Kunden`
```sql
CREATE TABLE Kunden (
  KundenID INT PRIMARY KEY,
  Name VARCHAR(100)
);
```

#### Tabelle `Bestellpositionen`
```sql
CREATE TABLE Bestellpositionen (
  BestellID INT,
  ProduktID INT,
  PRIMARY KEY (BestellID, ProduktID)
);
```

#### Primärschlüssel nachträglich hinzufügen
```sql
ALTER TABLE Kunden ADD PRIMARY KEY (KundenID);
```

#### Tabelle `Bestellungen` mit Fremdschlüssel
```sql
CREATE TABLE Bestellungen (
  BestellungID INT PRIMARY KEY,
  KundenID INT,
  FOREIGN KEY (KundenID) REFERENCES Kunden(KundenID)
);
```

#### Fremdschlüssel nachträglich hinzufügen
```sql
ALTER TABLE Bestellungen ADD CONSTRAINT fk_kunde
FOREIGN KEY (KundenID) REFERENCES Kunden(KundenID);
```

#### Tabelle `Benutzer` mit UNIQUE-Schlüssel
```sql
CREATE TABLE Benutzer (
  BenutzerID INT PRIMARY KEY,
  Email VARCHAR(100)
);

ALTER TABLE Benutzer ADD UNIQUE (Email);
```

#### Schlüssel entfernen
```sql
-- Primärschlüssel entfernen
ALTER TABLE Kunden DROP PRIMARY KEY;

-- Fremdschlüssel entfernen
ALTER TABLE Bestellungen DROP FOREIGN KEY fk_kunde;

-- UNIQUE-Schlüssel entfernen
ALTER TABLE Benutzer DROP INDEX Email;
```

### Lab 8.3: Referenzielle Integrität und Schlüsselverwaltung

#### Referenzielle Integrität definieren
```sql
ALTER TABLE Bestellungen ADD FOREIGN KEY (KundenID) REFERENCES Kunden(KundenID);
```

#### Verstoß gegen referenzielle Integrität
```sql
INSERT INTO Bestellungen (BestellungID, KundenID) VALUES (101, 9999); -- Fehler, KundenID existiert nicht
```

#### ON DELETE CASCADE
```sql
ALTER TABLE Bestellungen ADD FOREIGN KEY (KundenID) REFERENCES Kunden(KundenID)
ON DELETE CASCADE;
```

#### ON DELETE SET NULL
```sql
CREATE TABLE Abteilungen (
  AbteilungsID INT PRIMARY KEY
);

CREATE TABLE Mitarbeiter (
  MitarbeiterID INT PRIMARY KEY,
  AbteilungsID INT,
  FOREIGN KEY (AbteilungsID) REFERENCES Abteilungen(AbteilungsID)
  ON DELETE SET NULL
);
```

## Modul 9: Tabellen verbinden – Einführung in JOINS

### Lab 9.1: INNER JOIN, LEFT JOIN & RIGHT JOIN

#### INNER JOIN
```sql
SELECT Kunden.Name, Bestellungen.Bestelldatum
FROM Kunden
INNER JOIN Bestellungen ON Kunden.KundenID = Bestellungen.KundenID;
```

#### LEFT JOIN
```sql
SELECT Kunden.Name, Bestellungen.Bestelldatum
FROM Kunden
LEFT JOIN Bestellungen ON Kunden.KundenID = Bestellungen.KundenID;
```

#### RIGHT JOIN
```sql
SELECT Kunden.Name, Bestellungen.Bestelldatum
FROM Kunden
RIGHT JOIN Bestellungen ON Kunden.KundenID = Bestellungen.KundenID;
```

#### JOIN mit zusätzlichen Bedingungen
```sql
SELECT Kunden.Name, Bestellungen.Bestelldatum, Bestellungen.Preis
FROM Kunden
INNER JOIN Bestellungen ON Kunden.KundenID = Bestellungen.KundenID
WHERE Bestellungen.Preis > 50;
```

### Lab 9.2: JOINs über mehrere Tabellen hinweg

#### Tabellen für mehrstufige JOINs
```sql
SELECT K.Name, B.Bestelldatum, P.Produktname, BP.Menge
FROM Kunden K
INNER JOIN Bestellungen B ON K.KundenID = B.KundenID
INNER JOIN Bestellpositionen BP ON B.BestellungID = BP.BestellungID
INNER JOIN Produkte P ON BP.ProduktID = P.ProduktID;
```

### Lab 9.3: Verwendung von Primär- und Fremdschlüsseln in JOINs

#### JOIN mit Primär- und Fremdschlüssel
```sql
SELECT Kunden.Name, Bestellungen.Bestelldatum
FROM Kunden
INNER JOIN Bestellungen ON Kunden.KundenID = Bestellungen.KundenID;
```

#### Mehrstufiger JOIN
```sql
SELECT K.Name, P.Produktname, BP.Menge
FROM Kunden K
INNER JOIN Bestellungen B ON K.KundenID = B.KundenID
INNER JOIN Bestellpositionen BP ON B.BestellungID = BP.BestellungID
INNER JOIN Produkte P ON BP.ProduktID = P.ProduktID;
```

#### LEFT JOIN – Studenten mit und ohne Kurs

```sql
CREATE TABLE Studenten (
  StudentID INT PRIMARY KEY,
  Name VARCHAR(100)
);

CREATE TABLE Kurse (
  KursID INT PRIMARY KEY,
  Titel VARCHAR(100)
);

CREATE TABLE Teilnahmen (
  StudentID INT,
  KursID INT,
  PRIMARY KEY (StudentID, KursID),
  FOREIGN KEY (StudentID) REFERENCES Studenten(StudentID),
  FOREIGN KEY (KursID) REFERENCES Kurse(KursID)
);

SELECT Studenten.Name, Kurse.Titel
FROM Studenten
LEFT JOIN Teilnahmen ON Studenten.StudentID = Teilnahmen.StudentID
LEFT JOIN Kurse ON Teilnahmen.KursID = Kurse.KursID;
```