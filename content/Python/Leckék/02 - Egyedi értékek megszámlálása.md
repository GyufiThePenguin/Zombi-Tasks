Ez a lecke a gyakran előforduló programozási feladatra koncentrál, amikor egy adathalmazban lévő egyedi értékek számát kell meghatározni. Ez hasznos lehet adatok elemzésekor, jelentések készítésekor, vagy akár adatok tisztításakor.

#### Miért fontos az egyedi értékek megszámlálása?

Adatok elemzésekor gyakran fontos tudni, hány különböző típusú elem, kategória vagy csoport található az adatok között. Ez segíthet a minták azonosításában, az adatok értelmezésében és döntéshozatali folyamatokban. Például egy e-kereskedelmi weboldal esetében fontos lehet tudni, hány különböző termékkategória van, hogy megértsük a termékkínálat diverzitását.

#### Hogyan számoljuk meg az egyedi értékeket?

Pythonban az egyedi értékek megszámlálására általában a `set` adatszerkezetet használjuk, ami automatikusan eltávolítja a duplikált elemeket, így csak az egyedi elemek maradnak meg.

##### 1. Példa: Termékkategóriák megszámlálása

Tegyük fel, hogy van egy terméklistánk, ahol minden termékhez tartozik egy kategória. A feladatunk megszámolni, hány különböző kategória található a listában.

**Adatok:**
``` python
products = [
    (101, "Widget", 120, "2023-04-12", "A"),
    (102, "Gadget", 85, "2023-04-13", "B"),
    (103, "Tool", 150, "2023-04-14", "A"),
    (104, "Widget", 90, "2023-04-15", "C"),
    (105, "Gadget", 110, "2023-04-16", "B")
]
```

**Megoldás lépésekben:**

1. **Adatok beolvasása:** Először is, olvassuk be a terméklistát, amit már fentebb definiáltunk.

2. **Egyedi kategóriák gyűjtése:** Hozzunk létre egy üres **halmazt**, amelybe az egyes termékek kategóriáit fogjuk gyűjteni.

```python
categories = set()
for product in products:
    category = product[4]
    categories.add(category)
```

3. **Egyedi értékek számának kiíratása:**

```python
print("Különböző termékkategóriák száma:", len(categories))
```

Ez a kód kimenete a következő lesz, mivel három különböző kategória (A, B, C) szerepel a terméklistában:

```
Különböző termékkategóriák száma: 3
```

#### Miért hasznos ez a megközelítés?

A `set` használata egyszerű és hatékony módja az egyedi értékek kezelésének. Mivel a `set` csak egyedi értékeket tárol, ezáltal automatikusan eldobja a duplikátumokat. Ez a megközelítés különösen nagy adatkészletek esetén válik hatékonnyá, mivel a `set` műveletei általában gyorsak.