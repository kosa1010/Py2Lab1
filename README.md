# Wirtualne środowiska i zarządzanie pakietami w Pythonie

## 1. Wprowadzenie
Zarządzanie pakietami oraz wirtualnymi środowiskami w Pythonie jest kluczowe dla pracy programisty. Dzięki nim możemy kontrolować wersje bibliotek i unikać konfliktów między różnymi projektami. Podczas tych zajęć omówimy narzędzia Pip, Conda oraz Virtualenv, a także porównamy ich możliwości i zastosowania. Środowisko wirtualne (zwane również jako virtualenv lub venv) jest niczym innym jak oddzielnym, dedykowanym środowiskiem (inna instancja Pythona), na którym można pracować. Innymi słowy, jest to sposób na uruchomienie na naszej maszynie dedykowanego miejsca, aby zainstalować tylko potrzebne pakiety. Dzięki posiadaniu oddzielnych środowisk dopasowanych do potrzeb Twoich projektów nie będziesz musiał zaśmiecać głównej instancji wszystkimi niezbędnymi pakietami. Dzięki temu będziesz mieć kontrolę nad wersjami pakietów i unikniesz chaosu.

## 2. Pip – podstawowe narzędzie do zarządzania pakietami
### 2.1 Instalacja pakietów
Pip to domyślny menedżer pakietów w Pythonie. Możemy go używać do instalowania bibliotek z repozytorium PyPI.

**Przykłady:**
```sh
pip install numpy  # Instalacja konkretnego pakietu
pip install numpy==1.21.0  # Instalacja konkretnej wersji
pip install -r requirements.txt  # Instalacja pakietów z pliku
```
W przypadku instalacji pakietów z pliku requiments.txt należy pamiętać aby podać pełną ścieżkę do pliku, albo być w konsoli w folderze z tym plikiem.

### 2.2 Aktualizacja i usuwanie pakietów
```sh
pip install --upgrade numpy  # Aktualizacja pakietu
pip uninstall numpy  # Usunięcie pakietu
```

### 2.3 Sprawdzanie zainstalowanych pakietów
```sh
pip list  # Lista zainstalowanych pakietów
pip freeze  # Lista pakietów w formacie requirements.txt
```

### 2.4 Tworzenie pliku requirements.txt
Aby zapisać listę zależności projektu, możemy użyć:
```sh
pip freeze > requirements.txt
```
Następnie, możemy odtworzyć środowisko w nowym miejscu:
```sh
pip install -r requirements.txt
```

## 3. Virtualenv – tworzenie izolowanych środowisk
Virtualenv pozwala tworzyć izolowane środowiska dla różnych projektów.

### 3.1 Instalacja Virtualenv
```sh
pip install virtualenv
```

### 3.2 Tworzenie wirtualnego środowiska
```sh
virtualenv my_env  # Tworzenie nowego środowiska
```

### 3.3 Aktywacja środowiska
- Windows:
  ```sh
  my_env\Scripts\activate
  ```
- Linux/macOS:
  ```sh
  source my_env/bin/activate
  ```

### 3.4 Dezaktywacja środowiska
```sh
deactivate
```

### 3.5 Usuwanie wirtualnego środowiska
Nie ma dedykowanej komendy do usunięcia środowiska, ale wystarczy usunąć katalog:
```sh
rm -rf my_env  # Linux/macOS
rd /s /q my_env  # Windows
```

## 4. Conda – alternatywne narzędzie do zarządzania środowiskami i pakietami
Conda to alternatywa dla Pip i Virtualenv, szczególnie użyteczna dla środowisk naukowych.

### 4.1 Instalacja Conda
Conda jest częścią Anacondy i Minicondy.

