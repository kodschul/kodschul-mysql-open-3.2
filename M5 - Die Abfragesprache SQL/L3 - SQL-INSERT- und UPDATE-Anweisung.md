## Einführung in Relationale Datenbanken und MySQL: SQL-INSERT- und UPDATE-Anweisungen

Relationale Datenbanken wie MySQL ermöglichen es Benutzern, Daten in Tabellen einzufügen (INSERT) und zu aktualisieren (UPDATE), was grundlegende Operationen für die Datenmanipulation darstellt. Im Folgenden sind die SQL-Syntax und einige Beispiele für INSERT- und UPDATE-Anweisungen beschrieben:

### SQL-INSERT-Anweisung

Die INSERT-Anweisung wird verwendet, um neue Datensätze in eine Tabelle einzufügen.

#### Allgemeine Syntax:

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```
Beispiel:
```sql
-- Einfügen eines neuen Mitarbeiters in die Tabelle 'employees'
INSERT INTO employees (name, department, salary)
VALUES ('John Doe', 'IT', 60000);
```
In diesem Beispiel wird ein neuer Mitarbeiter mit Namen "John Doe", der der Abteilung "IT" angehört und ein Gehalt von 60000 hat, in die Tabelle 'employees' eingefügt.

### SQL-UPDATE-Anweisung
Die UPDATE-Anweisung wird verwendet, um vorhandene Datensätze in einer Tabelle zu aktualisieren.

#### Allgemeine Syntax:
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
Beispiel:
```sql
-- Aktualisieren des Gehalts für den Mitarbeiter mit der ID 123 auf 65000
UPDATE employees
SET salary = 65000
WHERE id = 123;
```
In diesem Beispiel wird das Gehalt für den Mitarbeiter mit der ID 123 auf 65000 aktualisiert.

### Zusammenfassung
Die SQL-INSERT- und UPDATE-Anweisungen sind grundlegende Werkzeuge zur Datenmanipulation in relationalen Datenbanken wie MySQL. Mit INSERT können neue Datensätze hinzugefügt werden, während UPDATE vorhandene Datensätze aktualisiert. Durch das Verständnis dieser SQL-Anweisungen können Benutzer Daten effektiv in ihren Datenbanken verwalten und aktualisieren.