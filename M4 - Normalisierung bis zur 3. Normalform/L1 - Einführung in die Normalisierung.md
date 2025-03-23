## Relationale Datenbanken: Einführung in die Normalisierung

Die Normalisierung ist ein wichtiger Prozess bei der Gestaltung von Datenbanken, um Redundanz zu reduzieren und die Integrität der Daten zu verbessern. Sie hilft dabei, Datenbanken in eine optimale Struktur zu transformieren, die Anomalien wie Anomalien bei der Einfügung, Aktualisierung und Löschung vermeidet. Im Folgenden sind einige grundlegende Konzepte und Normalisierungsstufen beschrieben:

### Grundlegende Konzepte

- **Funktionale Abhängigkeit**: Eine Attributmenge X ist funktional abhängig von einer Attributmenge Y, wenn jedes Y-Wert eindeutig einen X-Wert bestimmt.
- **Anomalien**: Probleme, die bei der Manipulation von Daten in nicht normalisierten Tabellen auftreten können, wie Inkonsistenzen, Redundanz und Verlust von Datenintegrität.
- **Normalisierung**: Ein Prozess, der dazu dient, eine Datenbank in eine Struktur zu transformieren, die Redundanz reduziert und Anomalien beseitigt.

### Normalisierungsstufen

#### Erste Normalform (1NF)

- Jede Zelle enthält einen einzigen Wert.
- Jede Spalte hat einen eindeutigen Namen.
- Die Reihenfolge der Zeilen und Spalten spielt keine Rolle.

#### Zweite Normalform (2NF)

- Die Tabelle ist in 1NF.
- Jedes Nicht-Schlüsselattribut ist voll funktional abhängig vom Primärschlüssel.

#### Dritte Normalform (3NF)

- Die Tabelle ist in 2NF.
- Jedes Nicht-Schlüsselattribut ist transitiv nicht funktional abhängig vom Primärschlüssel.

#### Boyce-Codd Normalform (BCNF)

- Die Tabelle ist in 3NF.
- Jede funktional abhängige Beziehung basiert nur auf den Kandidatenschlüsseln, nicht auf anderen Nicht-Schlüsselattributen.

### Beispiel

Betrachten wir eine nicht normalisierte Tabelle für Kundenbestellungen:

| Bestellungsnummer | Kundenname | Kundenadresse      | Produktnummer | Produktname | Produktkategorie |
|-------------------|------------|--------------------|---------------|-------------|------------------|
| 1                 | John       | 123 Main Street    | 101           | Laptop      | Elektronik       |
| 2                 | John       | 123 Main Street    | 102           | Smartphone  | Elektronik       |
| 3                 | Jane       | 456 Elm Street     | 103           | Fernseher   | Elektronik       |
| 4                 | Jane       | 456 Elm Street     | 104           | Sofa        | Möbel            |

Diese Tabelle ist in der ersten Normalform, aber nicht in der zweiten oder dritten Normalform, da die Spalten "Kundenname", "Kundenadresse", "Produktname" und "Produktkategorie" von der Bestellungsnummer abhängig sind, nicht jedoch voll funktional abhängig vom Primärschlüssel.

### Schritte zur Normalisierung

1. Identifizierung der funktionalen Abhängigkeiten.
2. Umwandlung der Tabelle in die erste Normalform, falls noch nicht geschehen.
3. Entfernung von Teilmengenfunktionalitäten durch Aufteilung der Tabelle in mehrere Tabellen.
4. Überprüfung der Normalisierungsstufen und gegebenenfalls weitere Aufteilung der Tabellen.

### Vorteile der Normalisierung

- Reduzierung von Redundanz.
- Verbesserung der Datenintegrität.
- Vereinfachung der Datenmanipulation.

Die Normalisierung ist ein wesentlicher Schritt bei der Entwicklung einer effizienten und wartungsfreundlichen Datenbankstruktur. Sie trägt dazu bei, Datenanomalien zu vermeiden und eine konsistente Datenverwaltung zu gewährleisten.
