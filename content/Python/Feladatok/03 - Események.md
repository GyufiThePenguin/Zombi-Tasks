**Bemeneti adatok:**
```
2023-04-12, 101234567, 12:30, H
2023-04-13, 101234568, 15:45, T
2023-04-14, 101234569, 11:00, H
2023-04-15, 101234570, 14:20, M
2023-04-16, 101234571, 16:35, T
```

Ahol:
- Az első rész a dátum (év-hónap-nap),
- A második rész egy egyedi azonosító szám,
- A harmadik rész az időpont (óra:perc),
- A negyedik rész az esemény típusát jelölő kód (H: Hírek, T: Technológia, M: Művészet).

#### Feladatok:
1. Olvassa be és tárolja el az esemenyek.txt állomány tartalmát a további feldolgozáshoz!
2. Jelenítse meg, hány különböző típusú esemény történt összesen!
3. Kérdezze meg a felhasználótól egy dátumot (év-hónap-nap formátumban), és adja meg, hogy azon a napon milyen típusú események történtek!
4. Határozza meg és írja ki, melyik eseménytípusból volt a legtöbb az adatok alapján, és hány esemény tartozik ehhez a típushoz!
5. Számítsa ki és jelenítse meg, hogy az egyes eseménytípusokra átlagosan mennyi idő jut egy hónapban!
6. Készítsen egy `esemeny_napok` nevű függvényt, amely paraméterként egy esemény típuskódot (pl. 'H') kap, és visszaadja azokat a napokat, amikor ilyen típusú esemény történt. A függvény egy listában adja vissza az érintett dátumokat.
7. Állítson elő egy összefoglaló jelentést, amely tartalmazza az összes esemény időpontját és típusát, rendezve dátum szerint. Az eredményeket jelenítse meg a képernyőn, és mentse el egy rendezvenyek_osszefoglalo.txt nevű állományba.
