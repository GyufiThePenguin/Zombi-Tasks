~~~ python
from datetime import datetime

# Adatok beolvasása a fájlból
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

# Különböző termékkategóriák számának meghatározása
categories = set()
for product in products:
    categories.add(product[4])
print("Különböző termékkategóriák száma:", len(categories))

# Terméktípusok eladási statisztikái
product_sales = {}
category_popularity = {}
for product in products:
    product_type = product[1]
    quantity = product[2]
    category = product[4]
    if product_type not in product_sales:
        product_sales[product_type] = 0
    product_sales[product_type] += quantity
    if category not in category_popularity:
        category_popularity[category] = {}
    if product_type not in category_popularity[category]:
        category_popularity[category][product_type] = 0
    category_popularity[category][product_type] += quantity

# A legnépszerűbb terméktípusok kategóriánként
for category, types in category_popularity.items():
    most_popular = max(types, key=types.get)
    print(f"A {category} kategóriában a legnépszerűbb terméktípus: {most_popular} ({types[most_popular]} darab)")

# Napok, amikor a legtöbb termék fogyott
daily_sales = {}
for product in products:
    date = product[3]
    quantity = product[2]
    if date not in daily_sales:
        daily_sales[date] = 0
    daily_sales[date] += quantity
max_sales_day = max(daily_sales, key=daily_sales.get)
print(f"A legtöbb termék eladva: {daily_sales[max_sales_day]} darab, dátum: {max_sales_day}")

# Függvény egy adott termékazonosítóhoz tartozó adatok lekérdezésére
def get_product_info(product_id):
    for product in products:
        if product[0] == product_id:
            return product[1:]
    return None

# Termékek eladási sebességének kiszámítása
product_launch_dates = {}
for product in products:
    product_type = product[1]
    sale_date = datetime.strptime(product[3], '%Y-%m-%d')
    if product_type not in product_launch_dates:
        product_launch_dates[product_type] = sale_date
    else:
        if sale_date < product_launch_dates[product_type]:
            product_launch_dates[product_type] = sale_date

# Jelentés készítése a termékkategóriák szerinti eladásokról
with open('termekek_osszefoglalo.txt', 'w') as file:
    for category in categories:
        file.write(f"Kategória: {category}\n")
        total_sold = sum(product[2] for product in products if product[4] == category)
        average_sold = total_sold / len([product for product in products if product[4] == category])
        dates = set(product[3] for product in products if product[4] == category)
        file.write(f"Összesen eladva: {total_sold}, Átlagosan: {average_sold:.2f}\n")
        file.write(f"Eladási dátumok: {', '.join(sorted(dates))}\n\n")
print("A termékkategóriák összegzése elmentve a 'termekek_osszefoglalo.txt' fájlban.")

~~~
