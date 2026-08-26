---
title: Projektitehtävä 1
permalink: /projekti1/
hide: true
---

# Projektitehtävä 1

Tämän tehtävän aineistona on tietokanta, joka sisältää tiedot kaupunkipyörillä tehdyistä matkoista vuonna 2024 Helsingin ja Espoon alueella. Tietokanta perustuu HSL:n julkaisemaan [avoimen datan aineistoon](https://www.avoindata.fi/data/fi/dataset/helsingin-ja-espoon-kaupunkipyorilla-ajatut-matkat), joka on muutettu tätä kurssia varten SQLite-tietokannaksi.

Voit kopioida tietokannan itsellesi tästä: [bikes_2024.zip](../bikes_2024.zip)

Tietokannassa on seuraavat kaksi taulua:

```sql
CREATE TABLE Stations (
    id INTEGER PRIMARY KEY,
    name TEXT
);

CREATE TABLE Trips (
    id INTEGER PRIMARY KEY,
    start_time TEXT,
    end_time TEXT,
    start_station_id INTEGER REFERENCES Stations,
    end_station_id INTEGER REFERENCES Stations,
    distance INTEGER,
    duration INTEGER
);
```

Kurssin materiaalissa on tarkempaa tietoa tietokannan sisällöstä sekä esimerkkejä tietokantaan liittyvistä kyselyistä.

Tehtäväsi on toteuttaa koodi, jossa on tietokantaa käyttäviä funktioita. Voit päättää itse, missä muodossa funktiot tarkalleen antavat tulokset. Oleellista on, että pystyt funktioiden avulla hakemaan osatehtävissä mainitut esimerkkitulokset.

Saat tietyn määrän pisteitä jokaisesta osatehtävästä. Pistemääräsi tehtävästä on summa ratkaisemiesi osatehtävien pisteistä.

## Osatehtävä 1 (4 pistettä)

* Toteuta funktio `trips_from_station(station_name)`, joka palauttaa annetulta asemalta alkaneiden matkojen määrän.
* Toteuta funktio `trips_to_station(station_name)`, joka palauttaa annetulle asemalle päättyneiden matkojen määrän.

Funktioiden tulisi antaa tuloksena esimerkiksi, että asemalla "Intiankatu" alkaneiden matkojen määrä on 8535 ja päättyneiden matkojen määrä on 8448.

## Osatehtävä 2 (5 pistettä)

* Toteuta funktio `longest_distance_trips(limit)`, joka palauttaa `limit` pisintä matkan pituutta sekä niitä vastaavat lähtö- ja kohdeasemat.
* Toteuta funktio `longest_duration_trips(limit)`, joka palauttaa `limit` pisintä matkan kestoa sekä niitä vastaavat lähtö- ja kohdeasemat.

Funktioiden tulisi antaa seuraavat tulokset, kun `limit` on 5:

| Lähtöasema         | Kohdeasema          | Etäisyys (m) |
|--------------------|----------------------|-------------------|
| Erottajan aukio    | Unioninkatu          | 655225            |
| Gunillantie        | Workshop Helsinki    | 425905            |
| Pajamäki           | Paloheinän kirjasto  | 393434            |
| Tupasaarentie      | Marjaniementie       | 277991            |
| Pitäjänmäen asema  | Workshop Helsinki    | 262121            |

| Lähtöasema       | Kohdeasema      | Kesto (s) |
|------------------|------------------|-------------------|
| Lintulahdenkatu  | Marjaniementie   | 6286982           |
| Tupasaarentie    | Marjaniementie   | 4649106           |
| Ehrenströmintie  | Workshop Helsinki| 4396006           |
| Matinkyläntie    | Paciuksenkaari   | 4000567           |
| Kuikkarinne      | Trumpettikuja    | 3987658           |

Sivuhuomio: Nämä tiedot eivät vaikuta uskottavilta, koska tämä tarkoittaisi, että pisin matkan pituus on 655 kilometriä ja pisin matkan kesto on 72 päivää.

## Osatehtävä 3 (6 pistettä)

* Toteuta funktio `trips_during_month(month)`, joka palauttaa annettuna kuukautena alkaneiden matkojen määrän. Tässä 1 = tammikuu, 2 = helmikuu, jne.
* Toteuta funktio `trips_during_weekday(day)`, joka palauttaa annettuna viikonpäivänä alkaneiden matkojen määrän. Tässä 1 = maanantai, 2 = tiistai, jne.

Funktioiden tulisi antaa seuraavat tulokset:

| Kuukausi  | Matkojen määrä |
|-----------|----------------:|
| Huhtikuu  | 167960          |
| Toukokuu  | 448518          |
| Kesäkuu   | 469132          |
| Heinäkuu  | 455422          |
| Elokuu    | 492348          |
| Syyskuu   | 340507          |
| Lokakuu   | 211781          |

| Päivä      | Matkojen määrä |
|------------|----------------:|
| Maanantai  | 379173          |
| Tiistai    | 423740          |
| Keskiviikko| 405657          |
| Torstai    | 406417          |
| Perjantai  | 367325          |
| Lauantai   | 311952          |
| Sunnuntai  | 291404          |

## Osatehtävä 4 (7 pistettä)

* Toteuta funktio `most_popular_start_stations(limit)`, joka palauttaa `limit` suosituinta lähtöasemaa.
* Toteuta funktio `least_popular_start_stations(limit)`, joka palauttaa `limit` vähiten suosittua lähtöasemaa.

Funktioiden tulisi antaa seuraavat tulokset, kun `limit` on 5:

| Asema                  | Lähtöjen määrä |
|------------------------|----------------|
| Itämerentori           | 50441          |
| Töölönlahdenkatu       | 36382          |
| Rautatientori / länsi  | 32415          |
| Pasilan asema          | 30910          |
| Kalasatama (M)         | 28352          |

| Asema                    | Lähtöjen määrä |
|--------------------------|----------------|
| Relay Box test station   | 9              |
| Workshop Helsinki        | 26             |
| Puistolan VPK            | 393            |
| Sateenkaarentie          | 418            |
| Jakomäentie              | 481            |

Tässä "Relay Box test station" vaikuttaa olevan testiasema ja "Workshop Helsinki" on ehkä pyörävarikko, minkä takia todellinen vähiten suosittu lähtöasema voisi olla "Puistolan VPK".

## Osatehtävä 5 (8 pistettä)

* Toteuta funktio `largest_differences(limit)`, joka palauttaa `limit` suurinta eroa aseman alkaneiden ja päättyneiden matkojen määrässä.

Funktion tulisi antaa seuraavat tulokset, kun `limit` on 5:

| Asema                 | Alkaneet matkat| Päättyneet matkat | Määrien ero |
|-------------------------|------:|--------:|--------:|
| Pasilan asema           | 30910 |   26670 |    4240 |
| Karhupuisto             |  9686 |    8018 |    1668 |
| Sompasaari              | 21604 |   23158 |    1554 |
| Vallilan varikko        |  6068 |    4647 |    1421 |
| Opastinsilta            |  5905 |    4550 |    1355 |

## Palautusohje

Liitä raporttiin koodi, joka sisältää toteuttamasi funktiot.
