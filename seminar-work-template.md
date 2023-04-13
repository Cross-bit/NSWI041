# Studentský informační systém - Modul rozvrhy

Modul rozvrhy slouží k vytváření a prohlížení rozvrhů. 
V rámci modulu jsou vedeny předměty a jejich příslušnost do studijních programů a jednotlivých semestrů studia, 
ve kterých jsou v rámci programu doporučeny. 
Dále jsou v rámci modulu vedeny učebny pro výuku a jejich kapacita. 
Pro každý předmět jsou evidovány rozvrhové lístky přednášek a cvičení, včetně jejich kapacit a vyučujících. 
Modul umožňuje rozvrhové komisi v jednotlivých semestrech vytváření centrálních rozvrhů přiřazováním rozvrhových lístků k učebnám na konkrétní den v týdnu a hodinu. 
Předměty ve stejném studijním programu a semestru musí být rozvrhovány tak, aby měli studenti v daném studijním programu a semestru možnost tyto předměty navštěvovat. 
Dále nesmí docházet k časovým kolizím jednoho učitele. 
Modul umožňuje vytvářet statistické reporty o vytíženosti místností v jednotlivých semestrech. 

## Funkční požadavky

### Slovník

Rozvrhový lístek = základní jednotka rovržení výuky předmětu, určuje čas a místo výuky, výuku předmětu zajišťuje učitel, který je uveden v rozvrhovém lístku. Rozvrhový 
lístek je vytvořen pro každý předmět, který se vyučuje v daném semestru.

### Uživatelské požadavky
**TODO:**

- Každý opravit svých 5 uživatelský požadavků.

- Vybrat si 2 uživatelké požadavky/skupiny požadavků (viz Markovy poznámky na messengeru) a zabrat si je připsáním jména k požadavku.

- Rozepsat požadavky do use casů (z toho dva detailně) a případně specifikovat entity s atributy (viz poznámky).


Ondřej
1) Děkanát potřebuje mít možnost vytvořit předmět, aby rozvrhová komise mohla vytvořit rozvrhové lístky danému předmětu.

2) Děkanát potřebuje mít možnost upravit předmět, aby pokud dojde ke změnám v daném předmětu(např. změna názvu), rozvrhová komise pracovala s aktuálními daty.

3) Děkanát potřebuje mít možnost smazat předmět, aby pokud se daný předmět zruší, nebyl již v systému dále registrovaný a rozvrhová komise k tomuto předmětu nevytvářela rozvrhové lístky.

4) Děkanát by měl být schopen specifikovat příslušnost předmětu do studijního programu a prerekvizity, korekvizity... předmětu, aby studenti při zápisu věděli, zdali mají již všechny potřebné znalosti pro tento předmět.

##TODO: Use case pro 5, 6, 7? 
5) Rozvrhová komise by měla být schopna vytvořit rozvhový lístek, aby se studenti mohli na daný předmět zapsat.

6) Rozvrhová komise by měla být schopna smazat rozvhový lístek, aby se studenti na příslušný předmět nemohli zapisovat, pokud dojde ke zrušení předmětu, ke kterému je tento lístek určen.

7) Rozvrhová komise by měla být schopna upravit rozvhový lístek, aby pokud vznikne při vytváření lístku chyba v obsahu, mohl být lístek upraven a studenti měli aktuální platná data.

8) Děkanát by měl být schopen zaevidovat, smazat, upravit místo (areál ve kterém výuka bude probíhat), aby:
   - Se mohla k místu přiřadit učebna a provést kontrala návaznosti rovržení výuky
   - Studenti a učitelé věděli, kam se mají dostavit na výuku.
   - Rozvrhová komise mohla dát předměty pro stejný studijní program a semestr na jedno místo.

9) Děkanát by měl být schopen zobrazit seznam všech učeben, aby věděl jaké učebny a k jakým místům eviduje.

10)  Děkanát by měl být schopen zaevidovat do systému učebnu, tj. přiradit ji k místu a specifikovat její kapacitu, aby ji rozvrhová komise mohla přidělit jednotlivým rozvrhovým lístkům a studenti a učitelé věděli kde budou mít výuku.

### Marek

#### Use case scenario: Specifikace (vytvoření) průběhu doporučeného průběhu studia

**Hlavní aktér:** `Děkanát`
**Cíl:** Navrhnout doporučený průběh studia pro studenty s ohledem na prerekvizity a požadavky studijního programu.

