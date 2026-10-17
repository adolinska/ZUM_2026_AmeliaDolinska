# Projekt końcowy ZUM 2026/2027

To repozytorium rozwijasz przez cały semestr. Górna część tego pliku mówi, jak pracować. Dolna część to dokumentacja Twojego projektu, którą uzupełniasz w kolejnych zadaniach.

## Jak pracować z tym repozytorium

### Co robisz

Przeprowadzasz jeden wiarygodny eksperyment nadzorowanej klasyfikacji jednolabelowej. Każdy przykład ma dokładnie jedną klasę docelową. Pracujesz na tekście, obrazie, audio albo danych multimodalnych. Projekt jest indywidualny.

Projekt ma trzy poziomy:
1. **Poziom A. Punkt odniesienia.** Prosty, sensowny baseline.
2. **Poziom B. Podejście pretrained.** Co najmniej jedno podejście pretrained. Dobrym pierwszym krokiem jest zamrożony encoder i prosty klasyfikator. Fine tuning nie jest obowiązkowy.
3. **Poziom C. Jedno uzasadnione rozszerzenie.** Odpowiada na to samo pytanie projektu i nie zmienia zmiennej docelowej ani problemu klasyfikacyjnego.

Pełne zasady są w pliku [PROJECT_RULES.md](PROJECT_RULES.md). Przeczytaj je przed zgłoszeniem tematu.

### Od czego zacząć

1. Utwórz własne repozytorium z tego szablonu: wybierz „Use this template”, a następnie „Create a new repository”.
2. Nazwij repozytorium `ZUM_2026_ImięNazwisko`.
3. Repozytorium może być publiczne albo prywatne. Jeśli jest prywatne, dodaj konto prowadzącej wskazane na platformie kursu. Jeśli Twoje dane zawierają informacje osobowe albo wrażliwe, przeczytaj najpierw zasadę o prywatności w [zasadach projektu](PROJECT_RULES.md).
4. Przeczytaj [instrukcję zgłoszenia tematu](assignments/00_topic_submission.md) i zgłoś temat.

### Kolejność i terminy

Wszystkie terminy przypadają w niedzielę o godzinie 23:59. Wszystko oddajesz na platformie kursu.

| Etap | Instrukcja | Termin | Punkty | Co oddajesz |
|---|---|---|---|---|
| Zgłoszenie tematu | [00_topic_submission.md](assignments/00_topic_submission.md) | 18 października 2026 | 0, obowiązkowe | wypełniony szablon zgłoszenia |
| Zadanie 1 | [01_data_and_protocol.md](assignments/01_data_and_protocol.md) | 8 listopada 2026 | 15 | link do repozytorium i tag `task-1` |
| Akceptacja artykułu spoza listy | [scientific_paper_review.md](assignments/scientific_paper_review.md) | 22 listopada 2026 | 0, obowiązkowe dla źródeł spoza listy | pełny opis bibliograficzny oraz DOI albo oficjalny link |
| Zadanie 2 | [02_baseline.md](assignments/02_baseline.md) | 29 listopada 2026 | 15 | link i tag `task-2` |
| Artykuł naukowy | [scientific_paper_review.md](assignments/scientific_paper_review.md) | 6 grudnia 2026 | 10, poza projektem | plik PDF albo Markdown |
| Zadanie 3 | [03_pretrained.md](assignments/03_pretrained.md) | 20 grudnia 2026 | 20 | link i tag `task-3` |
| Zadanie 4 | [04_extension.md](assignments/04_extension.md) | 17 stycznia 2027 | 20 | link i tag `task-4` |
| Zadanie 5 | [05_final_evaluation.md](assignments/05_final_evaluation.md) | 31 stycznia 2027 | 30 | link oraz tagi `final-freeze` i `task-5` |

Projekt jest wart 100 punktów. Artykuł jest osobnym zadaniem za 10 punktów.

### Final test w skrócie

1. Final test wydzielasz w Zadaniu 1 i od razu go zamrażasz.
2. Do końca Zadania 4 nie uruchamiasz na nim żadnego modelu. Wszystkie porównania i wybór systemu robisz na validation.
3. W Zadaniu 5 wybierasz dokładnie jeden finalny system, zapisujesz go w `final_system.md` i tworzysz tag `final-freeze`.
4. Nie trenujesz systemu ponownie na `train + validation` ani na żadnym większym zbiorze.
5. Dopiero potem uruchamiasz final test, jeden raz, tylko dla tego systemu. Wynik testu nie może zmienić systemu.

Szczegóły są w [zasadach projektu](PROJECT_RULES.md), w części „Zasady final test”.

### Tagi Git

Każde oddanie wskazuje commit oznaczony tagiem. Oceniamy stan repozytorium z tego commita.

```bash
git add .
git commit -m "Zadanie 1: protokół i podział danych"
git tag -a task-1 -m "Zadanie 1"
git push origin main
git push origin task-1
```

