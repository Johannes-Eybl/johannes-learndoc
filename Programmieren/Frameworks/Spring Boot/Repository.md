#programming #springBoot #java
Ein Repository ist die Schnittstelle zwischen Datenbank und dem Code. Jedes Repository ist ein Interface, dass vom Interface 'JpaRepository' erbt. 
# Aufbau
```Java
public interface ItemRepository extends JpaRepository<Item, Integer> {
	List<Item> findByNameContains(String name);

	@Query("SELECT i FROM Item i JOIN i likedTags t WHERE i name LIKE CONCAT('%', :tagName, '%')")
	List<Item> findByTagName(@Param("tagName") String tagName);
}
```

| Annotation              | Erklärung                                                            |
| ----------------------- | -------------------------------------------------------------------- |
| @Query                  | Erlaubt das Definieren von eigenen SQL-Queries                       |
| @Param("parameterName") | Zeigt Spring, welcher Parameter für das Query verwendet werden soll. |

> [!NOTE] Achtung
> JpaRepository hat bereits sehr viele eingebaute Funktionen, weshalb man häufig keine eigenen SQL-Queries schreiben muss!

