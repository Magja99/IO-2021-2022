###### tags: `Inżynieria Oprogramowania` `semestr 3`

# RPGo! - faza konstrukcji

Zadania
1. Dla każdego scenariusza użycia skonstruować listę kroków uwzględniającą warunki początkowe, format wejścia/wyjścia (np. zdefiniować poprawny kod pocztowy `12345` lub `12-345` itd.). Najlepiej opisać też dokładnie co dzieje się w aplikacji (zmiana stanów w bazie danych, odpalenie jakiegoś modułu itp.)
2. ==Opracować pomiary umożliwiające sprawdzenie czy system spełnia wymagania niefunkcjonalne opisane we wcześniejszych dokumentach - musi być to zgodne z normami *ISO/IEC 9126* oraz *25000*==
3. Plan beta-testowania
4. ==Plan zarządzania jakością oprogramowania==
5. Dokładny plan wykonania produktu, dokładna ocena pracochłonności, dokładniejszy harmonogram
6. ==Ocena zgodności z koncepcją systemu i specyfikacją wymagań==

---

## Scenariusze testowe

### Scenariusz 1: Logowanie / Rejestracja
Warunki początkowe: Użytkownik próbuje wejść do aplikacji nie będąc zarejestrowanym lub zalogowanym
| Użytkownik chce sie zarejestrować                                                                                                                                                                                                                                                                                                                                              |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| użytkownik zostaje poproszony o typ rejestracji. Do wyboru ma zarejstrowanie się za pomocą Facebooka, oraz za pomocą adresu email.                                                                                                                                                                                                                                             |
| w przypadku rejestracji przez facebooka zostanie on przekierowany na strone fb i tam poproszony o udzielenia pozwolenia na zarejstrowanie się poprzez aplikację                                                                                                                                                                                                                |
| w przypadku rejestracji poprzez adres e-mail zostanie on przekierowany do interfejsu tworzącego konto użytkownika.                                                                                                                                                                                                                                                             |
| użytkownik zostaje poproszony o podanie adresu e-mail. Adres musi zostać podany w formacie przykład@email.com/pl. Jeśli adres nie spełnia tego wymogu wyświetli się okno błędu z komunikatem “Nieprawidłowy adres email”                                                                                                                                                       |
| adres email zostanie wyszukany w bazie. Jeżeli takowy już istnieje, zostanie wyświetlone okno błędu z komunikatem “Adres email już istnieje”                                                                                                                                                                                                                                   |
| użytkownik zostaje poproszony o podanie hasła. Hasło musi zawierać przynajmniej jedną wielką literę, cyfrę, małą literę oraz znak interpunkcyjny. Musi również zawierać conajmniej 8 znaków. Jeśli hasło nie spełnia tych wymogów kolejne okna do podania informacji zostaną wyszarzone i nie będzie można ich wypełnić                                                        |
| użytkownik zostaje poproszony o ponowne podanie hasła. Po podaniu hasła zostaną porównane i jeśli zaistnieje pomiędzy nimi jakaś różnica wyświetli się okno błędu z komunikatem “Różne hasła”                                                                                                                                                                                  |
| użytkownik zostaje poproszony o login. W tym przypadku po podaniu loginu sprawdzone zostaje czy nie ma on formatu odpowiadającego adresowi email. Następnie zostanie on wyszukany w bazie danych. Jeżeli taki login już istnieje użytkownik zostanie o tym poinformowany i nie będzie miał możliwości dalszej rejestracji dopóki nie poda loginu który nie istnieje w bazie. |
---
| 2. Użytkownik chce się zalogować                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| - użytkownik zostaje poproszony o login lub adres email oraz hasło. System rozpoznaje czy został podany login czy adres email sprawdzając format jak powyżej. Następnie email, lub login zostaje wyszukany w bazie. Hasło podane przez gracza zostaje zaszyfrowane oraz porównane z wynikiem zapytania. Jeśli hasła się nie zgadzają zostanie wyświetlone okno błędu z komunikatem "Błędne hasło". W przeciwnym wypadku użytkownik zostanie przekierowany do aplikacji. |
---
| 3. Użytkownik loguje się jako gość                                                                                                                                                                                                                                                                                             |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| - użytkownikowi przydzielane zostaje jednorazowo wygenerowane id które zostanie dodane do bazy i będzie mogło tworzyć relacje w bazie tak jak zwykli zalogowani użytkownicy. Po zamknięciu witryny przez użytkownika id oraz wszystkie relacje zostaną usunięte. Użytkownik automatycznie zostanie przekierowany do aplikacji. |
### Scenariusz 2: Tworzenie nowej rozgrywki
Warunki początkowe: Użytkownik jest zalogowany (nie jako gość), ale nie utworzył jeszcze żadnej rozgrywki
| 1. Utworzenie nowej rozgrywki                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |   |   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|
| - użytkownik zostaje przekierowany do panelu w którym będzie mógł zaznaczyć typ rozgrywki. Następnie w bazie zostanie utworzony nowy pokój do którego będzie przypisany użytkownik z uprawnieniami mistrza gry. Wygeneruje się również kod alfanumeryczny z adresem danego pokoju który inni użytkownicy będą mogli wprowadzić aby dołączyć do gry. Po wprowadzeniu adresu pokoju do jednego z pól aplikacji pod nazwą "Dołącz do rozgrywki" zostaną oni poproszeni o zalogowanie/wejście jako gość i potem adekwatnie przypisani w bazie danych |   |   |
| - po zostaniu mistrzem gry następuje faza przygotowania rozgrywki przez użytkownika. Mistrz gry w prawym dolnym rogu interfejsu ma przycisk umożliwiający rozpoczęcie rozgrywki (aka. udostępnienie jej innym graczom). Dopóki go nie naciśnie ma możliwość edycji map, czli ustawienie przeciwników, modyfikacja ich statystyk, oraz wybranie pól akcji specjalnych. Będzie mieć również możliwość dodawania notatek tylko do wglądu własnego.                                                                                                  |   |   |

