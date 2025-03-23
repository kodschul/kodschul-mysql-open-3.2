## Relationale Datenbanken: Normalformen

Normalformen sind formale Regeln, die den Prozess der Datenmodellierung in relationalen Datenbanken leiten. Sie helfen dabei, die Struktur von Datenbanktabellen so zu gestalten, dass Redundanzen minimiert und die Datenintegrität gewährleistet wird. Im Folgenden sind die grundlegenden Normalformen beschrieben:

### 1. Erste Normalform (1NF)

Die Erste Normalform stellt sicher, dass alle Werte in einer Tabelle atomar sind, d.h., dass jedes Feld nur einen einzelnen Wert enthält und nicht wiederholende Gruppen von Werten vorhanden sind.

- **Beispiel**: Eine Tabelle mit einem Feld für Telefonnummern sollte nicht mehrere Telefonnummern in einem Feld enthalten, sondern jede Telefonnummer in einem separaten Feld.

### 2. Zweite Normalform (2NF)

Die Zweite Normalform beseitigt Teilabhängigkeiten, indem sie sicherstellt, dass jedes Nicht-Schlüssel-Attribut voll funktional von jedem Schlüsselkandidaten abhängt.

- **Beispiel**: In einer Tabelle mit den Spalten "OrderID", "ProductID", "Quantity" und "ProductName" hängt "Quantity" von "OrderID" und "ProductID" ab, nicht nur von "OrderID". Daher sollte "ProductName" in eine separate Tabelle verschoben werden, die nur von "ProductID" abhängt.

### 3. Dritte Normalform (3NF)

Die Dritte Normalform eliminiert transitive Abhängigkeiten, indem sie sicherstellt, dass jedes Nicht-Schlüssel-Attribut von einem Schlüsselkandidaten und nicht von einem anderen Nicht-Schlüssel-Attribut abhängt.

- **Beispiel**: In einer Tabelle mit den Spalten "EmployeeID", "DepartmentID" und "DepartmentName" hängt "DepartmentName" von "DepartmentID" ab, nicht direkt von "EmployeeID". Daher sollte "DepartmentName" in eine separate Tabelle verschoben werden, die nur von "DepartmentID" abhängt.

### Weitere Normalformen

Zusätzlich zu den grundlegenden Normalformen gibt es noch weitere, fortgeschrittenere Normalformen wie die Boyce-Codd Normalform (BCNF) und die Vierte Normalform (4NF), die weiter spezifische Anforderungen an die Struktur von Datenbanktabellen stellen.

### Zusammenfassung

Normalformen sind wichtige Konzepte in relationalen Datenbanken, die dazu beitragen, Datenbanktabellen so zu gestalten, dass Redundanzen vermieden und Datenkonsistenz gewährleistet wird. Das Verständnis der Normalformen ist entscheidend für das effektive Design von Datenbanken und die Vermeidung von Anomalien bei der Datenspeicherung und -abfrage.
