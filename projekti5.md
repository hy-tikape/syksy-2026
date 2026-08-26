---
title: Projektitehtävä 5
permalink: /projekti5/
hide: true
---

# Projektitehtävä 5

Tehtäväsi on toteuttaa koodi, jonka avulla voi määritellä relaatioita sekä suorittaa relaatioalgebran operaatioita projektio ja restriktio. Koodin tulee mahdollistaa seuraavat toiminnot:

* Luo uusi relaatio, jossa on annetut attribuutit
* Lisää uusi monikko (tuple) relaatioon
* Tulosta relaatiossa olevat monikot
* Muodosta uusi relaatio projektio-operaatiolla, kun annetaan halutut attribuutit
* Muodosta uusi relaatio restriktio-operaatiolla, kun annetaan haluttu attribuutin arvo

Voit olettaa restriktio-operaation toteutuksessa, että vertailu on aina `=`-muotoinen, eli operaation ei tarvitse sallia muunlaisia vertailuja.

## Koodin testaaminen (Python)

Seuraava koodi testaa Python-koodin toimintaa:

```python
products = Relation(("id", "name", "price"))

products.add_tuple((1, "retiisi", 7))
products.add_tuple((2, "porkkana", 5))
products.add_tuple((3, "nauris", 4))
products.add_tuple((4, "lanttu", 8))
products.add_tuple((5, "selleri", 4))

print(products)

print(projection(products, ("name",)))
print(projection(products, ("price",)))
print(projection(products, ("name", "price")))

print(restriction(products, "name", "porkkana"))
print(restriction(products, "price", 4))

print(projection(restriction(products, "price", 4), ("name",)))
```

Koodin tulostuksen tulisi näyttää seuraavan kaltaiselta:

```
{(1, 'retiisi', 7), (2, 'porkkana', 5), (3, 'nauris', 4), (5, 'selleri', 4), (4, 'lanttu', 8)}
{('lanttu',), ('selleri',), ('retiisi',), ('nauris',), ('porkkana',)}
{(7,), (8,), (4,), (5,)}
{('lanttu', 8), ('selleri', 4), ('retiisi', 7), ('nauris', 4), ('porkkana', 5)}
{(2, 'porkkana', 5)}
{(3, 'nauris', 4), (5, 'selleri', 4)}
{('nauris',), ('selleri',)}
```

## Koodin testaaminen (R)

Seuraava koodi testaa R-koodin toimintaa:

```r
products <- Relation(c("id", "name", "price"))

products <- add_tuple(products, c(1, "retiisi", 7))
products <- add_tuple(products, c(2, "porkkana", 5))
products <- add_tuple(products, c(3, "nauris", 4))
products <- add_tuple(products, c(4, "lanttu", 8))
products <- add_tuple(products, c(5, "selleri", 4))

print(products)

print(projection(products, c("name")))
print(projection(products, c("price")))
print(projection(products, c("name", "price")))

print(restriction(products, "name", "porkkana"))
print(restriction(products, "price", 4))

print(projection(restriction(products, "price", 4), c("name")))
```

Koodin tulostuksen tulisi näyttää seuraavan kaltaiselta:

```
  id     name price
1  1  retiisi     7
2  2 porkkana     5
3  3   nauris     4
4  4   lanttu     8
5  5  selleri     4

      name
1  retiisi
2 porkkana
3   nauris
4   lanttu
5  selleri

  price
1     7
2     5
3     4
4     8

      name price
1  retiisi     7
2 porkkana     5
3   nauris     4
4   lanttu     8
5  selleri     4

  id     name price
2  2 porkkana     5

  id    name price
3  3  nauris     4
5  5 selleri     4

     name
3  nauris
5 selleri
```

## Palautusohje

Liitä raporttiin toteuttamasi koodi.