**Precondition**
- `Uživatel` je přihlášen jako člen děkanátu a je v podsekci modulu rozvrhy
`Doporučené průběhy`.
- Informace o prerekvizitách a požadavcích studijního programu jsou dostupné.

**Normální scénář**
1. `Děkanát` otevře sekci pro vytvoření doporučeného průběhu studia.
2. Systém zobrazí všechny studijní programy
3. Děkanát vybere studijní program, pro který chce vytvořit doporučený průběh studia.
4. Software získá seznam předmětů a informace o prerekvizitách z databáze nebo systému spravujícího studijní plány. Informace o všech předmětech jsou zobrazeny spolu s ich prerekvizitami formou grafu nebo běžného seznamu.
5. `Děkanát` analyzuje jednotlivé předměty a jejich prerekvizity, aby zjistil, v jakém pořadí je studenti musí absolvovat.
6. `Děkanát` zohlední požadavky studijního programu, jako je minimální a maximální počet kreditů, povinné předměty, volitelné předměty a další specifické požadavky.
7. `Děkanát` navrhne doporučený průběh studia pomocí grafického rozhraní, které umožňuje přetahování předmětů z listu nebo grafu do jednotlivých semestrů a automaticky kontroluje splnění prerekvizit a požadavků studijního programu. Akonáhle je předmět už umístěn v nejakém semestru, v listu (nebo grafu), ze kterého byl přetáhnutý je vyšednutý a druhýkrát se už přetáhnut nedá.
8. Počas přetahování předmětů jsou předměty neustále kontrolovány na prerekvizity. Akonáhle je předmět umístnený bez prerekvizit, uživatel je patrične upozornen.
9. Po navržení doporučeného průběhu studia grafické rozhraní zobrazí děkanátu přehledný plán s jednotlivými semestry a přiřazenými předměty.
10. `Děkanát` zkontroluje navržený průběh studia s ohledem na splnění všech požadavků a prerekvizit.
11. `Děkanát` potvrdí návrh doporučeného průběhu studia v systému pomocí tlačítka `"Uložit"`.
12. Systém uloží doporučený průběh studia.
13. Po uložení se uživateli zobrazí možnost `"editovat"`, `"zveřejnit"` nebo `"zmazat"`studijní plán.
14. Po kliknutí na zveřejnit se studijní plán zveřejní pro studenty.

**Alternativní scénář:**

4. `Děkanát` zjistí, že některé informace o prerekvizitách nebo požadavcích studijního programu chybí nebo jsou neaktuální:
- `Děkanát` aktualizuje chybějící nebo neaktuální informace přímo v grafickém rozhraní a pokračuje v kroku `4` normálního scénáře.

9. `Děkanát` zjistí, že navržený průběh studia nesplňuje všechny požadavky nebo prerekvizity:
- `Děkanát` upraví doporučený průběh studia přímo v grafickém rozhraní. Poté pokračuje v kroku `9` normálního scénáře.

**Stav systému po dokončení operace:**

- Systém obsahuje aktualizovaný, případně zveřejněný doporučený průběh studia, který splňuje všechny požadavky a prerekvizity studijního programu.
- Studenti mají přístup k doporučenému průběhu studia přes systém, který jim pomáhá plánovat a organizovat své studium.
- Děkanát může v případě potřeby snadno aktualizovat libovolný doporučený průběh studia pro libovolný studijní program.

```plantuml
@startuml
left to right direction

actor "Děkanát" as Dekanat
actor "Student" as Student

package "Modul rozvrhy" {
  package "Vytvoření doporučeného průběhu studia" {
    usecase "Zvolení studijního programu" as UC1
    usecase "Vytvoření doporučeného průběhu studia" as UC2
    usecase "Přidávaní predmětů programu do semestrov studia" as UC3
    usecase "Kontrolování prerekvizit predmětů" as UC4
    usecase "Uložení doporučeného průběhu studia" as UC5
    usecase "Zveřejnit doporučeného průběhu studia" as UC6
    usecase "Zobrazit doporučený průběh studia" as UC7
  }
}

Dekanat --> UC1
Dekanat --> UC2
Dekanat --> UC3
Dekanat --> UC4
Dekanat --> UC5
Dekanat --> UC6

UC7 <-- Student

@enduml
```

#### Use case scenario: Specifikace harmonogramu

