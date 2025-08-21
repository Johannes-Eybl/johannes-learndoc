#programming 
#springBoot
#java
Eine Entity ist ein Objekt, das einen Datenbankeintrag repräsentiert. Mit ORM (Object Relational Mapping) kann Spring Boot die Entity selber erstellen. Programmieren muss man nur das Entity-Objekt mit seinen Variablen.

# Entity erstellen
Die SQL-Tabelle:

| person             |
| ------------------ |
| id INT PRIMARY KEY |
| first_name VARCHAR |
| last_name VARCHAR  |

Wird zu:
```Java
@Entity
public class Person {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;

	private String firstName;

	private String lastName;
}
```

# Entitys mit Relationen zueinander
Zur Entity "Person" gibt es noch eine Tabelle "pet":

| pet                      |
| ------------------------ |
| id INT PRIMARY KEY       |
| name VARCHAR             |
| owner_id INT FOREIGN KEY |

Wird zu:
```Java
@Entity
public class Pet {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;

	private String name;

	@ManyToOne
	@JoinColum(name = "owner_id")
	private Person owner;
}
```

Wenn nun die Personen abgefragt werden:
```Java
List<Person> people = personRepository.findAll();
```
Erhält man eine Liste von "Person"-Objekten.

# Assoziationen
Die Assoziationen sind:

| Annotation  | Assoziation |
| ----------- | ----------- |
| @OneToOne   | 1:1         |
| @OneToMany  | 1:m         |
| @ManyToOne  | m:1         |
| @ManyToMany | m:m         |
Alle Assoziationen sind gerichtet. 
Bei bidirektionalen Entitäten müssen wir uns selber darum kümmern, dass beide Beziehungen synchronisiert sind. 

## OneToOne
Beispiel -> Hauptstadt

```Java
@Entity
public class Country {
	@OneToOne
	@JoinColumn(name="capital_city_id");
	private City capitalCity;
}

@Entity
public class City {
	@OneToOne
	private Country country;
}
```
## OneToMany
Beispiel -> Personen zu Pets
```Java
@Entity
public class Person {
	@OneToMany(mappedBy="owner")
	private List<Pet> pets;
}

@Entity
public class Pet {
	@ManyToOne(optional=false)
	@JoinColumn(name="owner_id")
	private Person owner;
}
```

- "owner" ist der Names des Java-Feldes aus der Klasse "Pet"
- Für die Pets wird eine Liste verwendet, da wiederholbare Werte erwünscht sind. Für unique Values muss man ein Set verwenden.
- "optional=false" definiert, dass eine Beziehung bestehen _muss_
## ManyToMany
Beispiel -> Schüler zu Schulklassen

In SQL werden m:m-Beziehungen mit Zwischentabellen gelöst. Spring Boot kann diese Beziehung direkt mit '@ManyToMany' auflösen. Alternativ kann man die Zwischentabelle als eigene Klasse in Java implementieren.

```Java
@Entity
public class Course {
	@ManyToMany
	@JoinTable(
		name="course_student",
		joinColumns=@JoinColumn(name="course_id")
		inverseJoinColumns=@JoinColumn(name="student_id)
	)
	private Set<Student> students;
}

@Entity
public class Student {
	@ManyToMany(mappedBy="students")
	private Set<Course> courses;
}
```

# Zyklische Referenzen
Wenn man [[#ManyToMany]] verwendet, erfährt man früher oder später das Problem der "zyklischen Referenz". Bei dieser endlosen Schlaufe fragt die Klasse den Schüler ab und der Schüler die Klasse usw.
Aus diesem Grund wird nur in eine Richtung serialisiert. 


# Zusätzliche Annotationen

| Annotation                                 | Erklärung                                                    |
| ------------------------------------------ | ------------------------------------------------------------ |
| @Table(name="tbl_person")                  | Wenn sich DB- oder Tabellennamen unterscheiden               |
| @Column(name="vorname")                    | Wenn sich Spaltennamen unterscheiden                         |
| @Column(insertable=false, updatable=false) | Wenn das Feld von der Applikation nicht gesetzt werden darf. |
| @Column(unique=true)                       | Wenn das Feld einzigartig sein muss.                         |
| @GeneratedValue                            | Falls Id Datenbankseitig vergeben wird (best Practice)       |
