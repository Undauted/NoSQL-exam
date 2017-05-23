# Projekt Aggregation Pipeline (egzamin)

### Piotr Kacprowicz, Damian Centek, Daniel Banasiak

## Prezentacja

Opis agregacji i wyniki w [PDF](https://github.com/Undauted/NoSQL-exam/blob/master/Aggregation.pdf)

## Dane

Zbiór danych: [College Basketball Events](https://www.kaggle.com/c/march-machine-learning-mania-2017/data)

Plik RegularSeasonDetailedResults.csv

<h6>Liczba rekordów</h6>

```
Imported 76636 documents
```     

<h6>Przykładowy rekord</h6>

```
{
  "Season": 2003,
  "Daynum": 10,
  "Wteam": 1104,
  "Wscore": 68,
  "Lteam": 1328,
  "Lscore": 62,
  "Wloc": "N",
  "Numot": 0,
  "Wfgm": 27,
  "Wfga": 58,
  "Wfgm3": 3,
  "Wfga3": 14,
  "Wftm": 11,
  "Wfta": 18,
  "Wor": 14,
  "Wdr": 24,
  "Wast": 13,
  "Wto": 23,
  "Wstl": 7,
  "Wblk": 1,
  "Wpf": 22,
  "Lfgm": 22,
  "Lfga": 53,
  "Lfgm3": 2,
  "Lfga3": 10,
  "Lftm": 16,
  "Lfta": 22,
  "Lor": 10,
  "Ldr": 22,
  "Last": 8,
  "Lto": 18,
  "Lstl": 9,
  "Lblk": 2,
  "Lpf": 20
}
```

Plik Teams.csv

<h6>Liczba rekordów</h6>

```
Imported 364 documents
```   

<h6>Przykładowy rekord</h6>

```
{
  "Team_Id": 1101,
  "Team_Name": "Abilene Chr"
}
```

## Agregacje

1. Ilość fauli na przestrzeni 2003-2017
2. Wpływ boiska na wygraną
3. Zespoły które wygrywały ligę na przestrzeni lat 2003-2017
4. Najlepsza średnia rzutów za dwa i trzy 5 zespołów w lidze
5. Suma punktów wygranych i przegranych meczów na przestrzeni lat 2003-2017

## Zapytania z użyciem Pythona

Aby wykorzystać mongo w Pythonie należy wykorzystać pakiet PyMongo.

```
import pymongo
user = pymongo.MongoClient()
db = user.basketball
```

Nasze zapytanie w Pyhonie wygląda tak:
```
db.results.aggregate([
{
	$facet:{
		"Home":[stepHome1,stepHome2],
		"Away":[stepAway1,stepAway2],
		"Neutral":[stepNeutral1,stepNeutral2]
	}
}
]).pretty()
```


