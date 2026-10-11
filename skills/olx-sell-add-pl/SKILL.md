---
name: olx-sell-add-pl
description: Wystawianie ogłoszeń sprzedaży na lokalnym OLX na podstawie tytułu, opisu, ceny i zdjęć. Użyj przy prośbach po polsku lub jawnej prośbie o polską wersję; język nie określa kraju OLX.
---

# olx-sell-add-pl

Wystaw ogłoszenie na koncie OLX użytkownika i sprawdź wynik publikacji. Rozmawiaj po polsku. Jawne ustawienia użytkownika dla bieżącego ogłoszenia mają pierwszeństwo. Język rozmowy, kraj OLX i język ogłoszenia to niezależne ustawienia. Zachowaj język dostarczonego tytułu i opisu; przy generowaniu opisu ustal język ogłoszenia, jeśli nie wynika z prośby.

## Rynek OLX

Ustal kraj i lokalny serwis OLX z prośby użytkownika lub otwartego formularza. Jeśli rynek jest niejasny, zapytaj o kraj lub adres serwisu. Nie wybieraj olx.pl tylko dlatego, że rozmowa jest po polsku. Korzystaj z bieżącego lokalnego formularza: etykiety przycisków, waluty, pola i usługi mogą różnić się między rynkami. Nie zakładaj dostępności funkcji znanych z polskiego OLX.

## Dane wejściowe

Przy każdym nowym ogłoszeniu zbierz świeże dane: tytuł, opis, zdjęcia, cenę, lokalizację i preferowany kontakt. Ustal walutę na podstawie wybranego rynku i formularza; w razie niejasności zapytaj. Nie przeliczaj ceny samodzielnie. Nie przenoś ceny, parametrów, opisu ani zdjęć z poprzedniego przedmiotu.

- Lokalizacja: użyj lokalizacji podanej przez użytkownika lub jego jawnie ustalonej preferencji. Nie przyjmuj domyślnego miasta. Jeśli brakuje lokalizacji lub wymaganej dzielnicy, dopytaj.
- Kontakt: użyj preferencji użytkownika i opcji dostępnych na lokalnym OLX. Jeśli użytkownik wybierze telefon, zachowaj numer z konta; nie wymyślaj numeru. Jeśli go brakuje, poproś o niego. Stosuj wymagania narzędzia dotyczące zgody na ujawnienie danych kontaktowych; nie traktuj samego załadowania skilla jako zgody na publikację danych.
- Wysyłka: deklaruj ją tylko na podstawie danych lub jawnych preferencji użytkownika. Nie dodawaj automatycznie zdania o wysyłce ani kontakcie. Nie dopisuj kosztów, przewoźnika ani terminu wysyłki bez danych użytkownika. Wzmianka w opisie nie upoważnia do włączenia usługi dostawy OLX.
- Cena jest konieczna do sprzedaży. Jeśli jej brakuje, zapytaj o nią. Nie szacuj ceny bez prośby użytkownika. Nie zaznaczaj negocjacji bez wskazania użytkownika.
- Zachowaj przesłaną kolejność zdjęć; pierwsze zdjęcie jest główne, chyba że użytkownik wskaże inaczej.
- Jeśli użytkownik poda sam tytuł, **zapytaj, czy wygenerować opis samodzielnie, czy użytkownik poda własny**. Nie generuj opisu przed odpowiedzią. Możesz w tym samym pytaniu poprosić o cenę i zdjęcia.
- Gdy użytkownik wybierze generowanie opisu, oprzyj go na podanych faktach i widocznych cechach ze zdjęć. Dopytaj o istotne brakujące dane. Nie dopisuj niepotwierdzonej sprawności, historii, wymiarów, pochodzenia czy warunków dostawy.
- Podany tytuł i opis zachowaj w brzmieniu użytkownika. Istotną zmianę wymuszoną limitem lub walidacją OLX uzgodnij z nim.
- Jeśli brakuje zdjęć, poproś o ich załączenie lub wskazanie plików. Jeśli użytkownik chce publikacji bez zdjęć, kontynuuj, o ile OLX to dopuszcza.

## Formularz OLX

Używaj dostępnego interfejsu OLX. Przy obsłudze przeglądarki używaj `cua_repl` i aktualnej dokumentacji jego API. Wykorzystaj otwarty formularz, jeśli istnieje; nie twórz drugiego ogłoszenia dla tego samego zadania. Nie zapisuj identyfikatorów kart, elementów formularza ani danych logowania w skillu.

