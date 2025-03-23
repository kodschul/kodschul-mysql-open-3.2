## Tag 2

### Modul 4: Normalisierung – Für stabile und wartbare Datenmodelle

#### Lab 4.2: Normalformen

**1NF (Atomare Werte)**

**Vorher (nicht 1NF):**
```sql
CREATE TABLE kontakte_alt (
  KundenID INT PRIMARY KEY,
  Name VARCHAR(100),
  Telefonnummern VARCHAR(255)
);

INSERT INTO kontakte_alt VALUES (1, 'Max Mustermann', '030-123456,0176-55566677');
```

**Nachher (1NF):**
```sql
CREATE TABLE kontakte_1NF (
  KundenID INT,
  Telefonnummer VARCHAR(20),
  PRIMARY KEY (KundenID, Telefonnummer)
);

INSERT INTO kontakte_1NF VALUES
(1, '030-123456'),
(1, '0176-55566677');
```

**2NF (partielle Abhängigkeiten)**

**Vorher (nicht 2NF):**
```sql
CREATE TABLE Bestellungen_Produkte (
  BestellNr INT,
  ProduktNr INT,
  Produktname VARCHAR(100),
  PRIMARY KEY (BestellNr, ProduktNr)
);

INSERT INTO Bestellungen_Produkte VALUES (1001, 200, 'Laptop'), (1001, 201, 'Maus');
```

**Nachher (2NF):**
```sql
CREATE TABLE Bestellungen (
  BestellNr INT,
  ProduktNr INT,
  PRIMARY KEY (BestellNr, ProduktNr)
);

CREATE TABLE Produkte (
  ProduktNr INT PRIMARY KEY,
  Produktname VARCHAR(100)
);

INSERT INTO Produkte VALUES (200, 'Laptop'), (201, 'Maus');
INSERT INTO Bestellungen VALUES (1001, 200), (1001, 201);
```

**3NF (transitive Abhängigkeiten)**

**Vorher (nicht 3NF):**
```sql
CREATE TABLE Kunden_alt (
  KundenID INT PRIMARY KEY,
  Name VARCHAR(100),
  PLZ VARCHAR(10),
  Ort VARCHAR(100)
);

INSERT INTO Kunden_alt VALUES (1, 'Max Mustermann', '10115', 'Berlin');
```

**Nachher (3NF):**
```sql
CREATE TABLE Kunden (
  KundenID INT PRIMARY KEY,
  Name VARCHAR(100),
  PLZ VARCHAR(10)
);

CREATE TABLE Orte (
  PLZ VARCHAR(10) PRIMARY KEY,
  Ort VARCHAR(100)
);

INSERT INTO Orte VALUES ('10115', 'Berlin');
INSERT INTO Kunden VALUES (1, 'Max Mustermann', '10115');
```

### Modul 6: Daten pflegen – Einfügen und Aktualisieren mit SQL

#### Lab 6.1 & 6.2: INSERT & UPDATE

**Tabelle `kunden`**
```sql
CREATE TABLE kunden (
  KundenID INT PRIMARY KEY AUTO_INCREMENT,
  Name VARCHAR(100),
  Email VARCHAR(100) UNIQUE NOT NULL,
  aktiv BOOLEAN DEFAULT TRUE,
  letzteBestellung DATE,
  Stadt VARCHAR(50),
  PLZ VARCHAR(10)
);

INSERT INTO kunden (Name, Email, aktiv, letzteBestellung, Stadt, PLZ) VALUES
('Max Mustermann', 'max@example.com', TRUE, '2024-03-01', 'Berlin', '10115'),
('Anna Schmidt', 'anna@example.com', FALSE, '2023-11-20', 'Hamburg', '20095'),
('Tom Müller', 'tom@example.com', FALSE, '2023-12-15', 'Berlin', '10117');
```

**Tabelle `produkte`**
```sql
CREATE TABLE produkte (
  ProduktID INT PRIMARY KEY AUTO_INCREMENT,
  Produktname VARCHAR(100),
  Preis DECIMAL(10,2),
  Beschreibung TEXT,
  Kategorie VARCHAR(50)
);

INSERT INTO produkte (Produktname, Preis, Beschreibung, Kategorie) VALUES
('Laptop', 1200.00, 'Gaming Laptop', 'Elektronik'),
('Maus', 25.50, 'Kabellose Maus', 'Elektronik'),
('Kaffeetasse', 12.99, NULL, 'Haushalt'),
('Bürostuhl', 199.99, 'Ergonomischer Bürostuhl', 'Möbel');
```

#### Lab 6.3: NULL-Werte und Default-Werte

**Tabelle `kontakte`**
```sql
CREATE TABLE kontakte (
  KontaktID INT PRIMARY KEY AUTO_INCREMENT,
  Email VARCHAR(100) NOT NULL,
  Aktiv BOOLEAN DEFAULT TRUE
);

INSERT INTO kontakte (Email) VALUES ('kontakt1@example.com'), ('kontakt2@example.com');
```

### Modul 7: Daten abfragen – Mit SELECT gezielt analysieren

#### Lab 7.1 – 7.3: SELECT und Abfragen

**Tabelle `bestellungen`**
```sql
CREATE TABLE bestellungen (
  BestellID INT PRIMARY KEY AUTO_INCREMENT,
  KundenID INT,
  ProduktID INT,
  Preis DECIMAL(10,2),
  Bestelldatum DATE,
  FOREIGN KEY (KundenID) REFERENCES kunden(KundenID),
  FOREIGN KEY (ProduktID) REFERENCES produkte(ProduktID)
);

INSERT INTO bestellungen (KundenID, ProduktID, Preis, Bestelldatum) VALUES
(1, 1, 1200.00, '2024-03-15'),
(1, 2, 25.50, '2024-03-16'),
(2, 3, 12.99, '2023-11-21'),
(3, 4, 199.99, '2023-12-16');
```
