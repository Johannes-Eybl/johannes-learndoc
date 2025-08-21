#ÜK
#backend
#testing


“Ein ungetestetes System ist ein Kaputtes System” -Meinrad

Je später man mit dem Testing beginnt, um so mehr Aufwand steckt in der Fehlerbehebung. Deshalb sollte man so früh wie möglich mit den Tests beginnen.

# JUnit

JUnit ist ein Framework zum Testen in Java. Man kann Testmethoden und Testklassen erstellen.

First:

- Fast
- Isolated
- Repeatable
- Self-Validating
- Thorough & Timely

# Testing in Spring Boot

## `@WebMvcTest`

- Vordefinierte Annotation von Spring
- Konfiguriert den Test spezidisch um Controller zu testen
- Setzt Einstellungen für Security, Datenformate usw.

# Test Naming Convention

`what_when_then`

zb: `checkUsersAge_whenUserIsTooYoung_thenReturnFalse(){}`