
```python
# Adatok beolvasása a fájlból
orders = []
with open('rendeles.txt', 'r') as file:
    for line in file:
        parts = line.strip().split()
        orders.append(parts)

# Különböző városok számának meghatározása
unique_cities = set()
for order in orders:
    city = order[1]
    unique_cities.add(city)
print("Különböző városok száma:", len(unique_cities))

# Felhasználó által megadott dátumon történt rendelések számának kiszámítása
input_date = input("Adjon meg egy dátumot (pl. 2023-04-13): ")
orders_on_date = 0
for order in orders:
    if order[0] == input_date:
        orders_on_date += int(order[2])
print(f"Rendelések száma {input_date} napon:", orders_on_date)

# Nap amin a legkevesebb rendelés történt
daily_orders = {}
for order in orders:
    date = order[0]
    quantity = int(order[2])
    if date in daily_orders:
        daily_orders[date] += quantity
    else:
        daily_orders[date] = quantity

min_day = None
min_quantity = float('inf')
for date, quantity in daily_orders.items():
    if quantity < min_quantity:
        min_quantity = quantity
        min_day = date

print(f"Legkevesebb rendelés napja: {min_day}, rendelések száma: {min_quantity}")

# Város ahol a legtöbb rendelés történt
city_orders = {}
for order in orders:
    city = order[1]
    quantity = int(order[2])
    if city in city_orders:
        city_orders[city] += quantity
    else:
        city_orders[city] = quantity

max_city = None
max_orders = 0
for city, quantity in city_orders.items():
    if quantity > max_orders:
        max_orders = quantity
        max_city = city

print(f"Legtöbb rendelés városa: {max_city}, rendelések száma: {max_orders}")

# Az összes rendelési adat kiírása és mentése
with open('statisztika.txt', 'w') as file:
    for order in orders:
        line = "\t".join(order)
        print(line)
        file.write(line + '\n')
```

