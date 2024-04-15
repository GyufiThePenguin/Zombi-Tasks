**Bemeneti adatok:**
```
2023-04-12, "AB123", "Start", 14:30
2023-04-12, "AB123", "End", 16:45
2023-04-13, "CD456", "Start", 09:15
2023-04-13, "CD456", "End", 11:30
2023-04-14, "EF789", "Start", 12:00
2023-04-14, "EF789", "End", 14:15
```

Ahol:
- Az első rész a dátum (év-hónap-nap),
- A második rész egy egyedi azonosító szám a tevékenységhez,
- A harmadik rész az esemény típusa ("Start" vagy "End"),
- A negyedik rész az időpont (óra:perc).

#### Feladatok:
1. Olvassa be és tárolja el az esemenyek.txt állomány tartalmát a további feldolgozáshoz!
2. Számolja meg és jelenítse meg, hány különböző esemény azonosító szerepel az adatokban!
3. Készítsen egy függvényt, amely kiszámítja egy adott azonosítójú esemény teljes időtartamát percben. A függvény paraméterként az azonosító számot kapja, és az összes releváns "Start" és "End" eseményt használja fel az időtartam kiszámítására.
4. Jelenítse meg a leghosszabb időtartamú esemény azonosítóját és időtartamát!
5. Kérdezze meg a felhasználótól egy dátumot, és adja meg, hogy azon a napon hány esemény kezdődött és fejeződött be, továbbá mutassa meg a teljes napi tevékenység időtartamát!
6. Határozza meg, mely napokon voltak események, és listázza ki ezeket a napokat! Ezt a listát mentse el egy napok.txt fájlba.
7. Készítsen egy jelentést, amely tartalmazza az egyes azonosítókhoz tartozó összes eseményt, azok kezdő és záró időpontjaival együtt, és a teljes időtartamokkal együtt. A jelentést mentse el egy esemeny_jelentes.txt állományban.