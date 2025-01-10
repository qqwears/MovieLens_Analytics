# ETL proces datasetu MovieLens
Tento repozitár obsahuje realizáciu ETL procesu pre analýzu dát z datasetu MovieLens. Proces zahŕňa kroky na extrakciu, transformáciu a načítanie údajov do dimenzionálneho modelu v Snowflake. Tento model je navrhnutý tak, aby umožňoval vizualizáciu a analýzu filmov, používateľov a ich hodnotení.
## 1. Úvod a popis zdrojových dát
Hlavným cieľom tohto semestrálneho projektu je preskúmať dáta súvisiace s filmami, používateľmi a ich hodnoteniami. Analýza pomáha odhaliť trendy v diváckych preferenciách, najobľúbenejšie filmy a vzorce správania používateľov. Odkaz na DB nájdete [tu](https://grouplens.org/datasets/movielens/).
### Zdrojove data:
- `movies`
- `occupations`
- `ratings`
- `users`
### 1.1 Dátová architektúra
#### ERD diagram MovieLens:
![*Obrázok 1 Entitno-relačná schéma MovieLens*](ERD_Diagram.png)
## 2. Dimenzionálny model
Bol vytvorený hviezdicový model (star schema), v ktorom je centrálnou tabuľkou faktov tabuľka `fact_ratings`, ku ktorej sú pripojené ďalšie dimenzie:

- `dim_dates`: dátumy hodnotení.
- `dim_movies`: názvy filmov.
- `dim_users`: údaje o používateľoch.

Vizualizácia štruktúry schémy je uvedená nižšie:
![*Obrázok 2 Schéma hviezdy pre MovieLens*](Star_Schema.png)
## 3. ETL proces v Snowflake
ETL proces zahŕňal tri kľúčové etapy: extrakciu (Extract), transformáciu (Transform) a načítanie (Load). Tento postup bol realizovaný v Snowflake s cieľom spracovať zdrojové dáta zo staging vrstvy a pripraviť ich na využitie v dimenzionálnom modeli určenom na analýzu a vizualizáciu.
### 3.1 Extract
#### 1. Vytvorenie tabuľky:
```sql
CREATE OR REPLACE TABLE ratings_staging (
    user_id INT,
    movie_id INT, 
    rating INT,
    rating_date timestamp
);
```
#### 2. Importovanie dát:
```sql
TRUNCATE TABLE ratings_staging;
COPY INTO ratings_staging
FROM @my_stage/ratings.csv
FILE_FORMAT = (TYPE = 'CSV' FIELD_DELIMITER = '\t' FIELD_OPTIONALLY_ENCLOSED_BY = '"' SKIP_HEADER = 0)
ON_ERROR = 'CONTINUE';
```
#### 3. Kontrola správneho fungovania:
```sql
SELECT * FROM ratings_staging;
```
To isté musíte urobiť so všetkými tabuľkami.
### 3.2 Transform



### 3.3 Load