### Scenariusz 3: Uruchomienie modułu do gry na odległość od strony zwykłego użytkownika
Warunki początkowe: Użytkownik klikną w link "Dołącz do pokoju" i zostaje "wciągnięty" do rozgrywki.
| Kroki                                 | Opisy                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1. Użytkownik wchodzi do pokoju.      | W bazie danych dla danego pokoju zapisuje się który użytkownik jest online. Jeśli jest to zapisany użytkownik, zmieniona zostanie tylko wartość, jeśli gość - wartość zostanie dodana. Jeśli gracz nie ma przywilejów mistrza gry, zostanie dla niego uruchomiony bazowy interfejs bez możliwości jakie przysługują mistrzowi gry. Interfejs będzie zawierał kanały głosowe, listę innych graczy oraz informacje czy są oni online, przysługującą mu kartę bohatera, mapę (jeśli takowa należy do rozgrywki) oraz widok kości                                                                                      |
| 2. Użytkownik łączy się głosowo.      | Dla danego kanału który wybrał użytkownik zostaje uruchomiony moduł służący do komunikatorów głosowycD                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| 3. Użytkownik wysyła wiadomość        | W przypadku przesyłania wiadomości w bazie danych w tabeli messeges będą zapisywać się dane o przesłanym komunikacie tj. treść, autor, oraz kanał na którym wiadomość została wysłana.                                                                                                                                                                                                                                                                                                                                                                                                                             |
| 4. Użytkownik wykonuje rzut kośćmi    | Po kliknięciu na obrazek odpowiadający danej kości, włączy się generator, który wylosuje liczbę z danego zakresu. Po wylosowaniu obraz kości zostanie podmieniony na taki na którym widnieje kość obrócona daną wartością do gracza. Dany rzut wyświetli się innym graczom i dopóki mistrz gry nie zaakceptuje danego rzutu, użytkownik nie będzie miał możliwości wykonania rzutu ponownie.                                                                                                                                                                                                                       |
| 5. Użytkownik wykonuje ruch na mapie. | Użytkownik klika na dane pole na mapie. Pola na mapie są reprezentowane w systemie jako obiekty z wartościami tj. koordynaty na obrazie, przeciwnicy stojący na polu, bohaterowie stojący na polu i czy na dane pole przysługuje akcja dodatkowa. Po stanięciu na polu, zapisane zostanie kto stoi na danym polu, oraz jeśli uwzględniona jest akcja dodatkowa, zostanie ona wylosowana ze zbioru akcji dodatkowych np. znalezienie skarbu. Na polu może stać tylko jeden bohater lub przeciwnik.                                                                                                                  |
| 6. Użytkownik wykonuje atak.          | Na początku sprawdzany jest zasięg ataku i możliwość wykonania go. Jeśli atak jest specjalny sprawdzane jest czy został już wykonany w przeciągu czasu określonego przez cooldown. Jeśli nie został wykonany zostaje on zapisany i przez następne kilka tur jest blokowana możliwość ponownego wykonania go. Zwykłe ataki można wykonywać dowoli. Jeśli atak obejmuje pola na których stoją przeciwnicy, użytkownik rzuca kośćmi na obrażenia i odpowiadającym przeciwnikom zostaje zadany wynik rzutu kośćmi. Jeżeli przeciwnik dostał obrażenia większe niż jego punkty życia zostaje on usunięty z danego pola. |
### Scenariusz 4: Uruchomienie modułu do gry na odległość od strony mistrza gry
Warunki początkowe: Użytkownik utworzył pokój i do niego wszedł.
| Kroki                              | Opisy                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1. Użytkownik wchodzi do pokoju.   | Tak jak przy zwykłym użytkowniku, sprawdzane zostają uprawnienia. Gdy system sprawdzi, że dany użytkownik jest mistrzem gry zostanie mu ukazany bardziej rozbudowany interfejs niż zwykłemu użytkownikowi. Dodatkowe funkcjonalności dla mistrza: możliwość podglądu kart graczy, przycisk do blokowania możliwości rzutów, dostęp do wyświetlenia właściwości każego pola na mapie.                                                                                                              |
| 2. Użytkownik wykonuje rzut kośćmi | rzuty mistrza gry nie są widoczne dla innych użytkowników. Nie ma on też ograniczeń w postaci blokady możliwości rzutów.                                                                                                                                                                                                                                                                                                                                                                                       |
| 3. Ruchy na mapie                  | mistrz gry może poruszać się na mapie przeciwnikami, w ten sam sposób w jaki gracze poruszają się własnymi postaciami. Każdy przeciwnik jest zapisany w systemie jako obiekt, ma własne statystyki, zakresy ruchów oraz ataki. Mistrz gry może te statystyki dowolnie zmieniać przed rozpoczęciem rozgrywki. Po rozpoczęciu jedyna modyfikowalną wartością będzie zdrowie przeciwnika które będzie się uaktualniać automatycznie podczas zadawanych mu obrażeń na co mistrz będzie już miał ograniczony wpływ. |
---
Połączenia fukcjonują tak samo jak w przypadku zwykłego użytkownika.

