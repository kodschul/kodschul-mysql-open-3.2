# Lösungen zu den Übungen

## Tabellen erstellen

```sql
CREATE TABLE KontaktProdukt (
  KontaktID INT,
  ProduktID INT,
  GekauftAm DATE,
  FOREIGN KEY (KontaktID) REFERENCES Kontakte(KontaktID),
  FOREIGN KEY (ProduktID) REFERENCES Produkte(ProduktID)
);
```

## Übung 1: Einfügen von Daten

```sql
INSERT INTO KontaktProdukt (KontaktID, ProduktID, GekauftAm)
VALUES
(1, 1, '2024-01-10'),
(1, 2, '2024-01-15'),
(2, 3, '2024-02-20'),
(3, 1, '2024-02-25'),
(3, 4, '2024-03-05');
```

### Abfrage aller gekauften Produkte pro Kontakt

```sql
SELECT k.Vorname, k.Nachname, p.Name AS Produktname, p.Preis, kp.GekauftAm
FROM KontaktProdukt kp
JOIN Kontakte k ON kp.KontaktID = k.KontaktID
JOIN Produkte p ON kp.ProduktID = p.ProduktID
ORDER BY k.Nachname;
```

## Übung 2: Erweiterte Abfragen

### Kontakte ohne Käufe anzeigen

```sql
SELECT k.*
FROM Kontakte k
LEFT JOIN KontaktProdukt kp ON k.KontaktID = kp.KontaktID
WHERE kp.KontaktID IS NULL;
```

### Alle Produkte mit und ohne Verkäufe anzeigen

```sql
SELECT p.*, kp.KontaktID
FROM Produkte p
LEFT JOIN KontaktProdukt kp ON p.ProduktID = kp.ProduktID;
```
