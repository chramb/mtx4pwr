---
title: Fizyczne modele infrastruktury
---
# Terminologia
## Klient

Jest to aplikacja przeglądarkowa, desktopowa, lub aplikacja mobilna pozwalająca na połączenie z Serwerem (federacją) Matrix. 
Komunikują się bezpośrednio z serewrem za pomocą *Client-Server API*
Najpopularniejsze z nich to:

## Serwer Domowy
*ang. Homeserver*

Serwer z którym łączą się użytkownicy. Jest on złożony z wielu pokoi (niekoniecznie utworzonych na tym serwerze). Dzięki decentralizacji protokołu możliwe jest transparenna rozmowa z użytkownikami połączonymi z innymi serwerami oraz w pokojach na innych serwerach. Komunikują się między innymi serwerami za pomocą *Server-Server API*

## Usługa Aplikacji
*ang. Application Service*

Są to modułu działające wspólnie z serwerem Domowym pomagające na integrację oraz dodawanie arbitralnych funkcjonalności niezależnej od implementacji serwera.

Przykłady Usług aplikacji:

- Mosty *(bridges)* między innymi protokołami, np. IRC, SMTP
- Zaawansowane boty/integracje

## Systemy Tożsamości
*3PIDS - ang. 3rd Party Identity System*

Identyfikatory tożsamości pochodzące z innych systemów, usług lub kontenstów. Przykładami takich kontekstów mogą być:

- adres e-mail
- konta w serwisach społecznościowych 
- numery telefonów

W naszm przypadku wykorzystywane będą:

- LDAP - wraz z nr. indeksu
- OIDC - wykorzystywane z pomocą kont Google wykorzystywanych przez Politechnikę

# Monolityczna Implementacja
Jednym ze sposobów fizycznej implementacji jest stworzenie jednego domowego serwera (np `matrix.pwr.edu.pl`) i zagregowanie wszystkich użytkowników (studentów, wykładowców, innych pracowników uczelni).

**Zalety**

- Prostota implementacji
- Minimalizowanie zużycia zasobów
- Zcentralizowanie Administracji

**Wady**

- Ograniczna tolerancja na błędy oraz problemy z serwerem na poziomie protokołu/aplikacji - synapse(możliwe rozwiązanie na poziomie infrastruktury w zależności od wykorzystanych narzędzi

# Podział na wydziały/role
Alternatywnym modelem który można obrać jest podzielenie oddziałów/wydziałów na poszczególne serwery domowe co nie powinno stanowić większego problemu ze względu na założenia samego protokołu oczekujące decentralizacji serwerów.

**Przykłady podziałów:**

Przykład inspirowany podziałem e-mail'i:

- pracownicy serwer `<imię.nazwisko>:pwr.edu.pl`
- studenci `<indeks>:student.pwr.edu.pl`

podział na wydziały:

- np. `<indeks>:wit.pwr.edu.pl`

## Graficzny przykład podziału:

![Graficzny Przykład podziału infrastruktury](_img/diagram-architektury.png)

**Zalety**

- Replikacja danych oraz wysoka dostępowość

**Wady**

- Większe zużycie zasobów ze względu na replikację danych
- Problem: Jeden student - wiele wydziałów[^1]

[^1]: [GitHub/issue#246 - Decentralised user accounts](https://github.com/matrix-org/matrix-spec/issues/246)
