# Azja — państwa i stolice

Pomoc do sprawdzianu z geografii w 8. klasie szkoły podstawowej: interaktywna mapa polityczna Azji
do nauki i test „wskaż na mapie”.

## Nauka

- uproszczona mapa polityczna 49 państw Azji z punktami stolic
- po najechaniu myszką (na telefonie: po dotknięciu) na państwo albo punkt stolicy pojawia się nazwa
  państwa i jego stolicy, przy niektórych państwach z krótką uwagą (np. Tajwan, Izrael, Sri Lanka)
- opcjonalne podpisy państw i stolic na mapie
- przybliżanie kółkiem myszy, przyciskami +/− albo dwoma palcami; przesuwanie przez przeciąganie;
  szybkie widoki regionów (Bliski Wschód i Kaukaz, Azja Środkowa i Południowa, Wschodnia, Południowo-Wschodnia)
- alfabetyczna lista państw i stolic: najechanie podświetla państwo, kliknięcie przybliża do niego mapę

## Test

- mapa bez nazw: tylko kontury państw i punkty stolic
- pytania: „Wskaż na mapie państwo: …” albo „Wskaż na mapie stolicę: …” (do wyboru: państwa, stolice albo
  jedno i drugie), z całej Azji albo z wybranego regionu; 10 / 20 / wszystkie pytania w losowej kolejności
- bardzo małe państwa (Bahrajn, Singapur, Malediwy, Katar, Brunei…) mają przerywane kółko, które też można kliknąć
- po błędnej odpowiedzi kliknięte miejsce jest czerwone z nazwą, poprawne — zielone i pulsuje
- wynik z podziałem na państwa i stolice, tabela błędów i „Powtórz błędne”

## Struktura

```
index.html              aplikacja (HTML + CSS + logika, bez zewnętrznych bibliotek)
dane-mapa.js            kontury państw jako ścieżki SVG, stolice, kolory (wygenerowane)
narzedzia/panstwa.js    lista państw: kod ISO, nazwa, stolica, współrzędne stolicy, uwaga
narzedzia/build.html    generator dane-mapa.js
```

## Odświeżenie danych mapy

`narzedzia/build.html` rzutuje granice z [Natural Earth](https://www.naturalearthdata.com/) 1:50 mln
(pakiet [world-atlas@2.0.2](https://github.com/topojson/world-atlas), domena publiczna) w rzucie azymutalnym
równopolowym Lamberta i koloruje państwa tak, żeby sąsiednie miały różne kolory. Żeby go uruchomić, w folderze
`narzedzia/` muszą być:

- `d3.min.js` (d3@7.9.0) i `topojson-client.min.js` (topojson-client@3.1.0),
- `world.js` = `var WORLD=` + zawartość `countries-50m.json` + `;`.

Po otwarciu `build.html` w przeglądarce JSON pojawia się na stronie; zapisuje się go jako `const MAPA = …;`
w `dane-mapa.js`.