**Hlavní aktér:** `Děkanát`
**Cíl:** Navrhnout harmonogram akademického roku pro studenty, vyučující a ostatní zaměstnance školy s ohledem na začátek a konec výuky, zkoušková období a prázdniny.

**Precodition**
- Uživatel je přihlášen jako člen děkanátu, má přístup k modulu rozvrhů a je v podsekci `Doporučené průběhy`.
- Systém umožňuje zadávat a ukládat informace o harmonogramu akademického roku.

**Normální scénář**
1. `Děkanát` otevře sekci pro specifikaci harmonogramu v modulu rozvrhů, kliknutím na tlačítko `"Harmonogramy"`.
2. Systém zobrazí list všech už specifikovaných harmonogramů pro jednotlivé roky. Uživatel si může vyfiltrovat jenom nadcházející roky. Nad listom harmonogramů je tlačítko pro vytvoření nového harmonogramu.
3. `Děkanát` zvolí vytvoření nového harmonogramu.
4. Systém zobrazí interaktivní formulář, který umožňuje zadávat data začátku a koncu semestrů, zkouškových období a prázdnin. Takisto se zobrazí možnost vybrat datumy, kdy se provedou automatické kontroly.
5. Po zadání dat probehně kontrola, zda jsou data správně zadaná a nejsou v rozporu s předpisy školy nebo zákonem.
6. Pokud jsou data správně zadána, `Děkanát` uloží harmonogram pomocí tlačítka `"Uložit"`. Takýto harmonogra je zatím přístupný jenom `Děkanátu`.
7. Systém uloží harmonogram a zobrazí potvrzení o úspěšném uložení.
8. Po uložení se uživateli zobrazí možnost `"editovat"`, `"zveřejnit"` nebo `"zmazat"` harmonogram.
9. Po zvolení `"zveřejnit"` se tento harmonogram stane volne dostupným pro přihlášených použivatelů.

**Alternativní scénář:**
6. Po uložení harmonogramu si děkanát uvědomí, že potřebuje provést další úpravy:
- `Děkanát` se vrátí zpět do sekce pro specifikaci harmonogramu, upraví harmonogram podle potřeby a znovu ho uloží, následuje krok `6` normálniho scénáře.
7. Uživatel chce vytvořit harmonogram který se datumami už překrývá s jiným již vytvořeným harmonogramem. Nebo je nekterá kombinace datumů nesprávná ( napr. konec semestru je dřív než začátek ). Systém ho na tento problém upozorní a následuje krok `5` normálniho scenáře.

**Stav systému po dokončení operace:**
- Systém obsahuje uložený, případně aktualizovaný harmonogram akademického roku, který zohledňuje výuku, zkoušková období a prázdniny.
- Studenti, vyučující a ostatní zaměstnanci mají přístup k harmonogramu a mohou tak plánovat své aktivity v průběhu akademického roku.
- Zobrazení rozvrhů v systému je aktualizováno na základě uloženého harmonogramu.

```plantuml
@startuml
left to right direction

actor "Děkanát" as Dekanat
actor "Student" as Student

package "Modul rozvrhy" {
  package "Specifikace harmonogramu" {
    usecase "Vytvoření nového harmonogramu" as UC1
    usecase "Zadání dat začátku a konce semestru, zkouškových období, \nprázdnin a datumov automatických kontrol" as UC2
    usecase "Kontrola zadaných dat daného harmonogramu" as UC3
    usecase "Uložení harmonogramu" as UC4
    usecase "Úprava harmonogramu" as UC5
    usecase "Zveřejnění harmonogramu" as UC6
    usecase "Zobrazit všechny harmonogramy" as UC7
    usecase "Zobrazit harmonogram" as UC8
  }
}

Dekanat --> UC1
Dekanat --> UC2
Dekanat --> UC3
Dekanat --> UC4
Dekanat --> UC5
Dekanat --> UC6
Dekanat --> UC7
Dekanat --> UC8

UC8 <-- Student

@enduml
```

#### Use case scenario: Kontrola rozvrhu 

**Hlavní aktér:** `Student`, `Učitel` společne jako `Uživatel`.
**Cíl:** Zkontrolovat osobní rozvrh pro zjištění časů výuky předmětů, které student navštěvuje v průběhu semestru.

**Předpoklady**
- `Uživatel` je přihlášen do systému.
- V rozvrhu pro daný semestr má alespoň jeden rozvrženej předmět.

