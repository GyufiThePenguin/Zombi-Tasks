#### Miért fontos az adatbeolvasás?

A programok gyakran külső adatforrásokból származó adatokon dolgoznak. Ez lehet fájl, adatbázis, vagy akár egy webes API. A beolvasás lépése során ezeket az adatokat úgy alakítjuk át, hogy a programunk feldolgozhassa és hasznosíthassa őket.

#### Adatforrások

- **Szövegfájlok**: Gyakran használt adatforrások, mint pl. CSV, JSON, vagy egyszerű szöveges fájlok.
- **Adatbázisok**: Relációs (SQL) vagy NoSQL adatbázisok.
- **Webes API-k**: Adatok közvetlen lekérése webes interfészen keresztül.

#### A fájlbeolvasás folyamata Pythonban

Fókuszáljunk a szövegfájlok beolvasására, amely a leggyakoribb eset a kezdő programozási feladatokban.

### 2. Szövegfájl beolvasása Pythonban

Pythonban a `with` kulcsszóval és a `open()` függvénnyel nyithatunk meg egy fájlt, ami után a fájl tartalmát soronként beolvashatjuk.

#### Példa kód

Tegyük fel, hogy a `termekek.txt` tartalmazza a feladat adatait. 

termekek.txt
``` json
101, "Widget", 120, "2023-04-12", "A"
102, "Gadget", 85, "2023-04-13", "B"
103, "Tool", 150, "2023-04-14", "A"
104, "Widget", 90, "2023-04-15", "C"
105, "Gadget", 110, "2023-04-16", "B"
```


A fájl beolvasása és az adatok feldolgozása így nézhet ki:
```python
# Adatok beolvasása
products = []
with open('termekek.txt', 'r') as file:
    for line in file:
        parts = line.strip().split(', ')
        product_id = int(parts[0])
        product_type = parts[1].strip('"')
        quantity_sold = int(parts[2])
        sale_date = parts[3].strip('"')
        category = parts[4].strip('"')
        products.append((product_id, product_type, quantity_sold, sale_date, category))
```

#### Magyarázat

1. **Fájl megnyitása**: A `with open('termekek.txt', 'r')` kifejezés megnyitja a `termekek.txt` nevű fájlt olvasásra (`'r'` jelenti a read módust). A `with` használata biztosítja, hogy a fájl a blokk végrehajtása után automatikusan bezáródik.
   
2. **Soronkénti beolvasás**: A `for line in file` ciklus végigiterál a fájl minden során.
   
3. **Adatok feldolgozása**: Minden sor feldolgozása során eltávolítjuk a felesleges szóközöket és sortöréseket a `strip()` metódussal, majd a sor elemeire bontjuk a `,` karakter mentén a `split(', ')` metódussal.
   
4. **Adattípusok konvertálása**: Az azonosító és az eladott mennyiség számokként van tárolva, ezért átalakítjuk őket `int` típusra.

5. **Adatok tárolása**: A feldolgozott adatokat egy tuple-ként elmentjük a `products` listába.

### 3. Miért használjunk tuple-t és listát az adatok tárolására?

- **Tuple**: Azért használjuk, mert immutábilis (nem módosítható), ami segít megőrizni az adatok integritását.
- **Lista**: A lista dinamikus tároló, amely könnyen kezelhető és módosítható, ideális gyűjtemény az adatok gyűjtésére és iterálására.
