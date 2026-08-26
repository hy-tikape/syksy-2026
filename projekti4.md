---
title: Projektitehtävä 4
permalink: /projekti4/
hide: true
---

# Projektitehtävä 4

Tee ohjelma, jonka avulla voidaan suorittaa tietokannan tehokkuustesti. Tehokkuustestin osat ovat:

* Ohjelma luo taulun `Movies`, jossa on sarakkeet `id`, `name` ja `release_year`.
* Ohjelma lisää tauluun miljoona riviä. Jokaisen elokuvan nimeksi valitaan satunnainen merkkijono, jossa on 8 merkkiä, ja vuodeksi valitaan satunnainen kokonaisluku väliltä 1900–2000.
* Ohjelma suorittaa tuhat kertaa kyselyn, jossa haetaan elokuvien määrä vuonna `x`. Jokaisessa kyselyssä `x` valitaan satunnaisesti väliltä 1900–2000.

Toteuta ohjelma niin, että kaikki rivit lisätään saman transaktion sisällä (esimerkiksi alussa komento `BEGIN` ja lopussa komento `COMMIT`), jotta rivien lisääminen ei vie liikaa aikaa.

Käytä elokuvien määrän laskemisessa kyselyä, jossa haetaan rivien määrä `COUNT(*)` ehtoon täsmäävistä riveistä.

Tee ohjelmaan kolme funktiota, jotka suorittavat tehokkuustestin seuraavasti:

1. Tauluun ei lisätä kyselyitä tehostavaa indeksiä.
2. Tauluun lisätään kyselyitä tehostava indeksi ennen rivien lisäämistä.
3. Tauluun lisätään kyselyitä tehostava indeksi ennen kyselyiden suoritusta.

Merkitse muistiin jokaisessa testissä rivien lisäämiseen ja kyselyiden suoritukseen kuluva aika sekä tietokantatiedoston koko testin jälkeen. Miten voit selittää testin tulokset?

Varmista ennen varsinaisia testejä, että kyselysi antavat järkeviä tuloksia: indeksin tulisi nopeuttaa kyselyjä merkittävästi testeissä 2 ja 3. Älä kuitenkaan tulosta varsinaisissa testeissä mitään muuta kuin ajankäyttö, jotta tulostaminen ei vääristä testin tulosta.

Tarkasta tietokantatiedoston koko ohjelman suorituksen jälkeen.

## Palautusohje

Liitä raporttiin käyttämäsi koodi sekä testin tulokset seuraavasti:

* Testin 1 tulokset:
  - Rivien lisäämiseen kuluva aika (sekunteina)
  - Kyselyiden suoritukseen kuluva aika (sekunteina)
  - Tietokantatiedoston koko testin lopuksi (megatavuina)
* Testin 2 tulokset:
  - Rivien lisäämiseen kuluva aika (sekunteina)
  - Kyselyiden suoritukseen kuluva aika (sekunteina)
  - Tietokantatiedoston koko testin lopuksi (megatavuina)
* Testin 3 tulokset:
  - Rivien lisäämiseen kuluva aika (sekunteina)
  - Kyselyiden suoritukseen kuluva aika (sekunteina)
  - Tietokantatiedoston koko testin lopuksi (megatavuina)
* Miten selität testin tulokset?
