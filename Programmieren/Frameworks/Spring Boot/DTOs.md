#programming 
#springBoot
#java
Ein Data Transfer Object wird genutzt um genau zu bestimmen, welche Daten an den Client weitergegeben werden sollen und welche Daten nicht nach aussen sichtbar gemacht weden.

DTO sind also eine Schnittstelle zwischen Präsentationsschicht (REST-Controller) und Persistenzzschicht (Repository). 

Anstatt vom REST-Controller direkt auf das Repository zuzugreifen, verwendet man einen Service, der zwischen den beiden Schichten fungiert. 


# Welches Problem löst ein DTO?
Wenn man den Controller direkt mit dem Repository verbindet, kann es zu zyklischen Referenzen kommen, die zu einem Stack Overflow führen. DTOs sind die Lösung für dieses Problem.
# DTOS schreiben
Es gibt ein Request- und ein ResponseDTO. Das ResponseDTO erbt und enthält die ID der Entity.. 

