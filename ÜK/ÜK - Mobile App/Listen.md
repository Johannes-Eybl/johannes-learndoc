#ÜK
#mobileApp

# Ziele

- Verschiedene Listen und deren Einsatzzwecke kennen
- Wissen, wie man Listen verwendetn kann

# Map-Funktion

Sollte nur bei einer kleinen Anzahl Elemente verwendet werden, denn die Map-Funktion hat schlechte Performance.

# FlatList

FlatList ist viel schneller als Map, wenn man grosse Datensätze verarbeiten will. Sie bietet Funktionen wie Header und Footer, Trennkomponenten (zB ein Strich zwischen jedem Komponenten), mehrzeilige Items und Pull to Refresh.

## Props

### Data

Erwartet ein Array mit Daten

### RenderItem

Erwartet eine Komponente, die für jedes Item gerendert wird. Ein RenderItem entspricht also einem einzelnem Objekt in der Liste. RenderItem *muss* ein Item als Prop entgegennehmen!

# SectionList

Ist eine Liste, die in mehrere Sections unterteilt werden kann. Jede Section kann einen Header und Footer haben. Es hat die gleichen Funktionen wie eie Flatlist und ist praktisch eine Liste von FlatLists.

## Props

### Sections

Sections muss eine Liste von Objekten sein, die einen Header und eine Liste von Items/Daten enthält. So kann man verschiedene Sections definieren.

### RenderItem

Wird so wie im FlatList-Component verwendet.

### RenderSectionHeader

Its complicated…