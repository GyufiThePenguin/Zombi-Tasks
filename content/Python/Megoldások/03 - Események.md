~~~ python
# Adatok beolvasása a fájlból
events = []
with open('esemenyek.txt', 'r') as file:
    for line in file:
        parts = line.strip().split(', ')
        date = parts[0]
        identifier = parts[1]
        time = parts[2]
        event_type = parts[3]
        events.append((date, identifier, time, event_type))

# Különböző típusú események számának meghatározása
event_types = set()
for event in events:
    event_type = event[3]
    event_types.add(event_type)
print("Különböző típusú események száma:", len(event_types))

# Felhasználó által megadott dátumon történt események típusainak kiszámítása
input_date = input("Kérem adja meg a dátumot (év-hónap-nap, pl. 2023-04-13): ")
events_on_date = []
for event in events:
    if event[0] == input_date:
        events_on_date.append(event[3])
print(f"{input_date} napon történt események típusai:", set(events_on_date))

# Az eseménytípusok előfordulásának számítása
event_type_counts = {}
for event in events:
    event_type = event[3]
    if event_type in event_type_counts:
        event_type_counts[event_type] += 1
    else:
        event_type_counts[event_type] = 1

most_common_type = max(event_type_counts, key=event_type_counts.get)
print(f"Legtöbb eseménytípus: {most_common_type}, események száma: {event_type_counts[most_common_type]}")

# Eseménytípusok havi átlagos előfordulásának számítása
import collections
import calendar

# A teljes dátumtartomány meghatározása az adatokból
dates = [event[0] for event in events]
months = set(date[:7] for date in dates)  # Év-hónap formátumban gyűjtjük a dátumokat
month_counts = collections.defaultdict(int)
for event in events:
    month = event[0][:7]
    month_counts[month] += 1

average_per_month = {etype: sum(count for month, count in month_counts.items() if month.startswith(etype)) / len(months)
                     for etype in event_types}
for etype, avg in average_per_month.items():
    print(f"{etype} események átlagos száma egy hónapban: {avg:.2f}")

# Függvény: Esemény típus szerinti napok listázása
def esemeny_napok(event_type_code):
    days = []
    for event in events:
        if event[3] == event_type_code:
            days.append(event[0])
    return days

# Összefoglaló jelentés készítése
events_sorted = sorted(events, key=lambda x: x[0])  # Dátum szerint rendezve
with open('rendezvenyek_osszefoglalo.txt', 'w') as file:
    for event in events_sorted:
        line = f"{event[0]}, {event[1]}, {event[2]}, {event[3]}"
        print(line)
        file.write(line + '\n')

~~~