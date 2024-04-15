~~~ python
from datetime import datetime

# Adatok beolvasása a fájlból
events = []
with open('esemenyek.txt', 'r') as file:
    for line in file:
        parts = line.strip().split(', ')
        date = parts[0]
        identifier = parts[1].strip('"')
        event_type = parts[2].strip('"')
        time = parts[3].strip('"')
        events.append((date, identifier, event_type, time))

# Különböző esemény azonosítók számának meghatározása
unique_identifiers = set()
for event in events:
    unique_identifiers.add(event[1])
print("Különböző esemény azonosítók száma:", len(unique_identifiers))

# Függvény az esemény időtartamának kiszámítására
def calculate_duration(identifier):
    start_times = []
    end_times = []
    for event in events:
        if event[1] == identifier:
            date_time = datetime.strptime(event[0] + " " + event[3], '%Y-%m-%d %H:%M')
            if event[2] == "Start":
                start_times.append(date_time)
            elif event[2] == "End":
                end_times.append(date_time)
    
    total_minutes = 0
    for i in range(len(start_times)):
        duration = (end_times[i] - start_times[i]).seconds / 60
        total_minutes += duration
    return total_minutes

# Leghosszabb időtartamú esemény azonosítója és időtartama
longest_duration = 0
longest_identifier = None
for identifier in unique_identifiers:
    duration = calculate_duration(identifier)
    if duration > longest_duration:
        longest_duration = duration
        longest_identifier = identifier
print(f"Leghosszabb esemény azonosítója: {longest_identifier}, időtartam: {longest_duration} perc")

# Felhasználó által megadott dátumra vonatkozó események
input_date = input("Kérem adja meg a dátumot (év-hónap-nap, pl. 2023-04-13): ")
start_count = 0
end_count = 0
for event in events:
    if event[0] == input_date:
        if event[2] == "Start":
            start_count += 1
        elif event[2] == "End":
            end_count += 1
print(f"{input_date} napon {start_count} kezdő és {end_count} befejező esemény volt.")

# Napok listázása, amikor események voltak
event_days = set()
for event in events:
    event_days.add(event[0])

# Napok kiírása fájlba
with open('napok.txt', 'w') as file:
    for day in sorted(event_days):
        file.write(day + '\n')
print("Az események napjai kiírva a 'napok.txt' fájlba.")

# Esemény jelentés készítése
with open('esemeny_jelentes.txt', 'w') as file:
    for identifier in unique_identifiers:
        file.write(f"Esemény azonosító: {identifier}\n")
        # Keresse meg az adott azonosítójú eseményeket és rendezze őket idő szerint
        sorted_events = []
        for event in events:
            if event[1] == identifier:
                sorted_events.append(event)
        sorted_events.sort(key=lambda x: x[3])  # Idő szerint rendezés
        for event in sorted_events:
            file.write(f"  {event[0]} {event[3]} - {event[2]}\n")
        duration = calculate_duration(identifier)
        file.write(f"  Teljes időtartam: {duration} perc\n\n")
print("Az események összefoglalója kiírva az 'esemeny_jelentes.txt' fájlba.")

~~~