**Normální scénář**
- `Uživatel` otevře modul rozvrhů a zvolí možnost zobrazit svůj osobní rozvrh.
- `Uživatel` zobrazí osobní rozvrh `Uživatele`, který zahrnuje časy a místa výuky předmětů, které `Uživatel` navštěvuje/bude navštěvovat v průběhu semestru.
- `Uživatel` klikne na tlačítko `Kontrola rozvrhu`.
- Systém spustí kontrolu kolizí předmětů. Kolize může být buď časová (předměty se překrývají), nebo dopravní (předměty se konají na místech, které se nedají stihnout po skončení výuky prvního předmětu).

**Stav systému po dokončení operace:**
- `Uživatel` je oboznámen s výsledkem. Může se tedy rozhodnout svůj rozvrh změnit.

#### Use case scenario: Kontrola dodržení doporučeného průběhu studia 

**Hlavní aktér:** `Systém`.
**Cíl:** Systém automaticky zkontroluje, zda student splnil všechny povinné předměty v doporučených semestrech a zda má zapsané doporučené předměty pro daný semestr. Datumy a časy automatických kontrol jsou nastavovány při navrhování harmonogramu pro daný rok.

**Předpoklady**
- Doporučený průběh studia pro studijní program studenta je zveřejněn.
- Systém má aktuální informace o předmětech, které student splnil a zapsal.

**Normální scénář**
- Systém automaticky provádí kontrolu dodržení doporučeného průběhu studia pro každého studenta na základě jeho studijního programu a aktuálního semestru.
- Systém zkontroluje, zda student splnil všechny povinné předměty v doporučených semestrech dle studijního programu.
- Systém zkontroluje, zda student má zapsané doporučené předměty pro aktuální semestr.
- Pokud student splnil všechny povinné předměty v doporučených semestrech a má zapsané doporučené předměty pro aktuální semestr, systém zaznamená, že student dodržuje doporučený průběh studia.
- V případě, že student nesplnil některé z povinných předmětů v doporučených semestrech nebo nemá zapsané doporučené předměty pro aktuální semestr, systém studenta upozorní a dodá mu seznam předmětů, které by mal mít už splněné.

**Stav systému po dokončení operace:**
- Systém obsahuje aktuální informace o tom, zda student dodržuje doporučený průběh studia pro svůj studijní program.
- V případě nesplnění kritérií může systém informovat studenta nebo studijní oddělení o potřebě řešit problém.

```plantuml
@startuml
left to right direction

'======== Actors ========
actor Student
actor Učitel
actor Děkanát

'======== Use Cases ========
package "Modul rozvrhy" {
  package "Manuální kontroly" {
    usecase "Kontrola kolizí svého rozvrhu" as UC2
  }

  Package "Automatické kontroly" {
    usecase "Kontrola doporučeného průběhu studia" as UC1
    usecase "?????????????????????????Kontrola kolizí rozvrhu učebny\nTODO: TO ZE NEJSOU V UCEBNE DVA TERMINY VE STEJNOU DOBU PRI ROZVRHOVANI DANEHO PREDMETU - \nVTEDY HO TO ROVNO UPOZORNI A NEBUDE AKO AUTOMATICKA KONTROLA" as UC3
  }
}

'======== Use case links ========
Student --> UC1
Student --> UC2
Učitel --> UC2

'Right hand side
UC1 <-- Děkanát
UC3 <-- Děkanát
@enduml
```


Šimon
- Jako děkanát potřebujeme automatickou kontrolu, že doporučený průběh studia odpovídá prerekvizitám, abychom věděli, jestli jsme doporučený rozvrh navrhli tak, aby studenti byli schopni ho použít.

- Jako student nebo učitel potřebuju exportovat svůj rozvrh, abych si ho mohl dát do kalendáře.
- Jako student nebo učitel potřebuju zobrazit svůj rozvrh, abych věděl, kdy a kde mám být.
- Jako student nebo učitel potřebuju zobrazit rozvrh jiného učitele, abych věděl, kdy se s ním můžu sejít.
- Jako rozvrhová komise potřebujeme zobrazit rozvrh jakéhokoli učitele, abychom věděli, jestli jsme k rozvrhovým lístkům přiřadili správné učitele.

