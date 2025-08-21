#ÜK
#backend

# Ziele

- Mittels Annotationen Tabellen einbinden
- Den Begriff “ORM” einordnen
- Den Ablauf einer Datenmanipulation kennen und den des Auslesens bestimmter Datensätze.

# Beziehungen zwischen Tabellen abbilden

Es gibt eine Reihe von Annotationen, die Beziehungen einer relationalen Tabelle repräsentieren:

- @OneToOne
- @OneToMany
- @ManyToOne
- @ManyToMany

# Zyklische Referenz

Wenn sich zwei Entitäten gegenseitig referenzieren, führt das Abfragen zu einem Infinite Loop. Verhindern kann man das, in dem man die Referenz nur in eine Richtung macht.

# ORM

Object Relational Mapping bedeutet, ein Mapping zwischen der Datebank-Tabellen und der Klassen im Code zu haben. Die Datenbankeinträge sollen also zu Objekten werden. Dazu gehören auch Beziehungen, die zwischen Entitäten existieren.

# Entity

`@Entity` ist eine Annotation, die eine Klasse als Entität kennzeichnet. Der Primärschlüssel dieser Klasse muss mit `@Id` gekennzeichnet werden.

`@Table` wird genutzt, um 

`@Column` kann genutzt werden,