Polecenie `git ls-remote --tags origin` pokazuje, czy tag jest już na GitHub. Tag możesz też utworzyć na stronie GitHub w zakładce Releases. Nie przesuwaj i nie usuwaj tagów po oddaniu.

### Gdzie co zapisujesz

| Miejsce | Co tam trafia |
|---|---|
| `README.md`, część dolna | dokumentacja projektu |
| `notebooks/` | notebooki kolejnych etapów |
| `src/` | kod wspólny dla notebooków (opcjonalnie) |
| `splits/` | identyfikatory przykładów train, validation i final test ([opis formatu](splits/README.md)) |
| `results/` | metryki i predykcje na validation, dziennik eksperymentów, wynik final test (dopiero po `final-freeze`); [opis układu](results/README.md) |
| `final_system.md` | zapis finalnego systemu (Zadanie 5); [szablon](templates/final_system_template.md) |
| `data/sample/` | mała próbka danych, jeśli licencja i zasady prywatności na to pozwalają |
| `templates/` | szablony do skopiowania |

### Czego nie wrzucasz

* pełnych zbiorów danych;
* dużych wag modeli i checkpointów (przechowujesz je poza repozytorium i opisujesz, gdzie są);
* danych, próbek ani identyfikatorów umożliwiających identyfikację osób;
* haseł, tokenów i kluczy API;
* plików tymczasowych środowiska.

Plik `.gitignore` blokuje typowe przypadki, ale to Ty odpowiadasz za zawartość repozytorium.

### Jak oceniamy

Liczy się poprawność metodologiczna, uzasadnienie decyzji i jakość analizy. Wysokość wyniku nie jest sama w sobie kryterium. Projekt z niższym F1, wykonany poprawnie i dobrze przeanalizowany, może dostać więcej punktów niż projekt z bardzo wysokim wynikiem uzyskanym przy wycieku danych. Kryteria każdego zadania są w jego instrukcji, a rubryka ogólna w [zasadach projektu](PROJECT_RULES.md).

---

# Dokumentacja projektu

Uzupełniaj sekcje w zadaniach podanych w nawiasach. Zastępuj teksty w nawiasach kwadratowych.

## Informacje ogólne

* Tytuł: Klasyfikacja egipskich hieroglifów przy użyciu konwolucyjnych sieci neuronowych
* Autor: Amelia Dolińska
* Modalność: Obraz
* Problem klasyfikacji: 95 klas znaków hieroglificznych. Klasami są nazwy opisowe egipskich hieroglifów.

## Problem i pytanie eksperymentalne (Zadanie 1)

Celem eksperymentu jest zbadanie, jak zastosowanie fine-tuningu modelu pretrained wpływa na skuteczność wieloklasowej klasyfikacji egipskich hieroglifów. Porównane zostaną trzy podejścia: model pretrained z zamrożonym ekstraktorem cech, ten sam model poddany fine-tuningowi oraz prosta sieć CNN trenowana od podstaw. Pozwoli to ocenić, czy dostosowanie wstępnie wytrenowanych wag do badanego zbioru poprawia wyniki względem wykorzystania zamrożonych cech i uczenia od podstaw.

## Dane i licencja (Zadanie 1)

* **Źródło danych:** https://www.kaggle.com/datasets/alexandrepetit881234/egyptian-hieroglyphs/data
* **Licencja danych:** CC BY 4.0 (Attribution 4.0 International), zgodnie z informacją na Kaggle. Pierwotny zbiór został opublikowany w Roboflow Universe przez niezindetyfikowango użytkownika.
* **Sposób pobierania:** Za pomocą biblioteki `kagglehub`, zostało to opisane w notebooku Zadania 1.
* **Liczba przykładów:** 3890
* **Liczba klas:** '100', 'Among', 'Angry', 'Ankh', 'Aroura', 'At', 'Bad_Thinking', 'Bandage', 'Bee', 'Belongs', 'Birth', 'Board_Game', 'Book', 'Boy', 'Branch', 'Bread', 'Brewer', 'Builder', 'Bury', 'Canal', 'Cloth_on_Pole', 'Cobra', 'Composite_Bow', 'Cooked', 'Corpse', 'Dessert', 'Divide', 'Duck', 'Elephant', 'Enclosed_Mound', 'Eye', 'Fabric', 'Face', 'Falcon', 'Fingre', 'Fish', 'Flail', 'Folded_Cloth', 'Foot', 'Galena', 'Giraffe', 'He', 'Her', 'Hit', 'Horn', 'King', 'Leg', 'Length_Of_a_Human_Arm', 'Life_Spirit', 'Limit', 'Lion', 'Lizard', 'Loaf', 'Loaf_Of_Bread', 'Man', 'Mascot', 'Meet', 'Mother', 'Mouth', 'Musical_Instrument', 'Nile_Fish', 'Not', 'Now', 'Nurse', 'Nursing', 'Occur', 'One', 'Owl', 'Pair', 'Papyrus_Scroll', 'Pool', 'QuailChick', 'Reed', 'Ring', 'Rope', 'Ruler', 'Sail', 'Sandal', 'Semen', 'Small_Ring', 'Snake', 'Soldier', 'Star', 'Stick', 'Swallow', 'This', 'To_Be_Dead', 'To_Protect', 'To_Say', 'Turtle', 'Viper', 'Wall', 'Water', 'Woman', 'You'.
* **Potencjalne źródła wycieku danych:** Występowanie identycznych w różnych podzbiorach. Przeprowadzono kontrolę nazw plików oraz hashy, nie wykrywając duplikatów identycznych bajt po bajcie ani powtarzających się nazw. Kontrola ta nie wyklucza jednak występowania obrazów wizualnie podobnych.
* **Znane Ograniczenia:** Brak klasy 'Mascot' w zbiorze testowym przygotowanym przez autora danych, co uniemożliwia ocenę skuteczności modelu dla tej klasy na podstawie tego podzbioru.

