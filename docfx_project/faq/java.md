# Java

## Wat betekent deze foutmelding? "non-static variable this cannot be referenced from a static context"

```java
Compilation error Main.java:10: error: non-static variable this cannot be referenced from a static context   
return new Fraction();
       ^
``` 

Bij bovenstaande foutmelding is het verstandig aanwijzing 2 uit de eerste Stepik les van OPT1 (nogmaals)
te lezen:

“Voor alle opdrachten geldt dat het niet de bedoeling is om een class binnen een andere class te maken.”

## Waarvoor gebruik je 'static'?

Static, ook wel statisch in het Nederlands, is eigenlijk precies het tegenovergestelde van OO (object oriëntatie).   
Een statisch methode of variabel kan je **altijd** aanroepen, ook als er geen object van een klasse is aangemaakt.
Een instance methode of variabel kan slechts aangeroepen worden als er een object van een klasse is aangemaakt.

Eerst een voorbeeld van instance methode en variabelen (OO) waarmee jullie immiddels bekent zijn:

### Instance methodes en variabelen
De klasse ```Fraction``` heeft twee instance variabelen. Namelijk:  
```private Integer nominator``` en   
```private Integer denominator```

Beide hebben ook instance **methodes**. Namelijk:  
```java 
public Integer getNominator(); 
public Integer getDenominator(); 
public void setNominator(Integer nominator); 
public void setDenominator(Integer denominator);
```

(Aan de naamgeving kan je afleiden wat de methodes zouden moeten doen.)

Elke van deze methodes en variabelen hebben een beperkte scope. Ze zijn slechts gerelateerd aan **één** object van de
klasse Fraction.

Bijvoorbeeld ```Fraction HALF = new Fraction();```   
Als wij de instance get-methodes zouden aanroepen dan zouden wij
hoogstwaarschijnlijk een nominator van 1 en een denominator van 2 krijgen.

Stel dat dezelfde methodes in ```Fraction QUARTER = new Fraction();``` aanroepen, dan krijgen wij hoogstwaarschijnlijk
nominator van 1 en denominator van 4.   
De methodes en variabelen horen dus echt maar bij één object.  

### Static methodes en variabelen
Statische methodes en variabelen doen en geven **altijd** hetzelfde terug, onafhankelijk vanuit waar ze aangeroepen
worden. Een voorbeeld:

We de klasse ```Calculator``` bevat het volgende:
```java
public static int add(int firstNumber, int secondNumber);
public static int subtract(int firstNumber, int secondNumber);
public static int multiply(int firstNumber, int secondNumber);
public static double divide(int firstNumber, intsecondNumber);
```

Je kan je wellicht voorstellen dat het niet uit maakt hoeveel objecten van ```Calculator``` je aanmaakt.   
In een optelling van *1 + 1* een zal altijd resultaat van *2* moeten teruggeven.   
Precies daarom is het soms handig om statische methodes te maken.

Overigens kan je de add-methode als volgt aanroepen: ```Calculator.add(1,1);```

Hetzelfde geld voor statische variabelen.   
Stel je wilt een website bouwen die verschillende kleuren in zijn layout gebruikt.  
Het kan handig zijn om deze kleuren in bijvoorbeeld een ArrayList te plaatsen zodat je ze later gemakkelijk
kan aanroepen.   
Eigenlijk wil je in dat geval ook dat deze ArrayList direct toegangelijk is zonder dat je eerst een
object van de bevattende klasse hoeft aan te maken.   
Dan zou je bijvoorbeeld de lijst als volgt kunnen aanmaken:

```private static ArrayList<String> colors = new ArrayList<>();```

Bij zowel de *public static methodes* in Calculator, als de *private static ArrayList* van colors is het handig dat deze niet aan
één object gebonden zijn.