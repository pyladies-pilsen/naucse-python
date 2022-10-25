## Jak opakovat – a neopakovat *se*

Udělej v editoru nový soubor a ulož ho jako `cykly.py`.
Budeš v něm zkoušet *cykly*.

První opakovací program, který napíšeš, bude dělat tohle:

* Stokrát po sobě:
  * Napiš "Nikdy nebudu odsazovat o tři mezery!"

Přeložené do jazyka Python to vypadá následovně:

```python
for i in range(100):
    print('Nikdy nebudu odsazovat o tři mezery!')
```

Na ono `for i in range(100)` se detailněji podíváme za chvíli,
teď to pro nás bude “hlavička”, která říká “opakuj stokrát”.

Podobnou “hlavičku” už jsi viděl{{a}} u příkazu `if`.
Stejně jako u `if` tu je na konci dvojtečka a za ní následuje
odsazený blok – *tělo* příkazu; to na co se hlavička vztahuje.
Tělo příkazu `if` se provede jen někdy;
tělo příkazu `for` se opakuje několikrát dokola.


### Seznámení se Seznamy

Než se pustíme dále do poznávání cyklu `for`, představíme si jeden datový typ, kterému se budeme podrobněji věnovat v kurzu později. Pro lepší vysvětlení a pochopení i ho ale představíme už teď. 
Jedná se tzv. `seznamy`. Pro začátek můžeš seznam chápat jako třeba nákupní seznam. Obsahuje seřazené položky (prvky), které lze měnit, upravovat, přidávat a odebírat. Vytvoříme si tedy takový malý nákupní seznam.

```python
nakupni_seznam = ["chleba","mleko","jablka","maslo","maso"]
```

Seznam je seřazený v pořadí, ve kterém byl vytvořen. Zkusíme vybrat první položku:

```pycon
>>> nakupni_seznam[0]
'chleba'
```

Seznam obsahuje pět položek a jednotlivé prvky jsou číslovány (jak je v Pythonu zvykem) od nuly. Co se ale stane, když vybereme položku mimo náš rozsah?

```pycon
>>> nakupni_seznam[5]
```

Položky lze vybírat také pomocí zvoleného rozsahu. Touto způsobu se říká *slicing*.Takto vybereš první tři položky ze seznamu. Opět ale pozor na rozsah

```pycon
>>> nakupni_seznam[0:3]
['chleba', 'mleko', 'jablka']
```

Jak to ale souvisí s cyklem `for`. Ono totiž k práci se seznamem se dokonale hodí právě cyklus `for`. V úvodu kapitoly jsme měli za úkol vypsat 100x "Nikdy nebudu odsazovat o tři mezery!". Co kdybychom si úlohu trochu modifikovali a chtěli postupně vypisovat každou z položek v nákupním seznamu?

```python
nakupni_seznam[0]
nakupni_seznam[1]
nakupni_seznam[2]
nakupni_seznam[3]
nakupni_seznam[4]
```

Nicméně tato možnost bude zejména pro dlouhé seznamy dost nepraktická. 
Přitom Pythonu stačí říct: `Pro pokožku v seznamu vytiskni položku` 

```python
for polozka in nakupni_seznam:
    print(polozka)
```

Otevírá se tím další možnost a to využití podmínek (`if` a ` else`). Předpokládejme, že nákupní seznam se jednou promění v nákup a ten budeme chtít někam uklidit. Přitom všechny položky začínající na *m* patří do lednice. Zbytek můžeme složit do spižírny. Zařadíme tedy do ` for` cyklu podmínku, která nám označí položky, které do lednice patří a které ne.

```python
for polozka in nakupni_seznam:
    if "m" in polozka:
        print(polozka + " vlozena do lednice")
    else:
        print("polozka nepatri do lednice")
```

### Range

Vraťme se k `for i in range(100)`.
Už víš, že to znamená „Pro každé <var>i</var> ze sekvence `range(100)`“.
Co je ale to `range`? Když si ho vypíšeš, nevypadne nic vysvětlujícího:

```pycon
>>> range(100)
range(0, 100)
```

Je ale použité jako „sekvence“
v <code>for <var>promenna</var> in <var>sekvence</var></code>.
Je to nějaký výčet, nějaká posloupnost hodnot.
A teď už umíš vypsat, jaké to jsou!

```python
for i in range(5):   # Doporučuju použít jen 5 místo 100
    print(i)
```

neboli česky:

* Pro každé <var>i</var> z `range(5)`:
  * Vypiš <var>i</var>

Program spusť. Jaká čísla se vypíšou? (Neboli: co je v sekvenci `range(5)`?)

{% filter solution %}
Vypíšou se čísla od 0 do 4!
Program funguje steně, jako kdybys napsal{{a}}:

```python
i = 0
print(i)

i = 1
print(i)

i = 2
print(i)

i = 3
print(i)

i = 4
print(i)
```

V sekvenci `range(5)` jsou čísla 0, 1, 2, 3 a 4. Je jich celkem pět.
{% endfilter %}

Funkce `range(n)` vrací *sekvenci čísel*.
Začíná od 0 a čísel v ní je přesně <var>n</var>.
(Na samotné <var>n</var> se tedy už nedostane.)

Často budeš potřebovat Pythonu říct, ať něco „<var>n</var>-krát zopakuje“.
Na to můžeš použít `for i in range(n)` („pro každé <var>i</var> od 0 do
<var>n</var>-1“) s tím, že proměnná <var>i</var> – „počitadlo“ – tě nezajímá.
V programu ji jednoduše nepoužiješ.

Teď by už mělo být jasné, jak funguje původní program:

```python
for i in range(100):
    print('Nikdy nebudu odsazovat o tři mezery!')
```

* Zopakuj 100krát:
  * Vypiš `'Nikdy nebudu odsazovat o tři mezery!'`

Python píše hlášky, jednu za druhou, a u toho si v promněnné <var>i</var>
počítá, jak už je daleko.

Vzpomeň si teď, jak jsme vybírali jednotlivé položky ze seznamů prostřednictvím indexu *nakupni_seznam[i]*. Takto lze procházet seznam i pomocí `for `. Rovnou si představíme metodu ` len ()`. Tato metoda vrací počet prvků v objektu. Náš seznam má pět položek a proto:

```pycon
>>> len(nakupni_seznam)
5
```

Funkci lze používat také pro jiné datové typy, například *string*.

```pycon
>>> len('Ahoj')
4
```

Náš nákupní seznam si můžeme takto vypsat s použitím indexování: 

```python
for i in range(len(nakupni_seznam)):
    print(nakupni_seznam [i])
```

> [style-note]
> Proměnná <var>i</var> se v matematice typicky používá pro *celá čísla*;
> je to zkratka z termínu *index* (číslo prvku).
> V programování se tradičně používá pro číslo průchodu cyklem,
> jako v příkladu výše.
> Pro lepší pochopení bývá dobré použít popisnější jméno proměnné, tady
> například `cislo_vypisu`; v krátkých a přehledných cyklech – a zvlášť v těch
> které proměnnou nepoužívají – se ale často setkáš s krátkým `i`, `j`, `k`…
>
> Někteří programátoři pojmenovávají ignorovanou proměnnou `_` (podtržítko).
> To je pro Python jméno jako jakékoli jiné, ničím se neliší od `i` nebo `x`:
>
>```python
>for _ in range(100):
>   print('Nikdy nebudu odsazovat o tři mezery!')
>```
