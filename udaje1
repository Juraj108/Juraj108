import csv

import pickle

def vypisat_udaje(data):
    if not data:
        print("Zoznam je prázdny.")
    else:
        print("Aktuálne údaje:")
        for index, riadok in enumerate(data, start=1):
            print(f"{index}: {riadok}")

def pridat_udaje(data):
    novy_riadok = input("Zadajte nový riadok údajov: ")
    data.append(novy_riadok)
    print("Údaje boli pridané.")

def upravit_udaje(data):
    vypisat_udaje(data)
    try:
        cislo = int(input("Zadajte číslo riadku, ktorý chcete upraviť: ")) - 1
        if 0 <= cislo < len(data):
            novy_text = input("Zadajte nový obsah pre tento riadok: ")
            data[cislo] = novy_text
            print("Riadok bol upravený.")
        else:
            print("Neplatné číslo riadku.")
    except ValueError:
        print("Neplatný vstup. Zadajte číslo.")

def vymazat_udaje(data):
    vypisat_udaje(data)
    try:
        cislo = int(input("Zadajte číslo riadku, ktorý chcete vymazať: ")) - 1
        if 0 <= cislo < len(data):
            data.pop(cislo)
            print("Riadok bol vymazaný.")
        else:
            print("Neplatné číslo riadku.")
    except ValueError:
        print("Neplatný vstup. Zadajte číslo.")

def ulozit_do_csv(data):
    nazov_suboru = input("Zadajte názov súboru na uloženie (napr. udaje.csv): ")
    with open(nazov_suboru, mode='w', newline='', encoding='utf-8') as subor:
        writer = csv.writer(subor)
        for riadok in data:
            writer.writerow([riadok])
    print(f"Údaje boli uložené do súboru {nazov_suboru}.")

def nacitat_z_csv():
    nazov_suboru = input("Zadajte názov súboru na načítanie (napr. udaje.csv): ")
    try:
        with open(nazov_suboru, mode='r', encoding='utf-8') as subor:
            reader = csv.reader(subor)
            data = [riadok[0] for riadok in reader]
            print(f"Údaje boli načítané zo súboru {nazov_suboru}.")
            return data
    except FileNotFoundError:
        print("Súbor nebol nájdený.")
        return []
    except Exception as e:
        print(f"Nastala chyba pri načítaní súboru: {e}")
        return []

def ulozit_do_pickle(data):
    nazov_suboru = input("Zadajte názov súboru na uloženie (napr. udaje.pkl): ")
    with open(nazov_suboru, mode='wb') as subor:
        pickle.dump(data, subor)
    print(f"Údaje boli uložené do súboru {nazov_suboru}.")

def nacitat_z_pickle():
    nazov_suboru = input("Zadajte názov súboru na načítanie (napr. udaje.pkl): ")
    try:
        with open(nazov_suboru, mode='rb') as subor:
            data = pickle.load(subor)
            print(f"Údaje boli načítané zo súboru {nazov_suboru}.")
            return data
    except FileNotFoundError:
        print("Súbor nebol nájdený.")
        return []
    except Exception as e:
        print(f"Nastala chyba pri načítaní súboru: {e}")
        return []

def moznosti():
    data = []
    while True:
        print("\nMožnosti:")
        print("1. Pridať údaje")
        print("2. Upraviť údaje")
        print("3. Vymazať údaje")
        print("4. Vypísať údaje")
        print("5. Uložiť údaje")
        print("6. Načítať údaje5")
        print("7. Ukončiť program")

        volba = input("Zadajte číslo možnosti: ")

        if volba == "1":
            pridat_udaje(data)
        elif volba == "2":
            upravit_udaje(data)
        elif volba == "3":
            vymazat_udaje(data)
        elif volba == "4":
            vypisat_udaje(data)
        elif volba == "5":
            format_suboru = input("Zadajte formát na uloženie (csv/pickle): ").lower()
            if format_suboru == "csv":
                ulozit_do_csv(data)
            elif format_suboru == "pickle":
                ulozit_do_pickle(data)
            else:
                print("Neplatný formát.")
        elif volba == "6":
            format_suboru = input("Zadajte formát na načítanie (csv/pickle): ").lower()
            if format_suboru == "csv":
                data = nacitat_z_csv()
            elif format_suboru == "pickle":
                data = nacitat_z_pickle()
            else:
                print("Neplatný formát.")
        elif volba == "7":
            print("Program sa ukončuje.")
            break
        else:
            print("Neplatná možnosť. Skúste znova.")

if __name__ == "__main__":
    moznosti()