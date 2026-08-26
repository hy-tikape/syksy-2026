---
title: Projektitehtävä 6
permalink: /projekti6/
hide: true
---

# Projektitehtävä 6

MongoDB on suosittu NoSQL-tietokanta, joka ei perustu relaatiomalliin ja SQL-kieleen kuten useimmat perinteiset tietokannat. Tässä tehtävässä sinun tulee hakea tietoa olemassa olevasta tietokannasta, jossa on tietoa asunnoista ja niiden myyntihistoriasta.

Tehtäväsi on selvittää, miten MongoDB-tietokannasta haetaan tietoa ohjelmoimalla. Kurssin materiaalissa ei ole tietoa tästä, mutta voit käyttää nettilähteitä ja tekoälyä.

Tehtävään liittyvä tietokanta on MongoDB Atlas -pilvipalvelussa. Pääset tietokantaan koodissa käsiksi seuraavan tunnuksen ja salasanan kautta:

* Tunnus: `tikape`
* Salasana: `NAq8a4pNLWF8TMfd`

Tällä käyttäjällä on lukuoikeus tietokantaan, mikä tarkoittaa, että voit lukea tietokannassa olevaa tietoa mutta et voi muuttaa sitä. Tehtävässä on tarkoituksena käsitellä tietokantaa tekemällä ohjelma, joka yhdistää tietokantaan antamalla yllä olevan tunnuksen ja salasanan.

## Yhteys tietokantaan (Python)

Seuraava Python-koodi yhdistää tietokantaan ja hakee sieltä tietoa:

```python
import pymongo

connection_string = "mongodb+srv://tikape:NAq8a4pNLWF8TMfd@cluster0.u4vehy9.mongodb.net/"
client = pymongo.MongoClient(connection_string)

database = client.get_database("tikape")
apartments = database["apartments"]

count = apartments.count_documents({})
print(count)

first_apartment = apartments.find_one()
print(first_apartment)
```

Koodin tulostus on seuraavan kaltainen:

```
1000
{'_id': ObjectId('679e1f6ef33fbe011e152685'), 'zip_code': '00780', 'apartment_size': 109, 'construction_year': 1996, 'transactions': [{'date': '2005-08-21', 'selling_price': 548582}, {'date': '2011-04-28', 'selling_price': 545161}, {'date': '2013-01-20', 'selling_price': 550660}, {'date': '2019-12-06', 'selling_price': 538431}, {'date': '2024-11-25', 'selling_price': 548912}]}
```

Huomaa, että jos kokeilet suorittaa koodin itse, se saattaa näyttää eri asunnon tiedot. Koodi hakee jonkin tietokannassa olevan asunnon tiedot.

## Yhteys tietokantaan (R)

Seuraava R-koodi yhdistää tietokantaan ja hakee sieltä tietoa:

```r
connection_string <- "mongodb+srv://tikape:NAq8a4pNLWF8TMfd@cluster0.u4vehy9.mongodb.net/"

apartments <- mongo(collection = "apartments", db = "tikape", url = connection_string)

print(apartments$count())

print(apartments$find(limit = 1))
```

Koodin tulostus on seuraavan kaltainen:

```
[1] 1000

  zip_code apartment_size construction_year                                                                                       transactions
1    00780            109              1996 2005-08-21, 2011-04-28, 2013-01-20, 2019-12-06, 2024-11-25, 548582, 545161, 550660, 538431, 548912
```

Huomaa, että jos kokeilet suorittaa koodin itse, se saattaa näyttää eri asunnon tiedot. Koodi hakee jonkin tietokannassa olevan asunnon tiedot.

## Palautusohje

Liitä raporttiin koodi, joka hakee vastaukset seuraaviin kysymyksiin:

* Monessako asunnossa postinumero on 00700?
* Monessako asunnossa rakennusvuosi on 2000-luvulla?
* Monessako asunnossa pinta-ala on välillä 50–70 m²?
* Moniko asunnoista on myyty ainakin kerran vuosina 2010–2012?
* Mikä on kallein asunnon myyntihinta aineistossa?
