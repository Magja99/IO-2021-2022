# Inżynieria Oprogramowania - Zagadnienia
## Wykład 1
**1. Software** - oprogramowanie składające się z instrukcji oraz  napisanych przez człowieka. Jest to pewnego rodzaju abstrakcja modelowana przez użytkownika, której nie można dotknąć.
**2. Hardware** - rzeczy materialne związane ze sprzętem komputerowym np. procesor.
**3. Institute of Electrical and Electronics Engineers Standards Association** - jest jednostką operacyjną w ramach IEEE, która opracowuje globalne standardy w wielu branżach
![](https://i.imgur.com/1kNaUbJ.png)
**4. Walka ze złożonością**
- Zasada dekompozycji:
Rozdzielenie złożonego problemu na podproblemy, które można rozpatrywać i rozwiązywać niezależnie od siebie i niezależnie od całości.
- Zasada abstrakcji:
Eliminacja, ukrycie lub pominięcie mniej istotnych szczegółów rozważanego przedmiotu lub mniej istotnej informacji; wyodrębnianie cech wspólnych i niezmiennych dla pewnego zbioru bytów i wprowadzaniu pojęć lub symboli oznaczających takie cechy.
- Zasada ponownego użycia:
Wykorzystanie wcześniej wytworzonych schematów, metod, wzorców, komponentów projektu, komponentów oprogramowania, itd.
- Zasada sprzyjania naturalnym ludzkim własnościom:
Dopasowanie modeli pojęciowych i modeli realizacyjnych systemów do wrodzonych ludzkich własności psychologicznych, instynktów oraz mentalnych mechanizmów percepcji i rozumienia świata.

**5. Modelowania pojęciowe (conceptual modeling)** - modelowanie za pomocą środków takich jak dane, struktury danych lub innych które mają wspomagać ludzką wyobraźnię.
**6. Metodyka (Metodologia)**: - narzędzia np. języki, modele oraz metody np. sposobów postępowania służące do analizy oraz skutecznej i zorganizowanej pracy nad projektem
## Wykład 2
### Faza wstępna
**1. Analiza biznesowa** - sformułowanie potrzeby klienta, jaki jest problem, potem jak klient by chciał żeby to działało, grubsza analiza koncepcji systemu, orientacyjne oszacowanie kosztów, określenie zakresu przedsięwzięcia, analiza rozwiązań, określenie ograniczeń klienta
**Bardzo ważne jest wczesne określenie co ma zostać objęte systemem a co nie **
**2. Decyzje strategiczne** - wybór technik, narzędzi, modeli itp. oraz podjęcie decysji o współpracy z innymi producentami / zatrudnianie ekspertów, zidentyfikowanie ograniczeń np. czasowe
**3. Studium wykonalności** - dostępności, ograniczenia, niezbędne warunki, rozmiar projektu
**4. Harmonogram przedsięwzięcia** - ustalenie planu czasowego wykonywania poszczególnych zadań (testy, reklama, praca, zatrudnianie itp)
**5. Ocena rozwiązań** - koszty, czas, błędy na tydzień itp
**6. Modele szacowania kosztów**
- **Metoda COCOMO** - oszacowanie kosztów na podstawie liczby linijek w kodzie. Słaba bo możemy zastosować ją dopiero pod koniec pisania kodu.
- **Metoda punktów funkcyjnych** - zliczanie miejsc przechowywania danych, wejść/wyjść systemu. Mnożone przez wagi i sumowane. Stosowana gdy funkcje są już z grubsza opisane.
- **Metoda Delphi** - anonimowi eksperci szacują i brana jest średnia z ich szacowania![](https://i.imgur.com/PI7WKWG.png)
## Wykład 3
**1. Modele cyklu wytwarzania oprogramowania**:
- model kaskadowy (wodospadowy)
- model spiralny
- prototypowanie
- RUP
![](https://i.imgur.com/1z70qrg.png)
## Wykład 4
**1. Określenie Wymagań** - klient na początku może nie wiedzieć dokładnie czego chce więc robimy dalszą specyfikację. Praca z klientem w tym momencie jest ważna
**2. Problemy**:
- dużo specyfikacji nawet dla małych systemów
- klient nie zawsze wie czego chce
- duże systemy są wykorzystywane przez wielu użytkowników i ich cele są często sprzeczne
- zleceniodawca a użytkownik to dwie różne osoby ale klient ma zawsze rację. Tylko trzeba pokazać mu możliwości

**3. Poziomy określenia wymagań**:
- definicja wymagań - rezultat rozmowy z klientem
- specyfikacja wymagań - język naturalny + częściowo sformalizowane notacje
- specyfikacja oprogramowania - formalny opis wymagań

**4. Dobry opis wymagań**:
- opisuje zewnętrzne zachowanie programu a nie działanie od kuchni
- brać pod uwagę przyszłe możliwe zmiany
- obejmować ograniczenia
- opisywać zachowanie systemu w nieporządanych sytuacjach

**5. HISTORYJKI UŻYTKOWNIKÓW - opowiadania użytkowników dotyczące oczekiwanego działania systemów**

**6. Wymagania funkcjonalne** - opisują czynności wykonywane przez system:
- określenie wszystkich użytkowników którzy będą z systemu korzystać
- dla każdego użytkownika określenie funkcji systemu z jakiej będzie korzystać
- określenie zewnętrznych systemów (internet, sieć, serwery, bazy danych)
- prawna część
-
**7. Formularz wymagań**![](https://i.imgur.com/BwXv3EM.png)
**8. Wymagania niefunkcjonalne**
np. Każdy klient ma mieć własne id

## Wykład 5
