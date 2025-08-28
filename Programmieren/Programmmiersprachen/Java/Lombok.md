Lombok automatisiert Code wie Getter/Setter, sodass man weniger von Hand schreiben muss und mehr Zeit für die wichtigen Teile eines Projekts hat.
# Maven Setup
Um Lombok zu verwenden, muss man Maven sagen, dass man es verwenden will. Dafür muss man die folgende Dependency to 'pom.xml' hinzufügen:
```xml
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.36</version>
    <scope>provided</scope>
</dependency>
```
# Getter, Setter
Häufig verwendet man in Java Getter und Setter um anderen Objekten den Zugriff auf die Felder eines Objekts zu erlauben. Diese Getter und Setter brauchen häufig mehr Platz als der Rest vom Code einer Klasse.

Mit '@Getter' und  '@Setter' werden diese für alle Felder der Klasse generiert!
Auch wenn man neue Felder hinzufügt, bekommen diese automatisch ebenfalls Getter und Setter.
```Java
@Getter @Setter @NoArgsConstructor // <--- THIS is it
public class User {

    private Long id;

    private String firstName;
    private String lastName;
    private int age;

    public User(String firstName, String lastName, int age) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
}
```
Will man, das zB. die Id nur gelesen, aber nicht geändert werden kann, fügt man ihr zusätzlich noch ein Attribut hinzu:
```Java
private @Setter(AccessLevel.PROTECTED) Long id;
```
# Constructors
In manchen Frameworks (JPA beispielsweise) muss man seinen Klassen einen Konstruktor geben - auch, wenn man diesen nie verwendet.

Damit man diesen nicht ausschreiben muss, bietet Lombok die '@NoArgsConstructor'-Annotation. 

Umgekehrt kann man '@AllArgsConstructor' verwenden, um automatische einen Konstruktor mit allen Feldern zu erhalten.

Ausserdem gibt es den '@RequiredArgsConstructor', welcher die übergebenen Werte validiert, bevor er sie setzt. Das kann man mit Annotationen wie '@NonNull' verbinden, um Validation zu erzwingen.
# Equals und Hashcode
Die Annotation '@EqualsAndHashCode' generiert die entsprechenden Methoden mit allen relevanten Feldern.
# Builder
Die Annotation '@Builder' übernimmt praktisch alles, was die oberen Annotationen gemacht haben und noch mehr. 
```Java
@Getter
@Builder
public class Widget {
    private final String name;
    private final int id;
}
```
Die oben definierte Klasse kann man nun verwenden:
```Java
Widget testWidget = Widget.builder()
  .name("foo")
  .id(1)
  .build();

assertThat(testWidget.getName())
  .isEqualTo("foo");
assertThat(testWidget.getId())
  .isEqualTo(1);
```
