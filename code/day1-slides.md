## Tag 1

### Modul 1: Einführung in Relationale Datenbanken

**Lab 1.1: Das relationale Datenbankmodell**
- **Beispielrelation Kunden und Bestellungen:** Tabellenstruktur mit Kundennummer als gemeinsamer Schlüssel.

**Lab 1.2: Grundlagen der relationalen Algebra**
- **Selektion (σ):** Beispiel: Alle Kunden aus Berlin:
  ```
  σ_Stadt='Berlin'(Kunden)
  ```
- **Projektion (π):** Beispiel: Nur Kundennamen anzeigen:
  ```
  π_Name(Kunden)
  ```
- **Kreuzprodukt (×):** Beispiel: Kombination aller Kunden und Bestellungen:
  ```
  Kunden × Bestellungen
  ```
- **Vereinigung (∪):** Beispiel: Alle Produkte aus zwei Lagern:
  ```
  Lager1 ∪ Lager2
  ```
- **Differenz (−):** Beispiel: Kunden ohne Bestellung:
  ```
  Kunden − Bestellungen
  ```
- **Umbenennung (ρ):** Umbenennung von Relationen oder Attributen.
- **Join (⨝):** Beispiel: Bestellungen mit Kundennamen:
  ```
  Bestellungen ⨝ Kunden
  ```

**Lab 1.3: Anwendungsspezifische, logische und physikalische Ebene**
- **SQL-View (Externe Ebene):** Benutzer sieht nur Name und Stadt:
  ```sql
  CREATE VIEW Kunden_View AS
  SELECT Name, Stadt FROM Kunden;
  ```
- **Logisches Schema Beispiel:** Tabellenstruktur mit Attributen und Beziehungen (kein SQL-Code explizit gezeigt).
- **Interne Ebene Beispiel:** Index-Erstellung zur Optimierung:
  ```sql
  CREATE INDEX idx_Nachname ON Kunden(Nachname);
  ```

### Modul 2: Aufgaben und Bestandteile eines DBMS

**Lab 2.1: Funktionen und Hauptkomponenten eines DBMS**
- **Constraints Beispiel:** Datenintegrität sicherstellen (z.B. Preis > 0)
  ```sql
  ALTER TABLE Produkte ADD CHECK (Preis > 0);
  ```
- **Transaktionsbeispiel (ACID):** Beispielhafte Erläuterung ohne expliziten SQL-Code.
- **Sicherheitsbeispiel:** Benutzerverwaltung und Rechtevergabe in MySQL:
  ```sql
  GRANT SELECT, INSERT ON kunden.* TO 'user'@'localhost';
  ```
- **Backup-Beispiel (MySQL):**
  ```bash
  mysqldump -u root -p Datenbankname > backup.sql
  ```
- **Performanceoptimierung (Index-Beispiel):**
  ```sql
  CREATE INDEX idx_Produktname ON Produkte(Produktname);
  ```

**Lab 2.3: Werkzeuggestützte Entwicklung**
- Übersicht über Tools (kein expliziter Code)

### Modul 3: Methodik der Datenbank-Entwicklung

**Lab 3.1: Grundlagen des Datenbankdesigns**
- Datenbankschema-Erstellung (kein expliziter SQL-Code gezeigt).

**Lab 3.2: Entity-Relationship-Modellierung**
- **ER-Modell Beispiel:**
  ```plaintext
  Entität Kunde:
    - KundenID (PK)
    - Name
    - Adresse

  Beziehung Bestellung:
    - BestellID (PK)
    - Datum
    - KundenID (FK)
  ```
- **Beispiel Kardinalitäten:** (z.B. 1:n Kunde → Bestellungen, kein expliziter Code)
