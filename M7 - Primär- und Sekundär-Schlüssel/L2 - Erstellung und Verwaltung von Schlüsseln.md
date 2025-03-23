## Relationale Datenbanken und MySQL: Erstellung und Verwaltung von Schlüsseln

Schlüssel spielen eine wichtige Rolle in relationalen Datenbanken wie MySQL, da sie die Integrität der Daten sicherstellen und effiziente Abfragen ermöglichen. Im Folgenden werden die Grundlagen der Schlüsselerstellung und -verwaltung in relationalen Datenbanken, insbesondere mit MySQL, erläutert:

### Primärschlüssel (Primary Key)

Ein Primärschlüssel ist eine eindeutige Kennung für jede Zeile in einer Tabelle. Er identifiziert jede Zeile eindeutig und verhindert Duplikate.

**Erstellung in MySQL**:

  ```sql
  CREATE TABLE table_name (
    id INT PRIMARY KEY,
  );
```

Merkmale: Ein Primärschlüssel kann aus einer oder mehreren Spalten bestehen. In MySQL wird oft ein automatisch inkrementierendes Feld (AUTO_INCREMENT) als Primärschlüssel verwendet.
### Fremdschlüssel (Foreign Key)
Ein Fremdschlüssel ist ein Feld in einer Tabelle, das auf den Primärschlüssel einer anderen Tabelle verweist. Er stellt Beziehungen zwischen Tabellen her.


```sql
  CREATE TABLE table_name (
    id INT PRIMARY KEY,
    ...
  );
```

Merkmale: Ein Fremdschlüssel stellt sicher, dass jede referenzierte Zeile in der verknüpften Tabelle existiert. Dadurch werden Integritätsregeln wie die Referentielle Integrität durchgesetzt.

### Eindeutiger Schlüssel (Unique Key)
Ein eindeutiger Schlüssel sorgt dafür, dass der Wert in einer Spalte oder in einer Kombination von Spalten eindeutig ist, erlaubt jedoch NULL-Werte.

### Erstellung in MySQL:

```sql
  CREATE TABLE table_name (
  ...
  email VARCHAR(255) UNIQUE,
  ...
);
```

Merkmale: Ein eindeutiger Schlüssel erlaubt nur einen NULL-Wert in der Spalte und erzwingt die Eindeutigkeit der Werte.

### Composite Key
Ein Composite Key besteht aus mehreren Spalten und wird verwendet, um die Eindeutigkeit von Kombinationen von Werten sicherzustellen.

### Erstellung in MySQL:

```sql
CREATE TABLE table_name (
  ...
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  PRIMARY KEY (first_name, last_name)
);
```

Merkmale: Ein Composite Key besteht aus mehreren Spalten und stellt sicher, dass die Kombination dieser Spaltenwerte eindeutig ist.

### Zusammenfassung
Die Verwendung von Schlüsseln in relationalen Datenbanken wie MySQL ist entscheidend für die Datenintegrität und die Festlegung von Beziehungen zwischen Tabellen. Primärschlüssel identifizieren eindeutig jede Zeile in einer Tabelle, Fremdschlüssel verknüpfen Tabellen miteinander, Eindeutige Schlüssel stellen sicher, dass Spaltenwerte eindeutig sind, und Composite Keys ermöglichen die Verwendung mehrerer Spalten zur Identifizierung von Zeilen.