## Sprawdzenie wymagań niefunkcjonalnych
Na podstawie normy ISO/IEC 9126 wyróżniliśmy następujące pomiary umożliwiające zweryfikowanie spełnienia wymagań niefunkcjonalnych:
* **Efektywność** - dowolne standardowe zapytanie powinno zajmować nie dłużej niż 2 sekundy na przeciętnym procesorze
* **Bezpieczeństwo** - algorytm generujący kody dostępu powinien być nieco bardziej wyrafinowany, chcemy ograniczyć przypadki kiedy ktoś uzyskał dostęp do nie swojej rozgrywki do 10 rocznie.
* **Zachowanie anonimowości** - odsetek funkcji dostępnych tylko po podaniu prawdziwych danych powinien być niewielki (około 10-20\%) np. tylko podłączenie do mediów społecznościowych i newsletter
* **Niezawodność** - liczba błędów na godzinę użytkowania nie powinna przekraczać 1. Konieczne jest odpowiednie przechwytywanie błędów czy diagnozy sytuacji wyjątkowych po to, żeby błąd nie powodował np. nagłego zamknięcia aplikacji. Zaprojektujemy rózwnież sieć "checkpointów", które umożliwiłyby odtworzenie ostatnich kroków - średnia utraconych ruchów w aplikacji przy nagłym zatrzymaniu nie powinna przekraczać 5.
* **Użyteczność** - niezwykle ważna jest intuicyjność interfejsu, nakład pracy potrzebny do odkrycia/nauczenia się obsługi 80\% funcji aplikacji nie powinien być większy niż 1-2 godziny.
* **Wydajność** - aplikacja nie powinna zajmować zbyt dużo pamięci na dysku i pamięci RAM.
* **Łatwość konserwacji** i analizy - warto zwrócić uwage na to, jak duży nakład pracy jest potrzebny ze strony zespołu programistycznego w celu naprawienia średniego błędu. Chcemy kontrolować też nakład pracy potrzebny do zaimplementowania i przetestowania zmiany o przeciętnej złożoności.
* **Przenośność**, w tym łatwość wdrożenia i instalacji - średni czas instalacji (dane zebrane od użytkowników na różnych poziomach zaawansowania, w różnym wieku i korzystających z różnych systemów) nie powinien przekraczać 15 minut.

