
# Codebeispiele aus der Schulung "Grundlagen Relationale Datenbanken & MySQL"

## Tag 2

### Modul 4: Normalisierung – Für stabile und wartbare Datenmodelle

**Lab 4.2: Normalformen**
- **1NF (Atomare Werte):**
  ```plaintext
  Auflösung mehrerer Telefonnummern in einzelne Felder
  ```

- **2NF (partielle Abhängigkeiten):**
  ```plaintext
  Tabelle (BestellNr, ProduktNr, Produktname) wird zu:
  Tabelle Bestellungen (BestellNr, ProduktNr) & Produkte (ProduktNr, Produktname)
  ```

- **3NF (transitive Abhängigkeiten):**
  ```plaintext
  Tabelle Kunden (KundenID, Name, PLZ, Ort) wird zu:
  Kunden (KundenID, Name, PLZ) & Orte (PLZ, Ort)
  ```

### Modul 5: Einstieg in SQL – Die Sprache relationaler Datenbanken

**Lab 5.1: SQL-Grundstruktur**
- **DDL-Befehle:**
  ```sql
  CREATE TABLE tablename (...);
  ALTER TABLE tablename ADD COLUMN columnname datatype;
  DROP TABLE tablename;
  ```

- **DML-Befehle:**
  ```sql
  INSERT INTO tablename VALUES (...);
  SELECT * FROM tablename;
  UPDATE tablename SET columnname = value;
  DELETE FROM tablename WHERE condition;
  ```

- **DCL-Befehle:**
  ```sql
  GRANT SELECT ON tablename TO user;
  REVOKE INSERT ON tablename FROM user;
  ```

**Lab 5.2: Wichtige Datentypen**
- **Ganzzahltypen:**
  ```sql
  INT, SMALLINT, TINYINT, BIGINT
  ```

- **Dezimalzahlen:**
  ```sql
  DECIMAL(10,2)
  ```

- **Zeichenketten:**
  ```sql
  CHAR(10), VARCHAR(255), TEXT
  ```

- **Datum und Zeit:**
  ```sql
  DATE, TIME, DATETIME, TIMESTAMP
  ```

- **Boolesche Typen:**
  ```sql
  BOOLEAN, TINYINT(1)
  ```

**Lab 5.3: CREATE-Befehle**
- **Neue Datenbank erstellen:**
  ```sql
  CREATE DATABASE shop;
  USE shop;
  ```

- **Tabelle erstellen mit Constraints:**
  ```sql
  CREATE TABLE kunden (
    KundenID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100),
    Email VARCHAR(100) UNIQUE NOT NULL
  );
  ```

# Codebeispiele – Modul 6: Daten pflegen – Einfügen und Aktualisieren mit SQL

## Lab 6.1: INSERT INTO – Daten einfügen

**Einfacher INSERT**
```sql
INSERT INTO kunden (Name, Email) VALUES ('Max Mustermann', 'max@example.com');
```

**INSERT mit AUTO_INCREMENT (Primärschlüssel)**
```sql
INSERT INTO kunden (Name, Email) VALUES ('Anna Schmidt', 'anna@example.com');
```

**Mehrere Datensätze gleichzeitig einfügen**
```sql
INSERT INTO kunden (Name, Email) VALUES
('Anna Schmidt', 'anna@example.com'),
('Tom Müller', 'tom@example.com');
```

**Daten aus anderer Tabelle einfügen (INSERT INTO ... SELECT)**
```sql
INSERT INTO archivierte_kunden SELECT * FROM kunden WHERE aktiv = 0;
```

**INSERT IGNORE (ignoriert Duplikate)**
```sql
INSERT IGNORE INTO kunden (Email) VALUES ('max@example.com');
```

**REPLACE INTO (vorhandene Datensätze ersetzen)**
```sql
REPLACE INTO kunden (KundenID, Email) VALUES (1, 'neu@example.com');
```

## Lab 6.2: UPDATE – Daten aktualisieren

**Einzelnes Attribut aktualisieren**
```sql
UPDATE kunden SET Email = 'neu@example.com' WHERE KundenID = 1;
```

**Mehrere Attribute gleichzeitig aktualisieren**
```sql
UPDATE kunden SET Stadt = 'Berlin', PLZ = '10115' WHERE KundenID = 2;
```

**Massenaktualisierung (mehrere Zeilen gleichzeitig ändern)**
```sql
UPDATE produkte SET Preis = Preis * 1.1;
```

**UPDATE mit Bedingungen (WHERE-Klausel gezielt einsetzen)**
```sql
UPDATE produkte SET Preis = Preis * 0.9 WHERE Preis > 100;
UPDATE kunden SET Status = 'aktiv' WHERE letzteBestellung > '2024-01-01';
```

## Lab 6.3: Umgang mit NULL-Werten und Default-Werten

**Spalte mit DEFAULT-Wert erstellen**
```sql
CREATE TABLE kontakte (
  KontaktID INT PRIMARY KEY AUTO_INCREMENT,
  Email VARCHAR(100) NOT NULL,
  Aktiv BOOLEAN DEFAULT TRUE
);
```

**NULL-Werte in Abfragen berücksichtigen (IFNULL / COALESCE)**
```sql
SELECT Name, IFNULL(Telefonnummer, 'keine Nummer') FROM kunden;
```

# Codebeispiele – Modul 7: Daten abfragen – Mit SELECT gezielt analysieren

## Lab 7.1: Der SELECT-FROM-WHERE-Block im Detail

**Alle Kunden anzeigen**
```sql
SELECT * FROM kunden;
```

**Spezifische Attribute anzeigen**
```sql
SELECT Name, Email FROM kunden;
```

**Filterbedingung mit WHERE**
```sql
SELECT * FROM kunden WHERE Stadt = 'Berlin';
```

## Lab 7.2: Filterbedingungen mit WHERE und Vergleichsoperatoren

**Numerischer Vergleich (größer als)**
```sql
SELECT * FROM produkte WHERE Preis > 50.00;
```

**Textvergleich mit LIKE**
```sql
SELECT * FROM kunden WHERE Email LIKE '%@gmail.com';
```

**Mehrere Bedingungen kombinieren (AND / OR)**
```sql
SELECT * FROM bestellungen WHERE Preis > 100 AND Datum >= '2024-01-01';
SELECT * FROM kunden WHERE Stadt = 'Hamburg' OR Stadt = 'Berlin';
```

**NULL-Werte selektieren**
```sql
SELECT * FROM produkte WHERE Beschreibung IS NULL;
```

## Lab 7.3: Sortieren mit ORDER BY

**Einfaches Sortieren aufsteigend**
```sql
SELECT * FROM kunden ORDER BY Name ASC;
```

**Sortieren absteigend nach Datum**
```sql
SELECT * FROM bestellungen ORDER BY Bestelldatum DESC;
```

**Sortieren nach mehreren Spalten**
```sql
SELECT * FROM produkte ORDER BY Kategorie ASC, Preis DESC;
```