Michael
- Jako student si musím být schopen zobrazit rozvrh předmětu, abych si mohl vybrat pro mě vhodnou paralelku přednášky či konkrétní vhodné cvičení.
- Jako student si musím být schopen zobrazit rozvrh rozvrhového lístku, abych se mohl rozhodnout zda mi vyhovuje.
- Jako student bych měl mít možnost nechat si zasílat upozornění na změnu ve výuce, abych věděl, kdy a kam mám přijít.
- Jako děkanát si musíme být schopni zobrazit rozvrh předmětu, abychom mohli kontrolovat, zda probíhá výuka.
- Jako rozvrhová komise si musíme být schopni zobrazit rozvrh předmětu, abychom mohli kontrolovat, jestli jsme rozvrhové lístky naplánovali na dostatečné množství různých termínů.
- Jako rozvrhová komise si musíme být schopni zobrazit rozvrh rozvrhového lístku, abychom mohli zkontrolovat, že daný rozvrhový lístek dává smysl (jednotlivé části se nepřekryjí atd.).
- Jako učitel potřebuji mít možnost zrušit svou výuku v daném termínu, abych dal vědět účastníkům výuky, že se nemusí dostavit.
- Jako děkanát bychom měli mít možnost si nechat automaticky vygenerovat statický report o vytížení místností v jednotlivých semestrech, abychom mohli dělat orgranizační rozhodnutí na základě těchto dat (úprava vytápění místností, zajištění nových prostor atd.).
- Jako rozvrhová komise bychom měli mít možnost si nechat automaticky vygenerovat statický report o vytížení místností v jednotlivých semestrech, abychom mohli lépe rozvrhovat výuku na základě těchto dat. Michael

### Systémové požadavky

[*Document here your system requirements as use case diagrams.*]

### Ondřej

#### Use case scenario: Vytvoření předmětu děkanátem

**Precondition**
`Uživatel` je přihlášen jako člen děkanátu a je v podsekci modulu rozvrhy
`Předměty`.

**Normal**
1. `Uživatel` zvolí možnost `Upravit existující předmět` a otevře se mu subsekce (formulář) pro tvorbu nového předmětu – `Nový předmět`.
2. `Uživatel` v rámci tvorby dá předmětu název a vyplní další pvinné informace.TODO: přidat do diagramu (název semestr atd.??)??
3. Když uživatel zadá hodnotu, provede se kontrola vstupu.
4. V rámci vyplňování `uživatel` přiřadí předmět do konkrétních studijních programů.
5. `Uživatel` může u předmětu specifikovat prerekvizity a korekvizity z nabídky existujících předmětů.
  
**Alternativní scénáře**
- Pokud dojde při validaci povinných dat k chybě uživatel je na tuto chybu upozorněn a vyzván k opravě.
- Pokud jsou všechna pole validní a uživatel opustí podsekci `Nový předmět`, předmět je přidán do systému.

**Stav systému po dokončení operace**
Nově vytvořená učebna je v systému úspěšně evidovaná a `uživatel` si ji může zobrazit v seznamu všech učeben v sekci `Předměty`


#### Use case scenario: Evidence učebny děkanátem
**Precondition**

Uživatel je přihlášen jako člen děkanátu a systému eviduje `místo`, člen otevřel sekci Evidence učeben a míst v modulu rozvrhy.

**Normal**
1. `Děkanát` zadá pokyn vytvoření nového záznamu učebny.
2. `Děkanát` specifikuje kapacitu učebny.
3. Provede se kontrola vstupních údajů případně `děkanát` může kdykoliv tuto kontrolu provést manuálně pomocí možnosti `Kontrola vstupních údajů`.
4. `Děkanát` zadá evidovat učebnu k místu a přidá existující místo z nabídky, kterou mu systém poskytne.
5. Opět se provede kontrola vstupních údajů zdali místo bylo vyplněno.
6. Uživatel opustí podsekci `List evidence učebny`.


**Alternativní scénáře**
- Uživatel zadá do kapacity učebny nesprávnou hodnotu(obsahuje např. text) a při kontrole je informován o neplatnosti zadaných údajů. Uživatel může chybu opravit zadáním kapacity ve správném formátu.
- Uživatel chce k učebně přiřadit místo, ale to v systému neexistuje. Uživatel tedy před zadáním místnosti musí tuto místnost vytvořit.
- Pokdu nejsou všechna data vyplněna, nebo vstupy obasahují neplatná data,
uložení učebny při výstupu z podsekce `List evidence učebny` selže.

