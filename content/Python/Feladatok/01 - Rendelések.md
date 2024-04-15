
**Bemeneti adatok:**
```
2023-04-12 SZ 3
2023-04-13 BP 5
2023-04-13 DE 2
2023-04-14 SZ 1
2023-04-15 DE 4
```

Ahol:
- Az első dátum az év, hónap és nap a rendelési időpontot jelöli.
- A második elem egy városkód, amely azonosítja a rendelés helyszínét.
- A harmadik elem a rendelt termékek száma.

#### Feladatok:
1. Olvassa be és tárolja el a rendelesek.txt állomány tartalmát a további feldolgozáshoz!
2. Írja ki, hogy hány különböző városból érkezett rendelés!
3. Kérje be a felhasználótól egy dátumot, és adja meg, hogy az adott napon hány rendelés történt!
4. Jelenítse meg, melyik nap volt a legkevesebb rendelés, és mennyi rendelés történt azon a napon!
5. Számítsa ki, hogy melyik városból érkezett a legtöbb rendelés összesen, és mutassa meg ezt a várost és a rendelések számát!
6. Készítsen egy függvényt `napirendeles` néven, amely a megadott dátumra visszaadja, hogy mely városokból hány rendelés érkezett. A függvény bemeneti paramétere a dátum legyen string formátumban (pl. "2023-04-13"). A függvény visszaad egy szótárat, ahol a kulcsok a városok, az értékek pedig a rendelések száma.
7. Írja ki az összes rendelési adatot tabulátorokkal tagolt formában a képernyőre, és mentse el ugyanezt az adatot a statisztika.txt szöveges állományba.