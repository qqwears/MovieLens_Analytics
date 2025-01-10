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
# 2. Dimenzionálny model


![*Obrázok 2 Schéma hviezdy pre MovieLens*](Star_Schema.png)