**Stav systému po dokončení operace**
Nově vytvořená učebna je v systému úspěšně evidovaná a `děkanát` si ji může zobrazit v seznamu všech učeben.
Pokud data byla při opouštění sekce `List evidence učebny` nevalidní učebna není v systému evidována.
Managování předmětů (takové to vytvořit+smazat+upravit + ještě doporučený rozvrh + prerekvizity)


#### Šimon

#### Use case scenario: Provedení kontroly doporučeného rozvrhu děkanátem

**Precondition**
`Uživatel` je přihlášen jako člen `děkanátu` a je v podsekci modulu rozvrhy `Kontroly`.

**Normal**
1. `Uživatel` zvolí možnost `Provést kontrolu doporučeného průběhu studia`.
2. `Uživatel` otevře se formulář pro specifikaci kontroly, například pro který studijní program má kontrola být provedena.
3. Když `uživatel` formulář vyplní, začne se provádět kontrola.
4. `Uživatel` si může kontrolu prohlídnout v podsekci 
5. Po provedení kontroly uživatel dostane výsledek kontroly, včetně seznamu všech nalezených chyb.

**Alternativní scénáře**
- Po odeslání kontroly ji může `uživatel` zrušit, pokud ještě nedoběhla. V tomto případě je výsledek kontroly `zrušená`.

**Stav systému po dokončení operace**
Dokončená kontrola má stav `úspěšná`, `neúspěšná` a `zrušená`. `Uživatel` si ji může prohlédnout v podsekci modulu rozvrhy `Kontroly/Seznam`. Uživatel si může prohlídout seznam všech nalezených chyb.

#### Use case scenario: Export svého rozvrhu

**Precondition**
`Uživatel` je přihlášen jako `student` nebo `učitel` a je v podsekci modulu rozvrhy `Zobrazit`.

**Normal**
1. `Uživatel` zvolí možnost `Exportovat`.
2. Zobrazí se formulář pro určení formátu rozvrhu. `Uživatel` ho vyplní.
3. Po odeslání formuláře se `uživateli` stáhne soubor s exportovanými daty.

**Alternativní scénáře**
- Pokud zrovna neprobíhá žádná výuka, které se `uživatel` účastní, tak je upozorněn a akce skončí. 

**Stav systému po dokončení operace**
Akce neovlivní stav systému. Uživatel má soubor s exportovanými daty ve svém počítači.

Managování míst


Harmonogram (harmonogram rozvrhovou komisí + když profesor zruší předmět v 1 den)

Zobrazení rozvrhu
```plantuml
@startuml
left to right direction

'======== Actors ========
actor Student
actor "Student nebo učitel" as SU
actor Děkanát
actor "Rozvrhová komise" as RK

'======== Use Cases ========
package "Modul rozvrhy" {
  Package "Zobrazení rozvrhu" {
    usecase "Zobrazit rovrh předmětu" as UCP1
    usecase "Zobrazit rozvrh rozvrhového lístku" as UCP3
    usecase "Zobrazit rozvrh jakéhokoli profesora" as UCP4
    usecase "Zobrazit svůj rozvrh" as UCP2
  }
}

'======== Use case links ========
Student --> UCP1
SU --> UCP2
SU --> UCP3
SU --> UCP4

'Right hand side
UCP1 <-- Děkanát
UCP4 <-- RK
UCP3 <-- RK
UCP1 <-- RK
@enduml
```

Výstupy (export, statistika atd...)
```plantuml
@startuml
left to right direction

'======== Actors ========
actor Děkanát
actor "Rozvrhová komise" as RK

'======== Use Cases ========
package "Modul rozvrhy" {
  Package Reporty {
    usecase "Vytvoření reportu o využití místností" as UCA1
  }
  Package Exporty {
    usecase "Export svého rozvrhu" as UCB1
  }
}

'======== Use case links ========
Student --> UCB1
Učitel --> UCB1

UCA1 <-- Děkanát
UCA1 <-- RK
@enduml
```

#### Use case scenario
**Precondition**

Uživatel je přihlášen jako člen děkanátu

**Normal**

1. Otevře si `Modul rozvrhy`.
2. Vybere podsekci `Výstupy`.
3. Zvolí možnost `Vytvoření reportu o využití místností`.
4. Vybere si, za které semestry chce vygenerovat daný report.
5. Systém zkontroluje, že je zvolený nějaký semestr.
6. Systém vygeneruje report.
7. Uživatel si stáhne daný report.

