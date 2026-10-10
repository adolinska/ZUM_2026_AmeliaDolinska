# Zgłoszenie tematu

Odpowiedź mieści się na jednej stronie. Projekt dotyczy nadzorowanej klasyfikacji jednolabelowej: każdy przykład ma dokładnie jedną klasę.

1. Klasyfikacja egipskich hieroglifów przy użyciu konwolucyjnych sieci neuronowych.
2. Modalność: Obraz
3. Problem klasyfikacji: 95 klas znaków hieroglificznych. Klasami są nazwy opisowe egipskich hieroglifów.
4. Pytanie eksperymentalne: Jak zastosowanie fine-tuningu modelu pretrained wpływa na skuteczność klasyfikacji egipskich hieroglifów w porównaniu z wykorzystaniem tego samego modelu z zamrożonym ekstraktorem cech? Dodatkowo wyniki zostaną odniesione do prostego modelu CNN trenowanego od podstaw.
5. Źródło danych: https://www.kaggle.com/datasets/alexandrepetit881234/egyptian-hieroglyphs/data
6. Przybliżona wielkość zbioru: Około 35 MB i około 3 890 plików JPG. Dokładna liczba obrazów zostanie potwierdzona podczas przygotowania danych.
7. Lista klas i sposób oznaczenia etykiet: 95 klas znaków hieroglificznych. Etykiety są zapisane w plikach CSV w folderach `train`, `valid` i `test`. Każdy plik CSV zawiera kolumny: `filename`, `width`, `height`, `class`, `xmin`, `ymin`, `xmax`, `ymax`. Nazwy etykiet: '100', 'Among', 'Angry', 'Ankh', 'Aroura', 'At', 'Bad_Thinking', 'Bandage', 'Bee', 'Belongs', 'Birth', 'Board_Game', 'Book', 'Boy', 'Branch', 'Bread', 'Brewer', 'Builder', 'Bury', 'Canal', 'Cloth_on_Pole', 'Cobra', 'Composite_Bow', 'Cooked', 'Corpse', 'Dessert', 'Divide', 'Duck', 'Elephant', 'Enclosed_Mound', 'Eye', 'Fabric', 'Face', 'Falcon', 'Fingre', 'Fish', 'Flail', 'Folded_Cloth', 'Foot', 'Galena', 'Giraffe', 'He', 'Her', 'Hit', 'Horn', 'King', 'Leg', 'Length_Of_a_Human_Arm', 'Life_Spirit', 'Limit', 'Lion', 'Lizard', 'Loaf', 'Loaf_Of_Bread', 'Man', 'Mascot', 'Meet', 'Mother', 'Mouth', 'Musical_Instrument', 'Nile_Fish', 'Not', 'Now', 'Nurse', 'Nursing', 'Occur', 'One', 'Owl', 'Pair', 'Papyrus_Scroll', 'Pool', 'QuailChick', 'Reed', 'Ring', 'Rope', 'Ruler', 'Sail', 'Sandal', 'Semen', 'Small_Ring', 'Snake', 'Soldier', 'Star', 'Stick', 'Swallow', 'This', 'To_Be_Dead', 'To_Protect', 'To_Say', 'Turtle', 'Viper', 'Wall', 'Water', 'Woman', 'You'.
8. Licencja danych: CC BY 4.0 (Attribution 4.0 International), zgodnie z informacją na stronie Kaggle. Pierwotny zbiór został opublikowany w Roboflow Universe przez niezindetyfikowango użytkownika.
9. Proponowana jednostka generalizacji: Nowe obrazy symboli pochodzące z podobnego zbioru danych, niewykorzystywane podczas treningu ani doboru modelu.
10. Planowany baseline: Prosta konwolucyjna sieć neuronowa (CNN) trenowana od podstaw.
11. Wstępny pomysł na model pretrained: Model (np. ResNet18) z wcześniej wyuczonymi wagami, a następnie z fine-tuningiem wybranych warstw. 
12. Potencjalne ograniczenia obliczeniowe: Rozmiar obrazów wejściowych, zużycia pamięci podczas treningu, czasu obliczeń i dostępności GPU. Planowane są umiarkowane rozmiary obrazów i batchy oraz ograniczona liczba epok, tak aby kod i eksperymenty można było odtworzyć na komputerze domowym lub w darmowym Google Colab.
13. Dane osobowe, wrażliwe albo z ograniczeniami dostępu lub redystrybucji: Nie. Jest publicznie dostępny na Kaggle, a wskazana licencja to CC BY 4.0.