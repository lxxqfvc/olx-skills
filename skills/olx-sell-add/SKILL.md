---
name: olx-sell-add
description: Dodawanie ogłoszeń sprzedaży na OLX na podstawie tytułu, opisu i zdjęć, z domyślną lokalizacją Poznań, Stare Miasto oraz kontaktem przez telefon i czat. Użyj, gdy użytkownik chce wystawić przedmiot na OLX.
---

# olx-sell-add

Wystaw ogłoszenie na koncie OLX użytkownika i sprawdź wynik publikacji. Rozmawiaj po polsku. Jawne ustawienia użytkownika dla bieżącego ogłoszenia mają pierwszeństwo przed domyślnymi.

## Dane wejściowe

Przy każdym nowym ogłoszeniu zbierz świeże dane: tytuł, opis, zdjęcia i cenę. Miasto/dzielnica są opcjonalne. Nie przenoś ceny, parametrów, opisu ani zdjęć z poprzedniego przedmiotu.

- Domyślna lokalizacja: **Poznań, Stare Miasto**. Jeśli użytkownik poda inne miasto lub dzielnicę, użyj ich. Jeśli wybrane miasto wymaga dzielnicy, a jej nie podano i nie obowiązuje domyślna lokalizacja, dopytaj.
- Domyślny kontakt: **SMS na numer telefonu zapisany na koncie OLX + czat OLX**. Nie wymyślaj numeru. Jeśli nie ma numeru, poproś o niego. Stosuj wymagania narzędzia dotyczące zgody na ujawnienie danych kontaktowych; nie traktuj samego załadowania skilla jako zgody na publikację danych.
- Domyślnie w każdym opisie dodaj: **„Wysyłka możliwa. Kontakt przez SMS lub czat OLX.”** Jest to stała preferencja użytkownika, także przy opisie dostarczonym przez niego. Jawne inne warunki bieżącego ogłoszenia mają pierwszeństwo. Nie dopisuj kosztów, przewoźnika ani terminu wysyłki bez danych użytkownika. Ten zapis nie upoważnia do włączenia Przesyłki OLX.
- Cena jest konieczna do sprzedaży. Jeśli jej brakuje, zapytaj o nią. Nie szacuj ceny bez prośby użytkownika. Nie zaznaczaj negocjacji bez wskazania użytkownika.
- Zachowaj przesłaną kolejność zdjęć; pierwsze zdjęcie jest główne, chyba że użytkownik wskaże inaczej.
- Jeśli użytkownik poda sam tytuł, **zapytaj, czy wygenerować opis samodzielnie, czy użytkownik poda własny**. Nie generuj opisu przed odpowiedzią. Możesz w tym samym pytaniu poprosić o cenę i zdjęcia.
- Gdy użytkownik wybierze generowanie opisu, oprzyj go na podanych faktach i widocznych cechach ze zdjęć. Dopytaj o istotne brakujące dane. Nie dopisuj niepotwierdzonej sprawności, historii, wymiarów, pochodzenia czy warunków dostawy.
- Podany tytuł i opis zachowaj w brzmieniu użytkownika. Istotną zmianę wymuszoną limitem lub walidacją OLX uzgodnij z nim.
- Jeśli brakuje zdjęć, poproś o ich załączenie lub wskazanie plików. Jeśli użytkownik chce publikacji bez zdjęć, kontynuuj, o ile OLX to dopuszcza.

## Formularz OLX

Używaj dostępnego interfejsu OLX. Przy obsłudze przeglądarki używaj `cua_repl` i aktualnej dokumentacji jego API. Wykorzystaj otwarty formularz, jeśli istnieje; nie twórz drugiego ogłoszenia dla tego samego zadania. Nie zapisuj identyfikatorów kart, elementów formularza ani danych logowania w skillu.

