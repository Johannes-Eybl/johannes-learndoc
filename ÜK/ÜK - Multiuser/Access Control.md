#ÜK
#multiuser

# Ziele

- Spezifische Elemente für die Umsetzung von Multi-User-Fähigen Bernutzerschnittstellen  kennen (zB. Profil, Benutzerschichten, Berechtigungskonzept)
- Möglichkeiten kennen, mit denen man mehrbenutzerfähiges Rechtemanagement implementieren kann
- Gruppen, Rollen und Rechte erklären können
- Wissen, wie man Berechtigungen in Spring implementieren kann

# Begriffe

## Benutzer

Ein Benutzer ist eine spezifische Identität die in einer oder mehreren Gruppen sein kann.

## Gruppe

Eine Gruppe ist eine Sammlung mehrerer Nutzer mit gemeinsamen Merkmalen. Eine Gruppe kann eine oder mehrere Rollen haben

## Rolle / Scope

Eine Rolle ist eine Zusammenfassung von Rechten.

## Recht

Recht definiert, ob und wie auf Ressourcen zugegriffen werden kann.

# Mögliche Userverwaltung

## Direktberechtigungen

Hier werden Nutzern direkt Rechte verteilt. das Problem ist, dass bei vielen Nutzern extrem viel Aufwand entsteht. So ein System ist nicht wirklich brauchbar.

## Gruppen

Hier werden Nutzer in Gruppen unterteilt. Die Gruppen haben verschiedene Rechte und wer die entsprechende Rechte braucht, wird in die passende Gruppe eingeteilt.

## Rollen

Bei Rollen werden Rechte in Zusammengefasst und Nutzern zugewiesen. Wie bei Direktberechtigungen ist auch hier ein Problem, dass jedem Nutzer seine Rolle einzeln zugewiesen werden muss.

Rollen werden in der Fallstudie verwendet!

## Role based Access Control

RBAC ist der Goldstandart für Access-Control. Hier hat man Gruppen *und* Rollen. Nutzer sind also Teil einer Gruppe und haben die dementsprechenden Rechte. Rollen werden nicht Nutzern, sondern Gruppen zugeteilt. Die Rechte ansich werden dann nur mit den Rollen verbunden.

# Access Control in Spring Boot

Es gibt 2 Möglichkeiten, die Access Control ermögichen

## @PreAuthorize

Diese Annotation definiert, was erfüllt sein muss, bevor eine Funktion ausgelöst wird. 

## Eigene Methode

Es ist auch möglich, selber eine Methode zu erstellen, die die Authorität des Nutzers prüft.