# Lösung Aufgabe 1: Tabelle Kontakte erstellen

```sql
CREATE TABLE Kontakte (
  KontaktID INT AUTO_INCREMENT PRIMARY KEY,
  Vorname VARCHAR(50) NOT NULL,
  Nachname VARCHAR(50) NOT NULL,
  Firma VARCHAR(50) DEFAULT NULL,
  EMail VARCHAR(100) NOT NULL UNIQUE,
  Aktiv BOOLEAN NOT NULL DEFAULT TRUE
);
```

# Lösung Aufgabe 2: Tabelle Produkte erstellen

```sql
CREATE TABLE Produkte (
  ProduktID INT AUTO_INCREMENT PRIMARY KEY,
  Name VARCHAR(100) NOT NULL,
  Beschreibung TEXT DEFAULT NULL,
  Preis DECIMAL(10,2) NOT NULL,
  Verfügbar BOOLEAN NOT NULL DEFAULT TRUE,
  EingestelltAm TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```