## Beta-testowanie

#### Faza I: Testy pod kątem bezpieczeństwa danych użytkowników (2 miesiące)
Zanim aplikacja trafi do użytkowników mogących testować ją w praktyce chcielibyśmy się upewnić że jest jest ona przetestowana pod kątem bezpieczeństwa.
Człowiek wcześniej zatrudniony do sprawdzania bezpieczeństwa przez dwa miesiące będzie próbował zhakować aplikację aby wykryć jak najwięcej możliwych luk w systemie bezpieczeństwa.

#### Faza II: Testy pod kątem funkcjonalności aplikacji (3 miesiące)
Zatrudnieni w firmie programiści nie mający udziału w budowie aplikacji będą mieli za zadanie:
1. Warunki początkowe: włączony jest interfejs do wyboru rozgrywki.
 Test: sprawdzenie czy typy rozgrywek oraz odpowiadające im elementy takie jak sposoby budowy map i systemy tworzenia kart nie mieszają się.
2. Warunki początkowe: wygenerowany zostaje kod alfa numeryczny z adresem pokoju.
Test: poprawność przypisywania gracza do rozgrywki oraz zapisywania jego danych w danym pokoju jeśli jest/nie jest gościem.
3. Warunki początkowe: użytkownik przeprowadza interakcję z interfejsem logowania / rejestracji
Test: sprawdzanie rejestracji / logowań przy użyciu różnych danych.
4. Warunki początkowe: użytkownik tworzy grę, inni użytkownicy wchodzą do pokoju i mistrz gry nadaje im prawa.
Test: testowanie danych uprawnień użytkowników w praktyce.
5. Warunki początkowe: Mistrz gry tworzy mapy w nowym pokoju.
Testy: próbowanie utworzenia map nie zgadzających się z systemami w jakich są tworzone (np. dwóch przeciwników na jednym polu)
6. Warunki początkowe: Mistrz gry zaprasza użytkowników do pokoju i zaczynają oni tworzyć kart bohaterów.
Testy: próbowanie wpisywania w karty bohaterów wartości które nie powinny się tam znaleźć (np. tekst w polu gdzie naley wpisać wartość w jakimś przedziale).

