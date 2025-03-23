## Relationale Datenbanken und MySQL: Erstellung von Datenbanken und Tabellen

In relationalen Datenbanken wie MySQL werden Daten in Tabellen organisiert, und die Struktur dieser Tabellen wird durch Schemas definiert. Die Erstellung von Datenbanken und Tabellen ist ein grundlegender Schritt bei der Entwicklung einer Datenbankanwendung. Im Folgenden sind die grundlegenden Schritte zur Erstellung von Datenbanken und Tabellen in MySQL beschrieben:

### Datenbank erstellen

Die Erstellung einer Datenbank in MySQL erfolgt mit dem Befehl `CREATE DATABASE`.

#### Beispiel:

```sql
CREATE DATABASE my_database;
```

Dieser Befehl erstellt eine neue Datenbank mit dem Namen my_database.

### Tabelle erstellen
Die Erstellung einer Tabelle in MySQL erfolgt mit dem Befehl CREATE TABLE.

```sql
CREATE TABLE employees (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(100),
    salary DECIMAL(10, 2)
);
```

Dieser Befehl erstellt eine neue Tabelle mit dem Namen employees. Die Tabelle enthält vier Spalten: id, name, department und salary, jeweils mit ihren entsprechenden Datentypen und optionalen Einschränkungen.

### Primärschlüssel und AUTO_INCREMENT
In relationalen Datenbanken wird oft eine Primärschlüssel-Spalte verwendet, um jede Zeile eindeutig zu identifizieren. Mit dem Attribut AUTO_INCREMENT wird automatisch eine neue eindeutige ID für jede neu eingefügte Zeile generiert.

### Datentypen
MySQL unterstützt verschiedene Datentypen wie INT, VARCHAR, DECIMAL, DATE, TIME usw. Diese Datentypen legen fest, welche Art von Daten in einer Spalte gespeichert werden kann.

### Einschränkungen
Einschränkungen (Constraints) wie PRIMARY KEY, NOT NULL, UNIQUE usw. werden verwendet, um Regeln für die Daten in einer Tabelle festzulegen. Sie helfen dabei, die Datenintegrität sicherzustellen und die Konsistenz der Datenbank zu wahren.

### Zusammenfassung
Die Erstellung von Datenbanken und Tabellen ist ein grundlegender Schritt bei der Entwicklung relationaler Datenbankanwendungen. Mit MySQL und der relationalen Algebra können Entwickler Datenbankstrukturen entwerfen, die den Anforderungen ihrer Anwendungen entsprechen. Durch die Verwendung von Primärschlüsseln, Datentypen und Einschränkungen können Datenbanken effizient organisiert und verwaltet werden.