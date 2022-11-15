---
title: Terminologia
---
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
