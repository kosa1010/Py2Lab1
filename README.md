# Wirtualne środowiska i zarządzanie pakietami w Pythonie

Zarządzanie pakietami oraz wirtualnymi środowiskami w Pythonie jest kluczowe dla pracy programisty. Dzięki nim możemy kontrolować wersje bibliotek i unikać konfliktów między różnymi projektami. Podczas tych zajęć omówimy narzędzia Pip, Conda oraz Virtualenv, a także porównamy ich możliwości i zastosowania.
2. Pip – podstawowe narzędzie do zarządzania pakietami

2.1 Instalacja pakietów
Pip to domyślny menedżer pakietów w Pythonie. Możemy go używać do instalowania bibliotek z repozytorium PyPI.
Przykłady:

'''console
pip install numpy  # Instalacja konkretnego pakietu
pip install numpy==1.21.0  # Instalacja konkretnej wersji
pip install -r requirements.txt  # Instalacja pakietów z pliku
'''
