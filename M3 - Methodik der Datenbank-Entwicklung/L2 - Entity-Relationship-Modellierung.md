## Relationale Datenbanken: Entity-Relationship-Modellierung

Das Entity-Relationship-Modell (ER-Modell) ist ein konzeptionelles Werkzeug zur Datenmodellierung und zur Darstellung der Beziehungen zwischen Datenobjekten in einer Datenbank. Es dient als Grundlage für das Design und die Implementierung relationaler Datenbanken.

### Grundlegende Konzepte des ER-Modells

Das ER-Modell besteht aus den folgenden grundlegenden Konzepten:

- **Entitäten (Entities)**: Objekte oder Dinge, die in der Datenbank dargestellt werden sollen. Beispiel: Kunde, Bestellung.
- **Attribute**: Eigenschaften oder Merkmale einer Entität. Beispiel: Name, Adresse.
- **Schlüssel (Keys)**: Ein Attribut oder eine Kombination von Attributen, die eine Entität eindeutig identifizieren. Beispiel: Kundennummer.
- **Beziehungen (Relationships)**: Verbindungen zwischen Entitäten, die beschreiben, wie die Entitäten miteinander interagieren. Beispiel: Ein Kunde gibt eine Bestellung auf.

### Darstellung des ER-Modells

Das ER-Modell wird häufig grafisch dargestellt, wobei verschiedene Symbole verwendet werden:

- **Rechtecke**: Stellen Entitäten dar.
- **Ellipsen**: Stellen Attribute dar.
- **Rauten**: Stellen Beziehungen dar.
- **Linien**: Verbinden Entitäten mit ihren Attributen und Beziehungen.

### Beispiel: ER-Diagramm

Ein einfaches ER-Diagramm könnte wie folgt aussehen:

- **Entitäten**: Kunde, Bestellung
- **Attribute von Kunde**: Kundennummer, Name, Adresse
- **Attribute von Bestellung**: Bestellnummer, Datum, Betrag
- **Beziehung**: Ein Kunde gibt eine Bestellung auf

Kunde (Kundennummer, Name, Adresse)
|
| gibt auf
|
Bestellung (Bestellnummer, Datum, Betrag)

### Arten von Beziehungen

Beziehungen im ER-Modell können verschiedene Kardinalitäten haben:

- **Eins-zu-Eins (1:1)**: Eine Entität ist mit genau einer anderen Entität verbunden. Beispiel: Jeder Mitarbeiter hat genau eine Personalakte.
- **Eins-zu-Viele (1:N)**: Eine Entität ist mit mehreren anderen Entitäten verbunden. Beispiel: Ein Kunde kann mehrere Bestellungen aufgeben.
- **Viele-zu-Viele (M:N)**: Mehrere Entitäten sind mit mehreren anderen Entitäten verbunden. Beispiel: Ein Student kann mehrere Kurse belegen und ein Kurs kann von mehreren Studenten belegt werden.

### Normalisierung

Normalisierung ist der Prozess der Organisation von Daten in einer Datenbank, um Redundanzen zu minimieren und Datenintegrität zu gewährleisten. Es gibt mehrere Normalformen, die schrittweise angewendet werden können:

- **Erste Normalform (1NF)**: Beseitigt wiederholte Gruppen und stellt sicher, dass jedes Attribut einen einzigen Wert hat.
- **Zweite Normalform (2NF)**: Stellt sicher, dass alle Nicht-Schlüssel-Attribute vollständig vom Primärschlüssel abhängen.
- **Dritte Normalform (3NF)**: Stellt sicher, dass Nicht-Schlüssel-Attribute nicht transitiv vom Primärschlüssel abhängen.

### Zusammenfassung

Die Entity-Relationship-Modellierung ist ein wesentlicher Schritt im Design relationaler Datenbanken. Sie hilft dabei, die Struktur der Daten und die Beziehungen zwischen den Daten klar und präzise darzustellen. Durch die Anwendung von ER-Modellen und Normalisierungstechniken kann eine effiziente und konsistente Datenbankstruktur entworfen werden, die den Anforderungen der Anwendungen gerecht wird.
