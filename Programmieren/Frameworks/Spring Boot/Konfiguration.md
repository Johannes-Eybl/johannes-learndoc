#programming 
#springBoot
#java
Im Pfad 'src/main/resources/application.properties' befindet sich die Konfigurationsdatei für Spring Boot.
# Datenbank einbinden
```
# Database  
spring.jpa.hibernate.ddl-auto=none  
spring.datasource.url=jdbc:mysql://${MYSQL_HOST:localhost}:3306/db_todo_list  
spring.datasource.username=db_todo_list  
spring.datasource.password=Pass4CRUD2020  
  
spring.jpa.properties.hibernate.globally_quoted_identifiers=true  
  
# Security  
# NEVER  
server.error.include-stacktrace=ALWAYS  
  
# log sql queries with params  
#logging.level.org.hibernate.SQL=DEBUG  
#logging.level.org.hibernate.type.descriptor.sql.BasicBinder=TRACE  
#spring.jpa.properties.hibernate.format_sql=true
```

| Zeile                                  | Erklärung                                                                                          |
| -------------------------------------- | -------------------------------------------------------------------------------------------------- |
| spring.jpa.hibernate.ddl-auto = none   | deaktiviere das autmatische Anpassen, erstellen und/oder Validieren der Datenbank durch Hibernate. |
| spring.datasource                      | Setzen von Username, Passwort und Url zum Verbinden mit der DB.                                    |
| server.error.include-stacktrace=ALWAYS | Ob der ganze Stack Trace in einer HTTP-Message weitergegeben werden soll. never/always             |
