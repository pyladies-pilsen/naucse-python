{% set editor_name = 'Thonny' %}
{% set editor_url = 'https://thonny.org/' %}
{% extends lesson.slug + '/_base.md' %}

{% block name_gen %} Thonny(ho) {% endblock %}

{% block install %} 
Na Windows
si stáhni {{ editor_name }} z jeho [domovské stránky]({{ editor_url }})
a nainstaluj. Použij 64-bitovou nebo 32-bitovou verzi (ta je k dispozici pouze s Python 3.8), stejně jako v případě Pythonu.

Na Linuxu doporučujeme {{ editor_name }} nainstalovat přes `pip`, který je součástí Pythonu.
```console
$ python -m pip install thonny
```
Editor pak můžeš spustit z příkazové řádky
```console
$ thonny
```
nebo si vyrobit zkratku.
```console
$ shortcut {{ editor_name }}
```
Zkratka se vytvoří ve složce, ve které se právě nacházíš, poté ji můžeš přesunout kam chceš.
K jejímu vytvoření je třeba balík `shortcut`, ten se dá naistalovat opět pomocí pipu.
```console
$ python -m pip install shortcut
```


{% endblock %}

{% block setup %}

Jinak se v  {{ editor_name }} nemusí nic nastavovat, ani to moc nejde, funguje „z výroby“ jednoduše tak, jak má.

Odsazování a obarvování bude fungovat správně jen v souborech s koncovkou `.py`
(jako Python).
V jiných programovacích jazycích se totiž odsazuje i obarvuje jinak.

Proto jakmile v tomhle editoru vytvoříš nový soubor,
měl{{a}} bys ho co nejdřív uložit pod správným jménem.

## Spouštění programů
{{ editor_name }} není jen obyčejný editor pro psaní kódu, umí programy v Pythonu i spouštět, stačí kliknout a tlačítko Run a
kód, který máš právě otevřený se spustí, v dolní části okna se objeví výstup. Více si ukážeme na lekci.

{{ figure(img=static('thonny-run.png'), alt="Thonny run") }}

{% endblock %}