1. Otwórz właściwy lokalny OLX i wybierz dodanie ogłoszenia (np. „Dodaj ogłoszenie”). Jeśli konieczne jest logowanie i nie można go dokończyć w autoryzowany sposób, pozostaw kartę przez `markHandoff()` i poproś użytkownika o zalogowanie. Po „gotowe” wróć do tego formularza. Zmiana ustawień rozszerzenia może odnowić połączenie i identyfikator przeglądarki — w razie niedostępnego połączenia sprawdź aktualny inwentarz i odzyskaj kartę formularza bez przeładowywania jej.
2. Wpisz tytuł, przejdź dalej i sprawdź sugerowaną kategorię. Zmień ją, jeśli nie odpowiada przedmiotowi.
3. Wpisz opis i cenę oraz wymagane parametry kategorii, korzystając z danych użytkownika i zdjęć. Nie zgaduj istotnych nieznanych parametrów.
4. Wybierz lokalizację **z listy podpowiedzi**. Samo wpisanie tekstu może pozostawić poprzednią lokalizację konta. Zweryfikuj wybrane miasto i dzielnicę w formularzu lub podglądzie.
5. Ustaw dostępne opcje kontaktu zgodnie z preferencją użytkownika. Jeśli wybrano telefon, zachowaj numer z konta. Jeśli potrzebna jest zgoda wymagana przez narzędzie, poproś o nią dla konkretnego numeru i lokalnego OLX, bez powtarzania już udzielonej zgody.
6. Dodaj zdjęcia. Przed uploadem przeczytaj dokumentację `file-uploads`. Użyj oczekiwania na `filechooser` przed kliknięciem przycisku, a następnie `setFiles()` z absolutnymi ścieżkami. Sprawdź obsługę wielu plików i zachowaj ich kolejność. Zweryfikuj liczbę zdjęć oraz lokalne oznaczenie zdjęcia głównego (np. „GŁÓWNE”) przy właściwym pliku.
7. Jeśli upload w Chrome wymaga „Allow access to file URLs”, przeczytaj `chrome-file-upload-troubleshooting` i przekaż instrukcję wymaganą przez narzędzie. Zachowaj formularz i wróć do uploadu po potwierdzeniu użytkownika. Nie publikuj bez zdjęć, które użytkownik polecił dodać.
8. Sprawdź podgląd: tytuł, opis, cenę i walutę, zdjęcie główne, parametry i lokalizację. Nie włączaj płatnego promowania, automatycznego przedłużania ani lokalnej usługi dostawy OLX (np. Przesyłki OLX) bez prośby użytkownika. Samo wspomnienie wysyłki w opisie nie oznacza wyboru takiej usługi.

## Publikacja i wynik

Polecenie „wystaw na OLX” oznacza zgodę na publikację przygotowanego ogłoszenia w podanym zakresie. Nie dokładaj ogólnego pytania o publikację, jeśli wszystkie wymagane dane i zgody są już dostępne.

Wybierz przycisk publikacji w lokalnym formularzu (np. „Dodaj ogłoszenie”). Jeśli OLX pokaże ofertę promowania, wybierz opcję bez promowania i potwierdź bezpłatne wystawienie. Polskie etykiety „Nie promuj” i „Tak, dodaj” są przykładami; rozpoznaj odpowiedniki w bieżącym interfejsie. Jeśli dodanie wymaga opłaty, zatrzymaj się przed płatnością i podaj konkretną kwotę oraz walutę; nie kupuj pakietu ani promowania bez autoryzacji.

Po wysłaniu sprawdź potwierdzenie aktywacji lub wpis na liście ogłoszeń konta (np. „Twoje ogłoszenia”). Jeśli wynik jest niepewny, najpierw sprawdź dostępne lokalnie statusy, w tym ogłoszenia aktywne, oczekujące i nieopłacone; nie ponawiaj publikacji, dopóki nie ustalisz, czy ogłoszenie już powstało.

Komunikat potwierdzenia nie zawsze oznacza publiczną widoczność: na polskim OLX „Ogłoszenie aktywowane” może oznaczać, że wpis nadal jest w zakładce „Oczekujące”. Podaj faktyczny status, zamiast twierdzić, że ogłoszenie jest już publicznie widoczne. Nie czekaj bez potrzeby na moderację po potwierdzeniu przyjęcia ogłoszenia.

W odpowiedzi końcowej podaj link do ogłoszenia z interfejsu, cenę z walutą i faktyczny status w lokalnym OLX. Krótko potwierdź rynek, lokalizację, tryb kontaktu i zdjęcie główne. Zapisz i osadź zrzut ekranu potwierdzenia zgodnie z dokumentacją przeglądarki, bez zbędnych danych prywatnych. Zachowaj kartę wyniku przez `markDeliverable()`.
