## Relationale Datenbanken und MySQL: Sortierung und Filterung

Sortierung und Filterung sind grundlegende Operationen in relationalen Datenbanken, die es ermöglichen, Daten nach bestimmten Kriterien anzuzeigen und zu ordnen. MySQL, ein weit verbreitetes relationales Datenbanksystem, bietet umfangreiche Funktionen für Sortierung und Filterung von Daten. Im Folgenden sind einige grundlegende Konzepte und Beispiele für Sortierung und Filterung in MySQL beschrieben:

### Sortierung von Daten

Die Sortierung von Daten in MySQL wird mit dem `ORDER BY`-Statement durchgeführt. Dieses Statement ermöglicht es, Ergebnisse basierend auf einer oder mehreren Spalten zu sortieren, entweder aufsteigend (`ASC`) oder absteigend (`DESC`).

#### Beispiel: Sortierung nach einer Spalte

```sql
SELECT * FROM customers
ORDER BY last_name ASC;
```

Dieses Beispiel sortiert die Ergebnisse der Abfrage der Tabelle customers nach dem Nachnamen der Kunden in aufsteigender Reihenfolge.

#### Beispiel: Sortierung nach mehreren Spalten

```sql
SELECT * FROM orders
ORDER BY order_date DESC, order_amount ASC;

```

Hier werden die Ergebnisse der Abfrage der Tabelle orders zuerst nach dem Bestelldatum in absteigender Reihenfolge und dann nach dem Bestellbetrag in aufsteigender Reihenfolge sortiert.

### Filterung von Daten
Die Filterung von Daten in MySQL wird mit dem WHERE-Statement durchgeführt. Dieses Statement ermöglicht es, Ergebnisse basierend auf einer oder mehreren Bedingungen zu filtern.

#### Beispiel: Einfache Filterung

```sql
SELECT * FROM products
WHERE category = 'Electronics';
```

Dieses Beispiel filtert die Ergebnisse der Abfrage der Tabelle products und gibt nur Produkte aus der Kategorie 'Electronics' zurück.

#### Beispiel: Filterung mit logischen Operatoren

```sql
SELECT * FROM employees
WHERE department = 'HR' AND salary > 50000;
```

Hier werden die Ergebnisse der Abfrage der Tabelle employees gefiltert, um nur Mitarbeiter aus der Abteilung 'HR' mit einem Gehalt über 50.000 zurückzugeben.

### Kombinierte Sortierung und Filterung
Sortierung und Filterung können auch kombiniert werden, um spezifische Ergebnisse zu erhalten.

#### Beispiel: Kombinierte Sortierung und Filterung

```sql
SELECT * FROM orders
WHERE order_status = 'Shipped'
ORDER BY order_date DESC;
```

Dieses Beispiel filtert die Ergebnisse der Abfrage der Tabelle orders nach dem Status 'Shipped' und sortiert sie dann nach dem Bestelldatum in absteigender Reihenfolge.

### Zusammenfassung
Sortierung und Filterung sind grundlegende Operationen in relationalen Datenbanken, die es ermöglichen, Daten gezielt abzufragen und anzuzeigen. Mit MySQL können diese Operationen effektiv durchgeführt werden, um spezifische Anforderungen an die Datenanalyse zu erfüllen.