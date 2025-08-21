#programming 
#springBoot
#java
Spring Boot verwendet eine 3-Tier Architektur. Diese ist in verschiedenen Applikationen von Games bis zu Webservern anzutreffen.

![[SpringBootArchitecture.png]]

Diese Architektur basiert auf:

| Schicht              | Technischer Name           |
| -------------------- | -------------------------- |
| Präsentationsschicht | [[Controller]]             |
| Businesslogikschicht | Service, [[DTOs]]          |
| Persistenzschicht    | [[Repository]], [[Entity]] |
# Kommunikation zwischen den Schichten

| Präsentation        |                | Logik   |                  | Persistenz     |
| ------------------- | -------------- | ------- | ---------------- | -------------- |
| REST-[[Controller]] | <->[[DTOs]]<-> | Service | <->[[Entity]]<-> | [[Repository]] |

DTOs werden zwischen Service und Controller verwendet.
[[Entity]] wird zwischen Service und Repository verwendet
