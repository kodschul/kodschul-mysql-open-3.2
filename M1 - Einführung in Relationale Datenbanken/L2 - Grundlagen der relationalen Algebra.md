## Einführung in Relationale Datenbanken: Grundlagen der relationalen Algebra

Relationale Datenbanken basieren auf der relationalen Algebra, einem theoretischen Modell zur Manipulation und Abfrage von Daten. Diese Grundlagen sind entscheidend für das Verständnis der Funktionsweise relationaler Datenbanksysteme. Im Folgenden sind einige grundlegende Konzepte und Operationen der relationalen Algebra beschrieben:

### Grundlegende Konzepte

Die relationale Algebra besteht aus einer Reihe von Operationen, die auf Relationen (Tabellen) angewendet werden können, um neue Relationen zu erzeugen. Zu den grundlegenden Operationen gehören:

- **Selektionsoperation (Selection)**: Filtern von Zeilen basierend auf einer Bedingung.
- **Projektionsoperation (Projection)**: Auswählen bestimmter Spalten.
- **Kartesisches Produkt (Cartesian Product)**: Kombination jeder Zeile der ersten Tabelle mit jeder Zeile der zweiten Tabelle.
- **Vereinigungsoperation (Union)**: Vereinigung zweier Tabellen unter Entfernung von Duplikaten.
- **Differenzoperation (Set Difference)**: Bestimmen der Zeilen, die in der ersten, aber nicht in der zweiten Tabelle vorhanden sind.
- **Schnittmengenoperation (Intersection)**: Bestimmen der gemeinsamen Zeilen zweier Tabellen.
- **Verbundoperation (Join)**: Kombination von Zeilen aus zwei Tabellen basierend auf einer gemeinsamen Bedingung.

### Operationen der relationalen Algebra

#### Selektionsoperation (Selection)

Die Selektionsoperation filtert Zeilen einer Tabelle basierend auf einer Bedingung.

- **Notation**: $\sigma_{Bedingung}(Relation)$
- **Beispiel**: $\sigma_{department='HR'}(employees)$
- **Ergebnis**: Eine neue Relation, die nur die Zeilen enthält, welche die Bedingung erfüllen.

#### Projektionsoperation (Projection)

Die Projektion wählt bestimmte Spalten aus einer Tabelle aus und eliminiert dabei Duplikate.

- **Notation**: $\pi_{Spalten}(Relation)$
- **Beispiel**: $\pi_{name, department}(employees)$
- **Ergebnis**: Eine neue Relation, die nur die ausgewählten Spalten enthält.

#### Kartesisches Produkt (Cartesian Product)

Das kartesische Produkt kombiniert jede Zeile der ersten Tabelle mit jeder Zeile der zweiten Tabelle.

- **Notation**: $Relation1 \times Relation2$
- **Beispiel**: $employees \times departments$
- **Ergebnis**: Eine neue Relation, die alle möglichen Kombinationen der Zeilen beider Tabellen enthält.

#### Vereinigungsoperation (Union)

Die Vereinigungsoperation kombiniert die Zeilen zweier Tabellen und entfernt Duplikate.

- **Notation**: $Relation1 \cup Relation2$
- **Beispiel**: $employees1 \cup employees2$
- **Ergebnis**: Eine neue Relation, die alle einzigartigen Zeilen beider Tabellen enthält.

#### Differenzoperation (Set Difference)

Die Differenzoperation gibt die Zeilen zurück, die in der ersten Tabelle, aber nicht in der zweiten Tabelle vorhanden sind.

- **Notation**: $Relation1 - Relation2$
- **Beispiel**: $employees1 - employees2$
- **Ergebnis**: Eine neue Relation, die nur die Zeilen der ersten Tabelle enthält, die nicht in der zweiten Tabelle vorkommen.

#### Schnittmengenoperation (Intersection)

Die Schnittmengenoperation gibt die gemeinsamen Zeilen zweier Tabellen zurück.

- **Notation**: $Relation1 \cap Relation2$
- **Beispiel**: $employees1 \cap employees2$
- **Ergebnis**: Eine neue Relation, die nur die gemeinsamen Zeilen beider Tabellen enthält.

#### Verbundoperation (Join)

Der Verbund kombiniert Zeilen aus zwei Tabellen basierend auf einer gemeinsamen Bedingung.

- **Notation**: $Relation1 \bowtie_{Bedingung} Relation2$
- **Beispiel**: $employees \bowtie_{employees.department_id=departments.department_id} departments$
- **Ergebnis**: Eine neue Relation, die die Zeilenkombinationen enthält, die die Bedingung erfüllen.

### Zusammenfassung

Die relationale Algebra bietet eine formale Grundlage für das Verwalten und Abfragen von Daten in relationalen Datenbanksystemen. Durch das Verständnis der verschiedenen Operationen und deren Notation können komplexe Datenbankabfragen effektiv geplant und ausgeführt werden. Diese theoretischen Konzepte sind essenziell für das Arbeiten mit SQL und das Design von Datenbankstrukturen.
