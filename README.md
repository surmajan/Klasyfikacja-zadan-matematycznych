# Klasyfikacja zadań matematycznych (NLP)

Rozwiązanie zadania z konkursu Kaggle [Classification of Math Problems by Kasut Academy](https://www.kaggle.com/competitions/classification-of-math-problems-by-kasut-academy): przypisanie treści zadania do jednej z 8 kategorii matematycznych (algebra, geometria, analiza, prawdopodobieństwo, teoria liczb, kombinatoryka, algebra liniowa, algebra abstrakcyjna).

## Podejście

- Preprocessing tekstu z formułami LaTeX: oznaczanie wzorów, zamiana komend LaTeX na osobne cechy i normalizacja liczb.
- Wektoryzacja TF-IDF (n-gramy 1-3, 5000 cech).
- Modele XGBoost (z walidacją krzyżową) i CatBoost.

## Dane

10 189 zadań treningowych w 8 klasach o bardzo nierównej liczności (od 2618 do 86 przykładów). Pliki `train_math.csv` i `test_math.csv` pochodzą z konkursu i nie są dołączone do repozytorium, więc pobierz je ze strony konkursu i umieść obok notebooka.

## Wyniki

| Model | Ocena | F1 |
|:--|:--|:-:|
| XGBoost | walidacja krzyżowa (3-fold, f1_macro) | 0,70 |
| CatBoost | zbiór treningowy | 0,85-0,87 |

Wyniki CatBoost są liczone na danych treningowych, więc nie można ich porównywać z wynikiem walidacji krzyżowej XGBoost.

## Uruchomienie

```bash
pip install -r requirements.txt
jupyter notebook klasyfikacja_zadan_matematycznych.ipynb
```

Trening CatBoost jest długi (rzędu godziny), a zapisane w notebooku wyniki można obejrzeć bez ponownego uruchamiania.
