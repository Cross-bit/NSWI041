# Student information system - Modul rozvrhy

[*Module description*]

## Functional Requirements

This section specifies the functional requirements.

### User requirements

- (Zjistit, jestli máme řešit něco na vyšší úrovni, než předmět.)
- Vytvořit, smazat, upravit předmět
  - Příslušnost do studijního programu
  - Prerekvizity
- Vytvořit, smazat, upravit rozvrhový lístek
  - Rozvrhový lístek se skládá z rozvrhových termínů

- Vytvořit, smazat, upravit místo
- Vytvořit, smazat, upravit učebnu

- Specifikace doporučeného průběhu studia

- Specifikace harmonogramu (semestru)

- Kontroly
  - Učitel může navštěvovat všechny termíny
  - Studenti můžou navštěvovat všechny termíny na povinné předměty
  - V učebně nejsou dva termíny ve stejnou dobu
  - Doporučený průběh studia odpovídá prerekvizitám

- Zobrazení rozvrhu
  - Rozvrh studenta
  - Rozvrh učitele
  - Rozvrh předmětu
  - Rozvrh učebny
  - Rozvrh lístku

- Statický report o vytížení místností v jednotlivých semestrech

### System requirements

[*Document here your system requirements as use case diagrams.*]
větší detail než user requirements¨
jak ten samotný systéme funguje 


#### Actors

[*Document here all actors from the use case diagrams. Make a subsection for each actor and their short description in each subsection.*]

osoby interagující se systémem 
(né všichni učitelé jsou zaměstnanci)


##### [*Actor name*]

[*Actor description*]

#### Use cases

[*Document here all use cases. Create a subsection for each use case diagram. If you have only one use case diagram, you do not need a special subsection*]

##### [*Use case diagram title*]

[*Use case diagram in PlantUML*]

```plantuml
@startuml
left to right direction
actor Guest as g
package Professional {
  actor Chef as c
  actor "Food Critic" as fc
}
package Restaurant {
  usecase "Eat Food" as UC1
  usecase "Pay for Food" as UC2
  usecase "Drink" as UC3
  usecase "Review" as UC4
  usecase "Cook Food" as UC5
}
c --> UC5
fc --> UC4
g --> UC1
g --> UC2
g --> UC3
@enduml
```

To be able to embed PlantUML diagrams to Markdown code with previews in VSCode you need
* Markdown All in One extension
* PlantUML extension
* Mardown Plantuml Preview extension

Follow https://plantuml.com/

[*Describe the diagram in a short paragraph. Describe each use case from the diagram in the detail from the lecture in a separate subsection.*]

###### [*Use case title*]

[*Use case description in the structure from the lecture.*]

[*Add an activity diagram for one use case per a team member*]

## Information model

[*Express the information model of the domain as a UML class diagram in PlantUML. Do not use class methods in the diagram, only classes, class attributes and associations connecting classes.*]

```plantuml
@startuml
class Car

Driver - Car : drives >
Car *- Wheel : have 4 >
Car -- Person : < owns
@enduml
```

[*Document each class with a short description in a separate subsection*]
navíc description entit co skutečně znamenají
### [*Class name*]

[*Class description*]
