
**Bemeneti adatok:**
```
12:35 5.6 L
14:20 7.2 M
15:55 5.4 S
12:40 6.8 M
15:10 5.2 L
```

Ahol:
- Az első rész az időpont (óra:perc),
- A második a mért hőmérséklet Celsius-ban,
- A harmadik betű a mérési pont helyszínét jelölő kód.

#### Feladatok:
1. Olvassa be és tárolja el a homerseklet.txt állomány tartalmát a további feldolgozáshoz!
2. Jelenítse meg, hogy hány különböző mérési ponton történt mérés!
3. Kérdezze meg a felhasználótól egy időpontot (óra:perc formátumban), és adja meg, hogy ebben az időpontban milyen hőmérsékleteket mértek és hol!
4. Határozza meg és írja ki, melyik mérési ponton volt a nap legmagasabb hőmérséklete, és mennyi volt az!
5. Számítsa ki, hogy melyik mérési pont átlaghőmérséklete volt a legkisebb, és mutassa meg ezt az értéket és a helyszínt!
6. Készítsen egy `homerseklet_adott_idoben` nevű függvényt, amely paraméterként egy időpontot (óra:perc) kap, és visszaadja, hogy abban az időpontban mely helyszíneken mértek hőmérsékletet és milyen értékeket. A függvény visszaad egy listát, amely minden mérési helyszínre tartalmaz egy tuple-t az időponttal és a mért hőmérséklettel.
7. Állítson elő egy összefoglaló jelentést, amely tartalmazza minden mérési ponton az összes mért hőmérséklet átlagát, minimumát és maximumát. Az eredményeket jelenítse meg a képernyőn, és mentse el egy summary.txt nevű állományba.