# Codebeispiele – Modul 8: Primär- und Sekundär-Schlüssel

## Lab 8.2: Erstellung und Verwaltung von Schlüsseln

**Einfacher Primärschlüssel bei Tabellenerstellung**
```sql
CREATE TABLE Kunden (
  KundenID INT PRIMARY KEY,
  Name VARCHAR(100)
);
```

**Zusammengesetzter Primärschlüssel**
```sql
CREATE TABLE Bestellpositionen (
  BestellID INT,
  ProduktID INT,
  PRIMARY KEY (BestellID, ProduktID)
);
```

**Primärschlüssel nachträglich hinzufügen**
```sql
ALTER TABLE Kunden ADD PRIMARY KEY (KundenID);
```

**Fremdschlüssel bei Tabellenerstellung**
```sql
CREATE TABLE Bestellungen (
  BestellungID INT PRIMARY KEY,
  KundenID INT,
  FOREIGN KEY (KundenID) REFERENCES Kunden(KundenID)
);
```

**Fremdschlüssel nachträglich hinzufügen**
```sql
ALTER TABLE Bestellungen ADD CONSTRAINT fk_kunde
FOREIGN KEY (KundenID) REFERENCES Kunden(KundenID);
```

**UNIQUE-Schlüssel definieren**
```sql
ALTER TABLE Benutzer ADD UNIQUE (Email);
```

**Primärschlüssel entfernen**
```sql
ALTER TABLE Kunden DROP PRIMARY KEY;
```

**Fremdschlüssel entfernen**
```sql
ALTER TABLE Bestellungen DROP FOREIGN KEY fk_kunde;
```

**UNIQUE-Schlüssel entfernen**
```sql
ALTER TABLE Benutzer DROP INDEX Email;
```

## Lab 8.3: Referenzielle Integrität und Schlüsselverwaltung

**Fremdschlüssel mit referenzieller Integrität definieren**
```sql
ALTER TABLE Bestellungen ADD FOREIGN KEY (KundenID) REFERENCES Kunden(KundenID);
```

**Verstoß gegen referenzielle Integrität – Einfügen ungültiger Werte**
```sql
INSERT INTO Bestellungen (BestellungID, KundenID) VALUES (101, 9999); -- Fehler, wenn KundenID 9999 nicht existiert
```

**ON DELETE CASCADE verwenden**
```sql
ALTER TABLE Bestellungen ADD FOREIGN KEY (KundenID) REFERENCES Kunden(KundenID)
ON DELETE CASCADE;
```

**ON DELETE SET NULL verwenden**
```sql
ALTER TABLE Mitarbeiter ADD FOREIGN KEY (AbteilungsID) REFERENCES Abteilungen(AbteilungsID)
ON DELETE SET NULL;
```

# Codebeispiele – Modul 9: Tabellen verbinden – Einführung in JOINS

## Lab 9.1: INNER JOIN, LEFT JOIN & RIGHT JOIN

**INNER JOIN – Nur übereinstimmende Datensätze anzeigen**
```sql
SELECT Kunden.Name, Bestellungen.Bestelldatum
FROM Kunden
INNER JOIN Bestellungen ON Kunden.KundenID = Bestellungen.KundenID;
```

**LEFT JOIN – Alle Datensätze der linken Tabelle, passende rechte**
```sql
SELECT Kunden.Name, Bestellungen.Bestelldatum
FROM Kunden
LEFT JOIN Bestellungen ON Kunden.KundenID = Bestellungen.KundenID;
```

**RIGHT JOIN – Alle Datensätze der rechten Tabelle, passende linke**
```sql
SELECT Kunden.Name, Bestellungen.Bestelldatum
FROM Kunden
RIGHT JOIN Bestellungen ON Kunden.KundenID = Bestellungen.KundenID;
```

**JOIN mit zusätzlichen Bedingungen**
```sql
SELECT Kunden.Name, Bestellungen.Bestelldatum, Bestellungen.Preis
FROM Kunden
INNER JOIN Bestellungen ON Kunden.KundenID = Bestellungen.KundenID
WHERE Bestellungen.Preis > 50;
```

## Lab 9.2: JOINs über mehrere Tabellen hinweg

**JOIN über drei Tabellen (Kunden → Bestellungen → Bestellpositionen)**
```sql
SELECT K.Name, B.Bestelldatum, P.Produktname, BP.Menge
FROM Kunden K
INNER JOIN Bestellungen B ON K.KundenID = B.KundenID
INNER JOIN Bestellpositionen BP ON B.BestellungID = BP.BestellungID
INNER JOIN Produkte P ON BP.ProduktID = P.ProduktID;
```

## Lab 9.3: Verwendung von Primär- und Fremdschlüsseln in JOINs

**JOIN mit Primär- und Fremdschlüsselbeziehungen**
```sql
SELECT Kunden.Name, Bestellungen.Bestelldatum
FROM Kunden
INNER JOIN Bestellungen ON Kunden.KundenID = Bestellungen.KundenID;
```

**Mehrstufiger JOIN (mit Zwischentabelle)**
```sql
SELECT K.Name, P.Produktname, BP.Menge
FROM Kunden K
INNER JOIN Bestellungen B ON K.KundenID = B.KundenID
INNER JOIN Bestellpositionen BP ON B.BestellungID = BP.BestellungID
INNER JOIN Produkte P ON BP.ProduktID = P.ProduktID;
```

**LEFT JOIN – Studenten mit und ohne Kurs**
```sql
SELECT Studenten.Name, Kurse.Titel
FROM Studenten
LEFT JOIN Teilnahmen ON Studenten.StudentID = Teilnahmen.StudentID
LEFT JOIN Kurse ON Teilnahmen.KursID = Kurse.KursID;
```