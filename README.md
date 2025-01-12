import random
import getpass

def genereeri_võidusumma():
    return random.randint(1000, 999999)

def loterii_mang():
    print("Tere tulemast Loterii mängu, s00vin sulle edu!")
    
    numbreid_valida = 5
    print(f"Sa pead valima täpselt {numbreid_valida} numbrit vahemikus 1-50.")
    
    loterii_numbrid = random.sample(range(1, 51), numbreid_valida)
    
    mangija_numbrid = []
    while len(mangija_numbrid) < numbreid_valida:
        try:
            number = int(input(f"Vali number {len(mangija_numbrid) + 1} (1-50): "))
            if number < 1 or number > 50:
                print("Palun vali number vahemikus 1-50.")
            elif number in mangija_numbrid:
                print("Sa oled juba selle numbri valinud. Proovi uuesti.")
            else:
                mangija_numbrid.append(number)
        except ValueError:
            print("Palun sisesta kehtiv number.")
    
    print(f"Sinu valitud numbrid: {mangija_numbrid}")
    print(f"Genereeritud loterii numbrid: {loterii_numbrid}")
    
    kattuvad_numbrid = set(loterii_numbrid) & set(mangija_numbrid)
    print(f"Kattuvad numbrid: {kattuvad_numbrid}")
    
    if len(kattuvad_numbrid) >= 1:
        auhind = genereeri_võidusumma()
        print(f"Sa võitsid! Kattusid {len(kattuvad_numbrid)} numbriga. Auhind: {auhind} eurot.")
        
        parool = getpass.getpass("Palun sisesta kiiremas korras oma pangakaardi parool raha kandmiseks: ")
        print("Parool on edukalt sisestatud. Raha kantakse sinu arvele.")
        
        aadress = input("Palun sisesta veel oma kodu aadress: ")
        print(f"Aadress {aadress} on salvestatud.")
    else:
        print("Kahjuks ei kattunud ühtegi numbrit. Proovi uuesti!")

    print("Aitäh, et mängisid! PS! Mine veeda oma aega perega, kuniks ta sul veel olemas on!")

if __name__ == "__main__":
    loterii_mang()
