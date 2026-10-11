# Pivničný sommelier

Matúš Ráček

5ZYI34

## Stručný opis projektu

Pivničný sommelier je webová aplikácia pre milovníkov vína a destilátov, ktorá im pomáha viesť si prehľad o domácej zbierke a zapisovať si, čo a s kým ochutnali. Rieši bežný problém: človek má doma desiatky fliaš, no nepamätá si, ktorú už otváral, čo mu chutilo ani k akému jedlu sa hodila.

Aplikácia je určená domácim nadšencom, ktorí zbierajú víno alebo destiláty, a partiám priateľov, ktoré sa radi stretávajú na degustáciách. Jej hlavným účelom je mať na jednom mieste prehľad o tom, čo používateľ vlastní, čo mu chutí a čo si chce dokúpiť, a zároveň uľahčiť organizovanie spoločných degustačných posedení.

## Role v projekte

- **Návštevník (neprihlásený používateľ)** – môže si pozrieť úvodnú stránku s ukážkou aplikácie a verejne zdieľané degustačné udalosti. Nemá prístup k žiadnym osobným údajom a môže sa zaregistrovať alebo prihlásiť.
- **Registrovaný používateľ** – spravuje vlastnú zbierku fliaš, píše degustačné poznámky, plánuje degustačné udalosti a vidí iba svoje údaje. Zodpovedá za obsah, ktorý vytvorí.
- **Správca** – spravuje číselník kategórií nápojov (napr. červené víno, whisky, rum), môže upraviť alebo odstrániť nevhodný verejný obsah a spravovať používateľské účty.

## Prípady použitia podľa rolí

**Návštevník**
- prezrie si úvodnú stránku a popis aplikácie,
- prezrie si verejne zdieľané degustačné udalosti a ich hodnotenia,
- zaregistruje sa a prihlási do aplikácie.

**Registrovaný používateľ**
- pridá novú fľašu do svojej zbierky (druh, pôvod, ročník, počet kusov, miesto uloženia),
- upraví alebo odstráni fľašu zo zbierky,
- vyhľadá a vyfiltruje fľaše podľa kategórie, krajiny, ročníka alebo hodnotenia,
- zapíše k fľaši degustačnú poznámku s hodnotením a jedlom, s ktorým si nápoj sadol,
- naplánuje degustačnú udalosť, vyberie fľaše, ktoré sa na nej otvoria, a rozhodne, či bude verejná,
- po udalosti zapíše hodnotenia otvorených fliaš,
- upraví svoj profil a odhlási sa.

**Správca**
- pridá, upraví alebo odstráni kategóriu nápoja,
- zobrazí zoznam používateľov a zablokuje problémový účet,
- zmaže nevhodnú verejnú udalosť alebo poznámku.

## Plánované entity

- **Používateľ** – účet v systéme. Atribúty: e-mail, meno, heslo (hash), rola, dátum registrácie. Vlastní fľaše, poznámky a udalosti.
- **Kategória** – typ nápoja. Atribúty: názov, popis. Zaraďuje fľaše do skupín.
- **Fľaša** – položka v zbierke používateľa. Atribúty: názov, výrobca, krajina pôvodu, ročník, počet kusov, miesto uloženia, nákupná cena, fotografia. Patrí jednému používateľovi a jednej kategórii.
- **Degustačná poznámka** – záznam o ochutnaní fľaše. Atribúty: dátum, hodnotenie (1–5), opis chuti, vhodné jedlo. Patrí jednej fľaši a jej autorovi.
- **Degustačná udalosť** – naplánované alebo uskutočnené posedenie. Atribúty: názov, dátum, miesto, popis, príznak verejnosti. Patrí organizátorovi a obsahuje viacero fliaš.

## Vzťahy medzi entitami

- **Používateľ – Fľaša (1:N):** používateľ vlastní viac fliaš, každá fľaša patrí jednému používateľovi.
- **Kategória – Fľaša (1:N):** do jednej kategórie patrí viac fliaš, každá fľaša má jednu kategóriu.
- **Fľaša – Degustačná poznámka (1:N):** k jednej fľaši môže vzniknúť viac poznámok (napr. pri rôznych ochutnaniach).
- **Používateľ – Degustačná udalosť (1:N):** používateľ organizuje viac udalostí.
- **Degustačná udalosť – Fľaša (M:N):** na jednej udalosti sa otvára viac fliaš a tá istá fľaša sa môže objaviť na viacerých udalostiach.

## Hlavné stránky aplikácie

1. **Úvodná stránka** – predstavenie aplikácie, odkazy na registráciu a prihlásenie, výber verejných udalostí.
2. **Registrácia a prihlásenie** – vytvorenie účtu a prístup do súkromnej časti.
3. **Moja zbierka** – zoznam fliaš používateľa s filtrovaním a stránkovaním bez opätovného načítania stránky.
4. **Detail fľaše / formulár fľaše** – zobrazenie, pridanie a úprava fľaše spolu s jej degustačnými poznámkami.
5. **Degustačné udalosti** – zoznam vlastných a verejných udalostí s možnosťou vytvorenia novej.
6. **Detail udalosti** – zoznam fliaš na udalosti, pridávanie fliaš a zapisovanie hodnotení po akcii.
7. **Správa kategórií a používateľov** – stránka pre správcu (len pre rolu správca).
8. **Profil používateľa** – úprava osobných údajov.

## Rozdelenie funkcionality

**Základné funkcie (minimum na dokončenie projektu)**
- registrácia, prihlásenie a odhlásenie, oddelenie verejnej a súkromnej časti,
- plné CRUD nad fľašami a degustačnými udalosťami,
- pridávanie degustačných poznámok k fľašiam,
- priradenie fliaš k udalosti (vzťah M:N),
- správa kategórií správcom,
- AJAX filtrovanie a stránkovanie zbierky.

**Rozširujúce funkcie (podľa časových možností)**
- nahrávanie fotografií fliaš,
- vyhľadávanie nápoja podľa jedla, s ktorým sa osvedčil,
- in-place editovanie hodnotenia priamo v zozname,
- štatistiky zbierky (celková hodnota, najlepšie hodnotené fľaše, rozdelenie podľa krajín),
- zdieľanie udalosti odkazom a pozvánky pre ďalších používateľov,
- zoznam „na dokúpenie“ (wishlist).
