## Relationale Datenbanken und MySQL: Grundlagen des SFW-Blocks

Der SFW-Block (Select-From-Where) ist eine grundlegende Struktur in relationalen Datenbanken, die zum Abfragen von Daten verwendet wird. In MySQL und anderen SQL-Dialekten bildet der SFW-Block das Rückgrat von Abfragen. Im Folgenden werden die Grundlagen des SFW-Blocks und seine Verwendung in MySQL erläutert:

### Grundlegende Konzepte

Der SFW-Block besteht aus drei Hauptteilen:

- **Select**: Bestimmt, welche Spalten in der Ergebnismenge enthalten sein sollen.
- **From**: Gibt an, aus welchen Tabellen die Daten abgerufen werden sollen.
- **Where**: Filtert die Zeilen basierend auf einer Bedingung.

### Verwendung in MySQL

#### Beispiel 1: Einfacher SFW-Block

```sql
SELECT column1, column2
FROM table_name
WHERE condition;
```

In diesem Beispiel wählt der SFW-Block Spalten column1 und column2 aus der Tabelle table_name aus und filtert die Ergebnisse basierend auf einer Bedingung.

#### Beispiel 2: Verwendung von Funktionen

```sql
SELECT UPPER(name), COUNT(*)
FROM employees
WHERE department = 'HR'
GROUP BY name
HAVING COUNT(*) > 1;
```

Hier werden die Funktion UPPER() angewendet, um den Namen in Großbuchstaben umzuwandeln, und die COUNT()-Funktion, um die Anzahl der Vorkommen zu zählen. Die Ergebnisse werden nach der department-Bedingung gefiltert und dann nach name gruppiert.

#### Beispiel 3: Join-Operationen

```sql
SELECT employees.name, departments.department_name
FROM employees
JOIN departments ON employees.department_id = departments.id;
```

Dieser SFW-Block führt einen inneren Join zwischen den Tabellen employees und departments durch und wählt die Spalten name aus employees und department_name aus departments aus.

### Zusammenfassung
Der SFW-Block ist eine grundlegende Struktur in SQL, die zum Abfragen von Daten aus relationalen Datenbanken verwendet wird. Durch das Verständnis seiner Bestandteile und deren Verwendung können komplexe Abfragen erstellt und ausgeführt werden, um die gewünschten Informationen aus der Datenbank abzurufen.