~~~ python
# Adatok beolvasása a fájlból
measurements = []
with open('homerseklet.txt', 'r') as file:
    for line in file:
        parts = line.strip().split()
        time = parts[0]
        temperature = float(parts[1])
        location = parts[2]
        measurements.append((time, temperature, location))

# Különböző mérési pontok számának meghatározása
unique_locations = set()
for measurement in measurements:
    location = measurement[2]
    unique_locations.add(location)
print("Különböző mérési pontok száma:", len(unique_locations))

# Felhasználó által megadott időpontban mért hőmérsékletek és helyszínek
input_time = input("Kérem adja meg az időpontot (óra:perc formátumban, pl. 14:20): ")
temperatures_at_time = []
for measurement in measurements:
    if measurement[0] == input_time:
        temperatures_at_time.append((measurement[2], measurement[1]))
print("Ebben az időpontban mért hőmérsékletek és helyszínek:", temperatures_at_time)

# Nap legmagasabb hőmérséklete és helyszíne
max_temperature = -float('inf')
max_location = None
for measurement in measurements:
    if measurement[1] > max_temperature:
        max_temperature = measurement[1]
        max_location = measurement[2]
print(f"Nap legmagasabb hőmérséklete: {max_temperature} C, helyszín: {max_location}")

# Mérési pontonkénti legkisebb átlaghőmérséklet
average_temperatures = {}
for measurement in measurements:
    location = measurement[2]
    if location not in average_temperatures:
        average_temperatures[location] = []
    average_temperatures[location].append(measurement[1])

min_avg_temp = float('inf')
min_avg_location = None
for location, temps in average_temperatures.items():
    avg_temp = sum(temps) / len(temps)
    if avg_temp < min_avg_temp:
        min_avg_temp = avg_temp
        min_avg_location = location
print(f"Legkisebb átlaghőmérséklet: {min_avg_temp:.2f} C, helyszín: {min_avg_location}")

# Függvény: Adott időben mért hőmérsékletek listája
def homerseklet_adott_idoben(time):
    results = []
    for measurement in measurements:
        if measurement[0] == time:
            results.append((measurement[2], measurement[1]))
    return results

# Összefoglaló jelentés minden mérési pontról
summary = {}
for location in unique_locations:
    loc_temps = [temp for time, temp, loc in measurements if loc == location]
    loc_min = min(loc_temps)
    loc_max = max(loc_temps)
    loc_avg = sum(loc_temps) / len(loc_temps)
    summary[location] = (loc_avg, loc_min, loc_max)

# Jelentés kiírása és mentése
with open('summary.txt', 'w') as file:
    for location, stats in summary.items():
        report = f"{location}: Átlag: {stats[0]:.2f}, Min: {stats[1]:.2f}, Max: {stats[2]:.2f}\n"
        print(report)
        file.write(report)

~~~