- Pobranie Minicondy: [https://docs.conda.io/en/latest/miniconda.html](https://docs.conda.io/en/latest/miniconda.html)

### 4.2 Tworzenie środowiska Conda
```sh
conda create --name my_env python=3.9
conda env list       # Wypisywanie listy środowisk wirtualnych
```

### 4.3 Aktywacja środowiska Conda
```sh
conda activate my_env
```

### 4.4 Instalacja pakietów
```sh
conda install numpy
```

### 4.5 Usuwanie środowiska
```sh
conda remove --name my_env --all
```

### 4.6 Eksportowanie i importowanie środowiska Conda
Aby zapisać zależności projektu w pliku:
```sh
conda env export > environment.yml
```
Aby odtworzyć środowisko:
```sh
conda env create -f environment.yml
```

## 5.Dokumentacja
W razie wątpliwości wszelkie informacje można znaleźć w dokumentacji: [Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html), [Pip](https://docs.python.org/pl/3.9/tutorial/venv.html)


## 6. Porównanie narzędzi Pip, Virtualenv i Conda
| Cecha            | Pip + Virtualenv | Conda |
|-----------------|----------------|------|
| Zarządzanie pakietami | Tak | Tak |
| Tworzenie izolowanych środowisk | Tak | Tak |
| Instalacja pakietów binarnych | Nie | Tak |
| Popularność w ML/DL | Średnia | Wysoka |

## 7. Dobre praktyki przy tworzeniu projektu w Pythonie
1. **Używanie wirtualnych środowisk** – zawsze twórz wirtualne środowisko dla każdego projektu.
2. **Struktura katalogów** – organizuj pliki w czytelny sposób:
```
my_project/
│-- my_project/
│   │-- __init__.py  # Plik inicjalizacyjny modułu
│   │-- main.py  # Główny plik aplikacji
│   │-- utils.py  # Dodatkowe funkcje pomocnicze
│-- tests/
│   │-- test_main.py  # Testy jednostkowe
│-- requirements.txt  # Lista zależności
│-- README.md  # Dokumentacja projektu
│-- .gitignore  # Plik ignorowania dla Git
```
3. **Plik `__init__.py`** – ten plik informuje Pythona, że dany katalog powinien być traktowany jako moduł.
   
   **Przykład użycia `__init__.py`**:
   ```python
   # my_project/__init__.py
   print("Witaj! Korzystasz z modułu my_project.")
   
   from .utils import pomocnicza_funkcja
   
   def inicjalizacja():
       print("Moduł my_project został poprawnie załadowany.")
   ```

## 8. Przydatne linki 
[Wirtualne środowiska Python](https://realpython.com/python-virtual-environments-a-primer/)  
[Repozytorium Virtualenv na GitHubie](https://github.com/pypa/virtualenv)
  
## 9. Zadania do wykonania

### Zadanie 1: Praca z Pip
1. Zainstaluj pakiet `requests` za pomocą `pip`.
2. Sprawdź jego wersję.
3. Zaktualizuj pakiet do najnowszej wersji.
4. Odinstaluj pakiet `requests`.
5. Zapisz listę zainstalowanych pakietów do pliku `requirements.txt` i odtwórz środowisko w nowym katalogu.

### Zadanie 2: Virtualenv
1. Zainstaluj `virtualenv`.
2. Stwórz wirtualne środowisko o nazwie `test_env`.
3. Aktywuj środowisko.
4. Zainstaluj pakiet `flask` w tym środowisku.
5. Dezaktywuj środowisko i usuń je.

### Zadanie 3: Conda
1. Zainstaluj Minicondę lub Anacondę.
2. Stwórz nowe środowisko Conda z Pythonem 3.8.
3. Aktywuj to środowisko.
4. Zainstaluj w nim pakiet `pandas`.
5. Wyeksportuj środowisko do pliku `environment.yml`.
6. Usuń całe środowisko i odtwórz je na nowo z pliku `environment.yml`.

# Dekoratory i generatory w Pythonie

## 1. Wprowadzenie
Dekoratory i generatory to zaawansowane mechanizmy w Pythonie, które ułatwiają pisanie eleganckiego i efektywnego kodu. 

- **Dekoratory** pozwalają na modyfikację funkcji lub metod bez konieczności ich zmieniania.
- **Generatory** to specjalne funkcje, które pozwalają na leniwe generowanie wartości, co jest szczególnie przydatne przy pracy z dużymi zbiorami danych.

## 2. Dekoratory w Pythonie
### 2.1 Czym są dekoratory?
Dekoratory to funkcje, które modyfikują inne funkcje. Są one często używane do logowania, kontroli dostępu, mierzenia czasu wykonania i innych operacji.

### 2.2 Tworzenie dekoratora
Przykładowy dekorator, który loguje wywołanie funkcji:
```python
import time

def logger(func):
    def wrapper(*args, **kwargs):
        print(f"Wywołano funkcję {func.__name__} z argumentami {args}, {kwargs}")
        result = func(*args, **kwargs)
        print(f"Funkcja {func.__name__} zwróciła {result}")
        return result
    return wrapper

@logger
def add(a, b):
    return a + b

add(2, 3)
```

### 2.3 Dekoratory z parametrami
Dekorator może przyjmować argumenty, np. dekorator mierzący czas wykonania funkcji:
```python
def time_it(repeat=1):
    def decorator(func):
        def wrapper(*args, **kwargs):
            start = time.time()
            for _ in range(repeat):
                result = func(*args, **kwargs)
            end = time.time()
            print(f"Czas wykonania: {end - start:.4f} sekundy")
            return result
        return wrapper
    return decorator

@time_it(repeat=3)
def slow_function():
    time.sleep(1)
    print("Gotowe!")

slow_function()
```

## 3. Generatory w Pythonie
### 3.1 Czym są generatory?
Generatory to funkcje, które zwracają iteratory. Zamiast `return`, używają `yield` do zwracania wartości i zachowują swój stan między wywołaniami.

### 3.2 Tworzenie generatora
Przykładowy generator liczb Fibonacciego:
```python
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

for num in fibonacci(10):
    print(num)
```

### 3.3 Generatory vs zwykłe listy
Porównanie generatora i listy przy dużych zbiorach danych:
```python
# Lista zajmuje dużo pamięci
numbers = [x**2 for x in range(10**6)]

# Generator zużywa mniej pamięci
numbers_gen = (x**2 for x in range(10**6))
```

## 4. Podsumowanie
- **Dekoratory** pozwalają na modyfikację funkcji w elegancki sposób.
- **Generatory** pozwalają na oszczędność pamięci i lepszą wydajność przy pracy z dużymi zbiorami danych.

## 5. Zadania do wykonania
### Zadanie 1: Dekoratory
1. Napisz dekorator `timer`, który mierzy czas wykonania funkcji.
2. Użyj go do zmierzenia czasu wykonania funkcji sortującej listę.

### Zadanie 2: Generatory
1. Napisz generator zwracający liczby pierwsze.
2. Napisz generator, który generuje nieskończony ciąg liczb parzystych.