Ważne jest aby testy były przeprowadzane na różnych systemach oraz przeglądarkach.

#### Faza III Testy pierwszych użytkowników: (6 miesięcy)
Zareklamowany zostanie dostęp do gry w wersji early access. Użytkownicy zakładający konta będą mogli zgłaszać na bieżąco problemy za pomocą prostego formularza. Zachętą będzie możliwość dostępu do funkcjonalności płatnych w przyszłości gdy aplikacja zostanie wypuszczona w finalnej wersji.


## Plan zarządzania jakością oprogramowania
Wyróżniamy kilka najważniejszych kryteriów jakościowych: szczegółowa dokumentacja, konsekwentne stosowanie dobrych praktyk kodowania, regularne testowanie, nowoczesne narzędzia, zapewnienie bezpieczeństwa i poufności informacji.

W celu lepszej kontroli jakości naszego oprogramowania podejmiemy następujące kroki:
* Prędkość działania i awaryjność możemy sprawdzić zlecając testowanie różnym podmiotom na różnych systemach i sprzęcie.
* Kompatybilność (zarówno z zewnętrznymi aplikacjami jak i nowymi wersjami przeglądarek i systemów operacyjnych) możemy sprawdzić podczas testów, ale ważne jest również umożliwienie użytkownikom łatwego zgłaszania błędów.
* Bezpieczeństwo i poufność informacji zostanie zachowana dzięki ciągłemu stosowaniu powszechnie przyjętych standardów kodowania haseł itd.
* Kierownik projektu na bieżąco czuwa nad skończeniem kolejnych funkcji i wyznacza zadania dla zespołu.
* Podczas code review inni członkowie zespołu sprawdzają zgodność z ustalonymi zasadami kodowania i tylko wtedy zastwierdzają merge requesty. Tutaj pomoże korzystanie z narzędzi automatycznie sprawdzających format i strukturę kodu oraz zainstaloanie odpowiednich rozszerzeń do środowiska programistycznego.
* Opracowanie takiego systemu organizacji wyników testów, żeby łatwe było aktualizowanie go i identyfikacja (obecnych) najsłabszych ogniw aplikacji.
* Wykorzystanie narzędzi do kontroli wersji (np. GitLab) oraz zautomatyzowania kolejnych buildów aplikacji (coś podobnego do systemu Jenkins lub TeamCity).

## Dokładny plan wykonania produktu
#### Dokładny plan wykonania produktu, dokładna ocena pracochłonności, dokładniejszy harmonogram
1) Określenie funkcjonalności aplikacji (miesiąc)
2) Projektowanie aplikacji od strony zewnętrznej (miesiąc)
3) Projektowanie ze strony wewnętrzej (2 miesiące)
4) Pozyskanie oraz przygotowanie serwerów (miesiąc)
5) Implementacja razem z testami bieżącymi (3 miesiące)
6) Beta Testy (2 miesiące)
7) Poprawki (miesiąc)
8) Reklama (2 miesiące)
9) Publikacja

**Ocena pracochłonności:** 13 miesięcy optymistycznie

## Zgodność z koncepcją systemu i specyfikacją wymagań
Nie zostały dokonane liczne zmiany, ale będziemy musieli mocno ograniczyć liczbę dostępnych wariantów gry (ze względu na pracochłonność). Również opcja samodzielnej edycji zasad gry (w tym dodawanie nowych typów postaci i edycja relacji między nimi + dodawanie własnych zaklęć) zostanie zarezerwowana dla użytkowników *premium* jako, że jest to dosyć złożona operacja.

---

#### Notatki

*Wyrocznia testu* - szczegółowo opisany oczekiwany efekt końcowy tak, żeby przypisany tester mógł bez wątpliwości rozstrzygnąć czy zatwierdzić przypadek testowy

$X = 1 - \frac{A}{B}$

Dla każdego przypadku opisać też stan początkowy (co jest w bazie danych, połączenie sieciowe itd.)
