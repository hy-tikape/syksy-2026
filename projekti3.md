---
title: Projektitehtävä 3
permalink: /projekti3/
hide: true
---

# Projektitehtävä 3

Jokaisessa seuraavassa testissä lähtökohtana on SQLitessä taulu, joka on luotu seuraavasti:

```sql
CREATE TABLE Test (x INTEGER);
INSERT INTO Test (x) VALUES (1);
```

Testissä kuvataan kahdessa transaktiossa suoritettavat komennot järjestyksessä. K1 tarkoittaa käyttäjän 1 suorittamaa komentoa, ja K2 tarkoittaa käyttäjän 2 suorittamaa komentoa. Testaa komentoja avaamalla kaksi SQLite-tulkkia samaan tietokantatiedostoon.

Tehtäväsi on ilmoittaa, minkä tuloksen `SELECT`-kyselyt antavat sekä onnistuvatko transaktiot. Transaktio onnistuu, jos kaikki siinä olevat komennot suoritetaan onnistuneesti (eikä tule viestiä `Error: database is locked`).

## Testi 1

```
K1: BEGIN;
K1: SELECT x FROM Test;

K2: BEGIN;
K2: UPDATE Test SET x = 2;
K2: SELECT x FROM Test;
K2: COMMIT;

K1: COMMIT;
```

## Testi 2

```
K1: BEGIN;
K1: SELECT x FROM Test;
K1: UPDATE Test SET x = 2;

K2: BEGIN;
K2: SELECT x FROM Test;
K2: COMMIT;

K1: COMMIT;
```

## Testi 3

```
K1: BEGIN;
K1: UPDATE Test SET x = 2;

K2: BEGIN;
K2: UPDATE Test SET x = 3;
K2: SELECT x FROM Test;
K2: COMMIT;

K1: SELECT x FROM Test;
K1: COMMIT;
```

## Testi 4

```
K1: BEGIN;
K1: UPDATE Test SET x = 2;

K2: BEGIN;
K2: UPDATE Test SET x = 2;
K2: SELECT x FROM Test;
K2: COMMIT;

K1: SELECT x FROM Test;
K1: COMMIT;
```

## Testi 5

```
K1: BEGIN;
K1: SELECT x FROM Test;

K2: BEGIN;
K2: SELECT x FROM Test;
K2: UPDATE Test SET x = 2;
K2: COMMIT;

K1: UPDATE Test SET x = 2;
K1: COMMIT;
```

## Palautusohje

Liitä raporttiin testeihin 1–5 liittyen vastaukset seuraaviin kysymyksiin:

* Minkä tuloksen 1. transaktion `SELECT`-kysely antaa?
* Minkä tuloksen 2. transaktion `SELECT`-kysely antaa?
* Onnistuuko 1. transaktio?
* Onnistuuko 2. transaktio?
* Miten perustelet nämä tulokset?