## Protokół (Zadanie 1)

* **Jednostka generalizacji:** Obrazy symboli
* **Podział:** Zastsowano podział przygotwany wcześniej przez autora danych, w którym proporcje podziału wynoszą 70/20/10. Dystrybucja klas pomiędzy podzbiorami została opisane w notebooku Zadania 1. Podczas przeprowadzonego audytu danych nie zostały wykryte istotne nieprawidłowości w istniejącym podziale danych. Jedyne ograniczenie zostało opisane w sekcji wyżej.
* **Metryka główna i pomocnicze:** Metryka głównąbędzie macro F1-score, ponieważ klasy mają różną liczebność w poszczególnych podzbiorach, a uśrednianie makro nadaje każdej klasie jednakową wagę. F1-score uwzględnia zarówno precision, jak i recall, zapewniając zrównoważoną ocenę skuteczności klasyfikacji różnych hieroglifów, zamiast skupiać się wyłącznie na odsetku poprawnych predykcji. Metryki pomocnicze: accuracy, macro precision i macro recall, które uzupełnią ocenę modelu o ogólną skuteczność klasyfikacji oraz szczegółowe informacje o poprawności i kompletności rozpoznawania klas.
* **Seed:** 42. Zostanie wykorzystany do kontrolowania losowości, w tym inicjalizacji wag oraz kolejności próbek podczas treningu.
* **Final test:** zamrożony w commicie z tagiem `task-1`, identyfikatory w `splits/`. Jeśli podział był później poprawiany, podaj commit poprawionej wersji i opisz zmianę w dzienniku zmian.

| Zbiór | Liczba przykładów | Liczba niezależnych jednostek |
|---|---|---|
| train |2723|95|
| validation |778|95|
| final test |389|94|

## Wyniki (Zadania 2 do 5)

Wyniki na validation:

| Podejście | Zadanie | Metryka główna | Metryki pomocnicze | Czas i sprzęt | Uwagi |
|---|---|---|---|---|---|
| Trivial baseline | 2 | | | | |
| Baseline | 2 | | | | |
| Podejście pretrained | 3 | | | | |
| Rozszerzenie | 4 | | | | |

Wynik na final test, wyłącznie dla finalnego systemu i dopiero po utworzeniu tagu `final-freeze`:

| System | Metryka główna | Metryki pomocnicze |
|---|---|---|
| [nazwa z `final_system.md`] | | |

## Finalny system (Zadanie 5)

Pełny zapis jest w `final_system.md`. [Krótkie uzasadnienie wyboru na podstawie validation.]

## Reprodukcja

- **Wersja Pythona:** Python 3.13.16.
- **Instalacja środowiska:** instalacja wymaganych bibliotek na podstawie pliku `requirements.txt`.
- **Pobranie danych:** zbiór danych jest pobierany z Kaggle za pomocą biblioteki `kagglehub`:

```python
import kagglehub

path = kagglehub.dataset_download(
    "alexandrepetit881234/egyptian-hieroglyphs"
)
print("Path to dataset files:", path)
```

- **Kolejność uruchamiania:** Kod do Zadania 1 znajduje się w całości w notebooku `notebooks/01_data_and_protocol.ipynb`.
- **Sprzęt:** Google Colab (Zadanie 1 - CPU)
- **Przybliżony czas wykonania:** Zadanie 1 - około 10 sekund, bez uwzględnienia ewentualnego czasu pobierania danych.

## Ograniczenia

* **Ograniczenia danych:** Brak klasy 'Mascot' w zbiorze testowym przygotowanym przez autora danych, co uniemożliwia ocenę skuteczności modelu dla tej klasy na podstawie tego podzbioru.

## Dziennik zmian

| Data | Zadanie | Co zmieniono i dlaczego |
|---|---|---|
| 17.10.2026 | Zadanie 1 | Dodanie plików do Zadanie 1 oraz aktualizacja README.md |

## Licencja projektu

Kod źródłowy projektu jest udostępniony na licencji MIT. Zbiór danych wykorzystywany jest zgodnie z warunkami licencji CC BY 4.0 wskazanej na stronie Kaggle.
