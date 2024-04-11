# DMBLOCK - minizadanie3
**Tomáš Brček**
**Cvičenie:** Streda 11:00
**Dátum:** 10.4.2024

---

## Nesprávny use-case blockchainu

Príkladom nesprávneho použitia blockchainu by mohlo byť:

### Spravovanie lekárskych záznamov v jednej nemocnici

#### Vysvetlenie

1. **Je potrebné ukladať stav?** Áno, pretože lekárske záznamy musia byť bezpečne ukladané a spravované.
2. **Existujú viacerí zapisovatelia?** Áno, v rámci jednej nemocnice obvykle existuje viacero lekárov, ktorí vkladajú a pristupujú k záznamom pacientov.
3. **Môžete použiť vždy online dôveryhodnú tretiu stranu (TTP)?** Áno, IT oddelenie nemocnice môže spravovať a zabezpečiť dostupnosť a bezpečnosť centralizovanej databázy.
4. **Sú všetci autori známi?** Áno, nemocnica zamestnáva a poveruje lekárov, ktorí sú zodpovední za vkladanie a prístup k záznamom pacientov.
5. **Sú všetci autori dôveryhodní?** Áno, nemocnica dôveruje svojim lekárom, aby vkladali a pristupovali k záznamom pacientov, čo je súčasťou ich povinností.
6. **Je vyžadovaná verejná overiteľnosť?** Nie, záznamy pacientov musia zostať súkromné a pristupovať k nim môžu iba oprávnení lekári.

Keďže v jednej nemocnici pracujú len lekári, ktorí majú prístup k záznamom pacientov, a nemocnica môže mať vždy online dostupné a dôveryhodné IT oddelenie ako TTP, nie je potrebné použiť blockchain.

---

## Správny use-case blockchainu

Príkladom správneho použitia blockchainu by mohlo byť:

### Dodávanie potravín

#### Vysvetlenie

1. **Je potrebné ukladať stav?** Áno, pretože je potrebné ukladať stav každej fázy výrobného procesu potravín.
2. **Existujú viacerí zapisovatelia?** Áno, dodávatelia, výrobcovia, distribútori a maloobchodníci majú možnosť aktualizovať informácie o produkte počas jeho putovania cez reťaz dodávateľov.
3. **Môžete použiť vždy online dôveryhodnú tretiu stranu (TTP)?** Nie, pretože vzhľadom na komplexnosť siete dodávateľov je náročné mať dôveru vo všetkých zainteresovaných aktérov.
4. **Sú všetci autori známi?** Áno, všetci autori v globálnej dodávateľskej sieti by mali byť známi.
5. **Sú všetci autori dôveryhodní?** Nie, keďže v sieti sa môžeme stretnúť s rôznymi dodávateľmi a aktérmi, nie je možné úplne dôverovať ich záznamom a informáciám.
6. **Je vyžadovaná verejná overiteľnosť?** Áno, toto je dôležité z hľadiska transparentnosti siete a dôvery spotrebiteľov voči pôvodu a kvalite potravín.

Na základe týchto odpovedí môžeme zistiť, že použitie blockchainu je vhodné pre tento use-case, pretože umožňuje zabezpečiť transparentnosť, integritu dát a dôveru medzi všetkými zainteresovanými stranami.

#### Implementácia
Tento use-case bude realizovaný pomocou smart kontraktu v Solidity, ktorý bude slúžiť na sledovanie každého kroku pri dodávaní potravín, čo zvyšuje transparentnosť, dôveryhodnosť ale aj bezpečnosť pre všetkých účastníkov, ktorými sú dodávatelia, výrobcovia, distribútori a maloobchodníci.

Vďaka tomuto smart kontraktu majú spotrebitelia možnosť presne vedieť, odkiaľ pochádzajú potraviny a akými všetkými procesmi prešli, čo je v dnešnej dobe veľmi dôležité.

**Funkcie smart kontraktu:**
- **addProduct()**: pridá nový produkt do reťazca a zaznamená informácie o výrobcovi, pričom emituje udalosť *newProductAdded*.
- **assignDistributor()**: priradí distribútora k produktu, môže byť vykonaná iba vlastníkom kontraktu a emituje udalosť *distributorAssigned*.
- **assignRetailer()**: priradí maloobchodníka k produktu, môže byť vykonaná iba distribútorom priradeným k produktu a emituje udalosť *retailerAssigned*.
- **certifyProduct()**: mení stav produktu ako overený, môže byť vykonaná iba maloobchodníkom priradeným k produktu a emituje udalosť *productCertification*.
- **getProduct()**: vráti informácie o konkrétnom produkte vrátane jeho názvu, výrobcu, distribútora, maloobchodníka a stavu certifikácie.
