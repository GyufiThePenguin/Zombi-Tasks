### Mi az Összegzés és Csoportosítás?

Az összegzés és csoportosítás technikái lehetővé teszik számunkra, hogy nagy adathalmazokból hasznos információkat szűrjünk ki. Például, ha egy e-kereskedelmi vállalat eladási adatait elemezzük, csoportosíthatjuk az adatokat termékkategória, dátum vagy régió szerint, majd összesíthetjük az eladásokat, átlagos eladási értékeket vagy bármely más releváns metrikát különböző csoportokra vonatkozóan.

### Pythonban való megvalósítás

Pythonban a listák és szótárak kiválóan alkalmasak az összegzés és csoportosítás feladatokra. Itt egy példa arra, hogyan csoportosíthatunk és számolhatunk össze adatokat egy egyszerű terméklista alapján:

#### Adathalmaz

Tegyük fel, hogy a következő termékeket áruljuk:

``` python
products = [
    {"type": "Widget", "category": "A", "quantity": 120},
    {"type": "Gadget", "category": "B", "quantity": 85},
    {"type": "Tool", "category": "A", "quantity": 150},
    {"type": "Widget", "category": "C", "quantity": 90},
    {"type": "Gadget", "category": "B", "quantity": 110}
]
```

#### Cél

Szeretnénk kiszámítani, hogy melyik termékkategóriából hány darabot adtunk el összesen.

### Lépések

1. **Adatstruktúra inicializálása**: Hozzunk létre egy szótárat, amely minden kategóriához tárolja az eladott mennyiséget.

```python
category_sales = {}
```

2. **Adatok bejárása és csoportosítása**: Iteráljunk végig a termékeken, és minden termékhez adjuk hozzá a mennyiséget a megfelelő kategóriához a szótárban.

```python
for product in products:
    category = product["category"]
    quantity = product["quantity"]
    if category in category_sales:
        category_sales[category] += quantity
    else:
        category_sales[category] = quantity
```

3. **Eredmények megjelenítése**: Nyomtassuk ki az eredményeket.

```python
for category, total_quantity in category_sales.items():
    print(f"Category {category} sold a total of {total_quantity} items.")
```

#### Teljes kód

```python
products = [
    {"type": "Widget", "category": "A", "quantity": 120},
    {"type": "Gadget", "category": "B", "quantity": 85},
    {"type": "Tool", "category": "A", "quantity": 150},
    {"type": "Widget", "category": "C", "quantity": 90},
    {"type": "Gadget", "category": "B", "quantity": 110}
]

category_sales = {}
for product in products:
    category = product["category"]
    quantity = product["quantity"]
    if category in category_sales:
        category_sales[category] += quantity
    else:
        category_sales[category] = quantity

for category, total_quantity in category_sales.items():
    print(f"Category {category} sold a total of {total_quantity} items.")
```
