# Dziennik eksperymentów

Skopiuj ten plik do `results/experiment_log.md`. Dopisuj jeden wpis na każdy eksperyment, którego wynik raportujesz. W Zadaniach 2 do 4 wpisy dotyczą wyłącznie validation.

## Wpis: CNN Baseline

- Data: 14.11.2026
- Zadanie: 2
- Poziom (A, B albo C): A
- Cel albo hipoteza: Uzyskanie bazowego wyniku klasyfikacji hieroglifów przy użyciu prostej konwolucyjnej sieci neuronowej trenowanej od podstaw. Wynik będzie punktem odniesienia dla modeli wykorzystujących transfer learning.
- Reprezentacja i preprocessing:
  - Obrazy wejściowe RGB.
  - Przycięcie obrazu na podstawie bounding boxów z pliku `_annotations.csv`, z niewielkim marginesem.
  - Zmiana rozmiaru do 64 × 64 px z zachowaniem proporcji obrazu.
  - Konwersja do tensora PyTorch.
  - Normalizacja wartości pikseli do zakresu [-1, 1].
- Model i hiperparametry:
  - CNN z trzema blokami konwolucyjnymi.
  - Liczba kanałów odpowiednio 16, 32, 64 w kolejnych blokach.
  - W każdym bloku: konwolucja 3 × 3, ReLU i MaxPooling 2 × 2.
  - Adaptive Average Pooling do rozmiaru 1 × 1.
  - Klasyfikator: Flatten, Dropout (0.3), Linear.
  - Funkcja straty: CrossEntropyLoss.
  - Optymalizator: Adam.
  - Learning rate: 0.001.
  - Batch size: 32.
  - Liczba epok: 20
- Co jest zamrożone, a co trenowane: Wszystkie warstwy modelu są trenowane od początku. Nie wykorzystano wag wstępnie wytrenowanych.
- Sposób wyboru hiperparametrów: Ocena wyników na zbiorze validation po każdej epoce. Wybór epoki na podstawie macro F1.
- Seed: 42.
- Wynik na validation (metryka główna i pomocnicze): Macro F1-score: 0.8946, Accuracy: 0.8946, Macro precision: 0.9115, Macro recall: 0.9000
- Koszt (czas, sprzęt, pamięć): Trening na CPU; Czas treningu z walidacją: 405.28 s
- Pliki z wynikami w `results/`: 
    - validation/cnn_baseline_classification_report.csv - szczegółowy raport metryk dla poszczególnych klas
    - validation/cnn_baseline_metrics.csv - metryki na validation
    - validation/cnn_baseline_predictions.csv - prawdziwa oraz przewidziana klasa
- Wnioski: Uzyskane wyniki wskazują, że model CNN osiąga dobre rezultaty w klasyfikacji hieroglifów na zbiorze walidacyjnym. Wysoka wartość Macro F1-score oraz zbliżone wartości Macro Precision i Macro Recall świadczą o dobrym balansie między poprawnością predykcji a rozpoznawaniem poszczególnych klas. Model poprawnie klasyfikuje większość hieroglifów, jednak nadal występują pomyłki między wizualnie podobnymi klasami, m.in. Boy i Man, Mascot i Divide oraz Fish i Nile_Fish. Jednym z możliwych ograniczeń jest niewielka rozdzielczość obrazów oraz stosunkowo prosta architektura, które mogą utrudniać rozpoznawanie drobnych szczegółów. Podsumowując, model stanowi dobrą konfigurację bazową do dalszych eksperymentów. W kolejnej części projektu zastosowany zostanie transfer learning, aby sprawdzić, czy bardziej zaawansowana architektura i wcześniej wyuczone reprezentacje pozwolą poprawić skuteczność klasyfikacji.