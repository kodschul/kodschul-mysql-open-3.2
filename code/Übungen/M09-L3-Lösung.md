## Tabellen erstellen

```sql
CREATE TABLE KontaktProdukt (
  KontaktID INT,
  ProduktID INT,
  GekauftAm DATE,
  FOREIGN KEY (KontaktID) REFERENCES Kontakte(KontaktID),
  FOREIGN KEY (ProduktID) REFERENCES Produkte(ProduktID)
);

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
  FOREIGN KEY (StudentID) REFERENCES Studenten(StudentID),
  FOREIGN KEY (KursID) REFERENCES Kurse(KursID)
);
```

## Übung : JOIN und LEFT JOIN (Studenten und Kurse)

### JOIN-Abfrage: Name und Kurstitel

```sql
SELECT s.Name, k.Titel
FROM Studenten s
JOIN Teilnahmen t ON s.StudentID = t.StudentID
JOIN Kurse k ON t.KursID = k.KursID;
```

### LEFT JOIN-Abfrage: Alle Studenten, auch ohne Kurse

```sql
SELECT s.Name, k.Titel
FROM Studenten s
LEFT JOIN Teilnahmen t ON s.StudentID = t.StudentID
LEFT JOIN Kurse k ON t.KursID = k.KursID;
```
