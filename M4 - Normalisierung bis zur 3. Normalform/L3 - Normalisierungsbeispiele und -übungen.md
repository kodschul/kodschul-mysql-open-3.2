## Relationale Datenbanken: Normalisierungsbeispiele und -übungen

Die Normalisierung ist ein wichtiger Prozess beim Entwurf relationaler Datenbanken, um Datenredundanz zu minimieren und die Integrität der Daten zu gewährleisten. Es gibt verschiedene Normalisierungsstufen, die auf den Prinzipien der relationalen Algebra basieren. Im Folgenden sind einige Beispiele und Übungen zur Normalisierung von relationalen Datenbanken:

### Grundlegende Konzepte

Die Normalisierung ist ein Prozess zur Organisation von Daten in einer Datenbank, um Redundanz und Anomalien zu reduzieren. Die Normalisierung erfolgt in verschiedenen Stufen, die als Normalformen bezeichnet werden. Die gängigsten Normalformen sind:

- **1. Normalform (1NF)**: Alle Attribute in einer Tabelle enthalten atomare Werte und es gibt keine wiederholten Gruppen von Attributen.
- **2. Normalform (2NF)**: Eine Tabelle ist in 1NF, und alle Nicht-Schlüsselattribute sind funktional abhängig vom gesamten Schlüssel.
- **3. Normalform (3NF)**: Eine Tabelle ist in 2NF, und es gibt keine transitiven Abhängigkeiten zwischen den Nicht-Schlüsselattributen und dem Primärschlüssel.

### Beispiel 1: 1. Normalform (1NF)

Gegeben ist eine Tabelle mit wiederholten Gruppen von Attributen:

| OrderID | Customer  | Product      | Quantity |
| ------- | --------- | ------------ | -------- |
| 1       | John      | Apple        | 5        |
| 1       | John      | Banana       | 3        |
| 2       | Alice     | Orange       | 2        |
| 2       | Alice     | Watermelon   | 1        |

Um die 1. Normalform zu erreichen, müssen wiederholte Gruppen von Attributen eliminiert werden, indem die Tabelle in zwei Tabellen aufgeteilt wird:

Tabelle `Orders`:

| OrderID | Customer  |
| ------- | --------- |
| 1       | John      |
| 2       | Alice     |

Tabelle `OrderDetails`:

| OrderID | Product      | Quantity |
| ------- | ------------ | -------- |
| 1       | Apple        | 5        |
| 1       | Banana       | 3        |
| 2       | Orange       | 2        |
| 2       | Watermelon   | 1        |

### Beispiel 2: 2. Normalform (2NF)

Gegeben ist eine Tabelle, in der Nicht-Schlüsselattribute funktional abhängig sind von einem Teil des Schlüssels:

| OrderID | Product      | Category     | Price  |
| ------- | ------------ | ------------ | ------ |
| 1       | Apple        | Fruit        | 2.50   |
| 1       | Banana       | Fruit        | 1.80   |
| 2       | Orange       | Fruit        | 3.00   |
| 2       | Chair        | Furniture    | 25.00  |

Um die 2. Normalform zu erreichen, müssen Nicht-Schlüsselattribute von der vollständigen Schlüsselabhängigkeit entkoppelt werden:

Tabelle `Products`:

| Product      | Category     | Price  |
| ------------ | ------------ | ------ |
| Apple        | Fruit        | 2.50   |
| Banana       | Fruit        | 1.80   |
| Orange       | Fruit        | 3.00   |
| Chair        | Furniture    | 25.00  |

Tabelle `Orders`:

| OrderID | Product      |
| ------- | ------------ |
| 1       | Apple        |
| 1       | Banana       |
| 2       | Orange       |
| 2       | Chair        |

### Beispiel 3: 3. Normalform (3NF)

Gegeben ist eine Tabelle mit transitiven Abhängigkeiten zwischen Nicht-Schlüsselattributen und dem Primärschlüssel:

| OrderID | Product      | Category     | CategoryDescription |
| ------- | ------------ | ------------ | ------------------- |
| 1       | Apple        | Fruit        | Juicy and delicious |
| 1       | Banana       | Fruit        | Great source of potassium |
| 2       | Orange       | Fruit        | Rich in vitamin C   |
| 2       | Chair        | Furniture    | Comfortable seating |

Um die 3. Normalform zu erreichen, müssen transitive Abhängigkeiten entfernt werden, indem eine neue Tabelle für Kategorien erstellt wird:

Tabelle `Products`:

| Product      | CategoryID   |
| ------------ | ------------ |
| Apple        | 1            |
| Banana       | 1            |
| Orange       | 1            |
| Chair        | 2            |

Tabelle `Categories`:

| CategoryID   | Category     | CategoryDescription |
| ------------ | ------------ | ------------------- |
| 1            | Fruit        | Juicy and delicious |
| 2            | Furniture    | Comfortable seating |

Tabelle `Orders`:

| OrderID | ProductID    |
| ------- | ------------ |
| 1       | 1            |
| 1       | 2            |
| 2       | 3            |
| 2       | 4            |

Diese Beispiele und Übungen verdeutlichen die Anwendung der Normalisierung auf relationale Datenbanken, um Datenkonsistenz und -integrität sicherzustellen.
