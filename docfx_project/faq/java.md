# Java

## Wat betekent deze foutmelding: "non-static variable this cannot be referenced from a static context"?

```java
Compilation error Main.java:10: error: non-static variable this cannot be referenced from a static context   
return new Fraction();
       ^
``` 

Bij bovenstaande foutmelding is het verstandig aanwijzing 2 uit de eerste Stepik-les van OPT1 (nogmaals)
te lezen:

“Voor alle opdrachten geldt dat het niet de bedoeling is om een class binnen een andere class te maken”.

## Waarvoor gebruik je 'static'?

Static, ook wel statisch in het Nederlands, is eigenlijk precies het tegenovergestelde van OO (Object Oriëntatie).

Een statische methode of variabele kun je **altijd** aanroepen; ook als er geen object van een klasse is aangemaakt.
Een instance-methode of -variabele kan slechts aangeroepen worden als er een object van een klasse is aangemaakt.

Eerst een voorbeeld van een instance-methode met variabelen (OO) waarmee jullie immiddels bekend zijn.

### Instance-methodes en -variabelen
De klasse ```Fraction``` heeft twee instance-variabelen voor teller (nominator) en noemer (denominator) (in 2/3 is 2 de 
teller en 3 de noemer; teller / noemer); namelijk:  

```java 
private Integer nominator;
private Integer denominator; 
```

Beiden hebben ook instance-**methodes**; namelijk:  
```java 
public Integer getNominator (); 
public Integer getDenominator (); 
public void setNominator (Integer nominator); 
public void setDenominator (Integer denominator);
```

(uit de naamgeving kun je afleiden wat de methodes zouden moeten doen)

Elk van deze methodes en variabelen hebben een beperkte scope. Ze zijn slechts gerelateerd aan **één** object van de
klasse Fraction.

Laten we bijvoorbeeld uitgaan van de volgende declaratie:
```java
Fraction HALF = new Fraction(1, 2);
```
Als wij na deze declaratie de instance-(get-)methodes van het object ```HALF``` zouden aanroepen, dan krijgen we met
```HALF.getNominator ()``` 1 terug en met ```HALF.getDenominator ()``` 2 als resultaat.

Stel dat we en object ```QUARTER``` als volgt zouden definiëren:

```java
Fraction QUARTER = new Fraction(1, 4);
```
Dan zou de aanroep van dezelfde methodes als nominator 1 opleveren en als denominator 4.   

De methodes en variabelen horen dus echt maar bij één object.

### Static methodes en variabelen
Statische methodes en variabelen doen en geven **altijd** hetzelfde terug, onafhankelijk vanuit waar ze aangeroepen
worden. Een voorbeeld:

De klasse ```Calculator``` bevat het volgende:
```java
public static int add(int firstNumber, int secondNumber);
public static int subtract(int firstNumber, int secondNumber);
public static int multiply(int firstNumber, int secondNumber);
public static double divide(int firstNumber, intsecondNumber);
```

Je kunt je wellicht voorstellen dat het niet uitmaakt hoeveel objecten van ```Calculator``` je aanmaakt. 
Een optelling van '*1 + 1*' zal altijd het resultaat *2* op moeten leveren. Daar hoef je geen object voor te maken.  
Precies daarom is het **soms** handig om statische methodes te maken.

Overigens kun je de add-methode als volgt aanroepen:
```java
Calculator.add (1, 1);
```

Hetzelfde geldt voor statische variabelen.   
Stel dat je een website wilt bouwen die verschillende kleuren in de layout gebruikt.  
Het kan handig zijn om deze kleuren in bijvoorbeeld een ArrayList te plaatsen zodat je ze later gemakkelijk
kunt aanroepen en gebruiken.
Eigenlijk wil je in dat geval ook dat deze ArrayList direct toegangelijk is zonder dat je eerst een
object van de bevattende klasse hoeft aan te maken.   
Dan zou je bijvoorbeeld de lijst als volgt kunnen aanmaken:


Omdat deze eigenschap van ```Layout``` ```private``` is, moet een ```public``` methode ```getColors``` worden
toegevoegd om deze lijst van buiten ```Layout``` aan te kunnen roepen:

```java
ArrayList<String> colors = Layout.getColors ();
```

Bij zowel de *public static methodes* in Calculator, als de *private static ArrayList* van colors is het handig dat 
deze niet aan één object gebonden zijn.