**Alternativní scénáře**
- Uživatel nezvolil žádné období (semestr). V tom případě je vyzván ke zvolení nějakého období.
- Nastane chyba při zpracování dat. V tom případě se chyba zaloguje a uživatel je o ní informován.

**Stav systému po dokončení operace**
- Uživatel si úspěšně uložil vygenerovaný report.
- Při zpracování nastala chyba a tato chyba byla zalogována pro další šetření.


```plantuml
@startuml
left to right direction

'======== Actors ========
actor Student
actor Učitel

'======== Use Cases ========
package "Modul rozvrhy" {
  Package "Můj rozvrh"{
    usecase "Zrušit výuku" as UCMR1
    usecase "Upozornit na změnu ve výuce" as UCMR2
  }
}

'======== Use case links ========
Učitel --> UCMR1
Student --> UCMR2
UCMR1 .> UCMR2 : << extends >>

@enduml
```


#### Actors

[*Document here all actors from the use case diagrams. Make a subsection for each actor and their short description in each subsection.*]


##### [*Actor name*]

Děkanát = Je výkonný orgán řízení fakulty po stránce hospodářské a administrativní.

Rozvrhová komise = Poradní orgán pro děkanát, který se zabývá vytvářením předmětů.

Uživatel = Osoba, která má přístup do univerzitního systému.

Student = Osoba, která je zapsána ke studiu.

Učitel = Osoba, která vyučuje předmět.


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




```plantuml
@startuml

' ======= the actors =========

actor :Left 1: as Left1 << Human >> #f8fdff
actor :Right 1: as Right1 << Stereotype >>
actor :Left 2: as Left2 << Human >> #eaf0f9

actor :Left 3: as Left3 << Human >> #eaf0f9
actor :Left 4: as Left4 << Human >> #eaf0f9

actor :Left 5: as Left5  #eaf0f9
actor :Right 3: as Right3  #eaf0f9
actor :Right 2: as Right2  #eaf0f9

rectangle "My Rectangle" #C0C0C0 {
    left to right direction

    ' ====== the use cases =========

    (Use case A) as (UseCaseA) #83d3f6
    (Use case B) as (UseCaseB) #83d3f6
    (Use case C) as (UseCaseC) #83d3f6
    (Use case D) as (UseCaseD) #83d3f6
    (Use case E) as (UseCaseE) #83d3f6

    (Use case F) as (UseCaseF) #7a97ca
    (Use case G) as (UseCaseG) #7a97ca
    (Use case H) as (UseCaseH) #7a97ca

    (Use case I) as (UseCaseI) #ffcb0c
    (Use case J) as (UseCaseJ) #ffcb0c
    (Use case K) as (UseCaseK) #ffcb0c
    (Use case L) as (UseCaseL) #ffcb0c

    ' Prevent PlantUML from re-ordering these items
    together {
        (Use case M) as (UseCaseM) #a4e148
        (Use case N) as (UseCaseN) #a4e148
        (Use case O) as (UseCaseO) #a4e148
    }

    ' ==== the use case links. Note '---' means longer line ======

    ' These Actors are positioned on the left hand side.
    ' Note the Actor is referenced first, and the Use-Case second.
    Left1 --- (UseCaseA)
    Left1 -- (UseCaseB)
    Left1 -- (UseCaseC)
    Left1 -- (UseCaseD)
    Left1 -- (UseCaseE)

    Left2 -- (UseCaseF)
    Left2 -- (UseCaseG)
    (UseCaseF) .> (UseCaseA) : << extends >>
    (UseCaseG) .> (UseCaseA) : << extends >>

    Left3 -- (UseCaseG)
    Left3 -- (UseCaseH)
    (UseCaseH) .> (UseCaseD) : << extends >>

    Left4 -- (UseCaseI)
    Left4 -- (UseCaseJ)
    Left4 -- (UseCaseK)
    Left4 -- (UseCaseL)

    Left5 -- (UseCaseM)

    ' These dotted lines will cause a better placement of the
    ' Use-Cases, compared to using the normal non-dotted lines.
    (UseCaseM) <. (UseCaseN)
    (UseCaseO) .> (UseCaseM)

    ' These Actors are positioned on the right hand side.
    ' Note the Use-Case is referenced first, and the Actor second.
    (UseCaseN) --- Right3
    (UseCaseA) --- Right1
    (UseCaseD) --- Right2
}

@enduml
```

