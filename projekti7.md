---
title: Projektitehtävä 7
permalink: /projekti7/
hide: true
---

# Projektitehtävä 7

Tehtävän 1 aineistona on tietokanta `bikes_2024.db`, joka sisältää vuoden 2024 tiedot kaupunkipyörämatkoista Helsingin ja Espoon alueella.

Tässä tehtävässä sinun tulee laatia ohjelma, joka muodostaa vastaavan tietokannan `bikes_2023.db` vuodelle 2023. Löydät tietokantaan tulevat tiedot CSV-muodossa HSL:n [avoimen datan aineistosta](https://www.avoindata.fi/data/fi/dataset/helsingin-ja-espoon-kaupunkipyorilla-ajatut-matkat).

Ohjelmasi tulee lukea tiedot CSV-tiedostoista ja suorittaa SQL-komennot, jotka lisäävät tiedot tietokantaan vastaavassa muodossa kuin tehtävän 1 tietokannassa.

## Tietokannan testaaminen

Voit testata seuraavien kyselyiden avulla, että luomasi tietokannan sisältö vaikuttaa oikealta:

```console
sqlite> SELECT COUNT(*) FROM Stations;
459
sqlite> SELECT COUNT(*) FROM Trips;
2544025
sqlite> SELECT * FROM Stations WHERE id = 100;
100|Teljäntie
sqlite> SELECT * FROM Trips WHERE id = 123456;
123456|2023-04-18T15:18:42|2023-04-18T15:22:02|573|575|596|196
```

## Vastausohje

Liitä raporttiin toteuttamasi koodi.