1. Otwórz OLX i wybierz „Dodaj ogłoszenie”. Jeśli konieczne jest logowanie i nie można go dokończyć w autoryzowany sposób, pozostaw kartę przez `markHandoff()` i poproś użytkownika o zalogowanie. Po „gotowe” wróć do tego formularza. Zmiana ustawień rozszerzenia może odnowić połączenie i identyfikator przeglądarki — w razie niedostępnego połączenia sprawdź aktualny inwentarz i odzyskaj kartę formularza bez przeładowywania jej.
2. Wpisz tytuł, przejdź dalej i sprawdź sugerowaną kategorię. Zmień ją, jeśli nie odpowiada przedmiotowi.
3. Wpisz opis i cenę oraz wymagane parametry kategorii, korzystając z danych użytkownika i zdjęć. Nie zgaduj istotnych nieznanych parametrów.
4. Wybierz lokalizację **z listy podpowiedzi**. Samo wpisanie tekstu może pozostawić poprzednią lokalizację konta. Zweryfikuj wybrane miasto i dzielnicę w formularzu lub podglądzie.
5. Zachowaj numer telefonu z konta i czat zgodnie z ustawieniami kontaktu. Jeśli potrzebna jest zgoda wymagana przez narzędzie, poproś o nią dla konkretnego numeru i OLX, bez powtarzania już udzielonej zgody.
6. Dodaj zdjęcia. Przed uploadem przeczytaj dokumentację `file-uploads`. Użyj oczekiwania na `filechooser` przed kliknięciem przycisku, a następnie `setFiles()` z absolutnymi ścieżkami. Sprawdź obsługę wielu plików i zachowaj ich kolejność. Zweryfikuj liczbę zdjęć oraz oznaczenie „GŁÓWNE” przy właściwym pliku.
7. Jeśli upload w Chrome wymaga „Allow access to file URLs”, przeczytaj `chrome-file-upload-troubleshooting` i przekaż instrukcję wymaganą przez narzędzie. Zachowaj formularz i wróć do uploadu po potwierdzeniu użytkownika. Nie publikuj bez zdjęć, które użytkownik polecił dodać.
8. Sprawdź podgląd: tytuł, opis, cenę, zdjęcie główne, parametry i lokalizację. Nie włączaj płatnego promowania, automatycznego przedłużania ani Przesyłki OLX bez prośby użytkownika. Samo wspomnienie wysyłki w opisie nie oznacza wyboru Przesyłki OLX.

## Publikacja i wynik

Polecenie „wystaw na OLX” oznacza zgodę na publikację przygotowanego ogłoszenia w podanym zakresie. Nie dokładaj ogólnego pytania o publikację, jeśli wszystkie wymagane dane i zgody są już dostępne.

Kliknij „Dodaj ogłoszenie”. Jeśli OLX pokaże ofertę promowania, wybierz „Nie promuj”, a następnie „Tak, dodaj” w potwierdzeniu bezpłatnego wystawienia. Jeśli dodanie wymaga opłaty, zatrzymaj się przed płatnością i podaj konkretną kwotę; nie kupuj pakietu ani promowania bez autoryzacji.

Po wysłaniu sprawdź potwierdzenie aktywacji lub wpis w „Twoje ogłoszenia”. Jeśli wynik jest niepewny, najpierw sprawdź ogłoszenia aktywne, oczekujące i nieopłacone; nie ponawiaj publikacji, dopóki nie ustalisz, czy ogłoszenie już powstało.

„Ogłoszenie aktywowane” może oznaczać, że wpis nadal jest w zakładce „Oczekujące”. Podaj faktyczny status, zamiast twierdzić, że ogłoszenie jest już publicznie widoczne. Nie czekaj bez potrzeby na moderację po potwierdzeniu przyjęcia ogłoszenia.

W odpowiedzi końcowej podaj link do ogłoszenia z interfejsu, cenę i status. Krótko potwierdź lokalizację, tryb kontaktu i zdjęcie główne. Zapisz i osadź zrzut ekranu potwierdzenia zgodnie z dokumentacją przeglądarki, bez zbędnych danych prywatnych. Zachowaj kartę wyniku przez `markDeliverable()`.
