---
title: Opis Technologii
---
Dogłębny Opis Technologii zostanie umieszczony w [późniejszym terminie](../analiza-wykonalnosci.md/#kamienie_milowe)

# Matrix
![Wizualizacja protokołu](https://yuhu.ddns.net/images/service_matrix_network.png)

Matrix to otwarty standard i protokół komunikacyjny. Ma na celu umożliwienie bezproblemowej komunikacji w czasie rzeczywistym między różnymi dostawcami usług, w taki sam sposób, w jaki standardowa poczta e-mail (**S**imple **M**ail **T**ransfer **P**rotocol) obecnie działa w przypadku usługi przechowywania i przesyłania poczty e-mail, umożliwiając użytkownikom posiadającym konta u jednego dostawcy usług komunikacyjnych komunikowanie się z użytkownikami innego dostawcy usług za pośrednictwem czatu online, Voice over IP i wideotelefonii. Służy zatem podobnemu celowi jak protokoły takie jak XMPP, ale nie jest oparty na żadnym istniejącym protokole komunikacyjnym.

Z technicznego punktu widzenia jest to protokół komunikacyjny warstwy aplikacji do sfederowanej komunikacji w czasie rzeczywistym. Zapewnia interfejsy API HTTP i implementacje referencyjne typu open source do bezpiecznej dystrybucji i utrwalania wiadomości w formacie JSON za pośrednictwem otwartej federacji serwerów. Może integrować się ze standardowymi usługami internetowymi za pośrednictwem WebRTC, ułatwiając aplikacje między przeglądarkami.


# LDAP
**Lightweight Directory Access Protocol (LDAP)** – protokół przeznaczony do korzystania z usług katalogowych, bazujący na standardzie X.500. Jest to również nazwa usługi katalogowej pozwalającej na wymianę informacji za pośrednictwem TCP/IP.

LDAP jest wykorzystywany praktycznie w adresacji sieci Internet/Intranet w celu zapewnienia niezawodności, skalowalności i bezpieczeństwa danych. W odróżnieniu od X.500 nie potrzebuje ani szerokiego pasma, ani dużej mocy obliczeniowej. Pracuje w oparciu o protokół TCP/IP lub inne połączeniowe usługi transportu. Dane grupowane są w strukturze przypominającej drzewo katalogów. Każdy obiekt jest jednoznacznie identyfikowany poprzez swoje położenie w drzewie, tzw. Distinguished Name (DN).

LDAP w wielu sytuacjach uznawane jest za rozwiązanie lepsze od innych usług katalogowych, ponieważ korzystając z TCP/IP (które działa tylko w warstwie transportowej modelu OSI), daje niezwykle szybkie odpowiedzi na żądania zgłaszane przez klienta.


# OAuth 2.0
OAuth 2.0 to baranżowy standard wśród protokołów autoryzacji. OAuth 2.0 koncentruje się na prostocie programisty klienta, zapewniając jednocześnie określone przepływy autoryzacji dla aplikacji internetowych, aplikacji komputerowych, telefonów komórkowych i urządzeń w salonie. Ta specyfikacja i jej rozszerzenia są opracowywane w ramach grupy roboczej IETF OAuth.

# OpenID Connect
OpenID Connect 1.0 to prosta warstwa tożsamości oparta na protokole OAuth 2.0. Umożliwia Klientom weryfikację tożsamości Użytkownika końcowego na podstawie uwierzytelnienia przeprowadzonego przez Serwer Autoryzacyjny, a także uzyskanie podstawowych informacji o profilu Użytkownika końcowego w sposób interoperacyjny i podobny do REST.

OpenID Connect pozwala klientom wszystkich typów, w tym klientom internetowym, mobilnym i JavaScript, żądać i otrzymywać informacje o uwierzytelnionych sesjach i użytkownikach końcowych. Pakiet specyfikacji jest rozszerzalny, umożliwiając uczestnikom korzystanie z opcjonalnych funkcji, takich jak szyfrowanie danych tożsamości, wykrywanie dostawców OpenID i wylogowanie, gdy ma to dla nich sens.

# Cel w projekcie
Planowane jest wykorzystanie jednego lub więcej powyższych standardów w celu integracji z instniejącymi usługami politechniki (konta wykorzystywane przez [oauth.pwr.edu.pl/](oauth.pwr.edu.pl/) i/lub Google)


# Źródła
- Matrix: [en.wikipedia.org](https://en.wikipedia.org/wiki/Matrix_(protocol))
- LDAP: [pl.wikipedia.org](https://pl.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol)
- OAuth2.0: [oauth.net](https://oauth.net/2/)
- OpenID: [openid.net](https://openid.net/connect/)
