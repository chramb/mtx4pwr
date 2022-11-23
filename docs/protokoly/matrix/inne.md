---
title: Inne Protokoły
---
## WebRTC (Web Real-Time Communication)
Wolny i otwartoźródłowy projekt, część standardu HTML5 zapewniająca przeglądarkom internetowym oraz aplikacjom mobilnym możliwość komunikacji w czasie rzeczywistym
poprzez zestaw prostych interfejsów programowania (API). Podstawowym celem projektu jest umożliwienie komunikacji audio/video na stronach internetowych poprzez
bezpośrednią komunikację typu peer-to-peer, eliminując w ten sposób potrzebę instalacji wtyczek czy ściągania natywnych aplikacji.
Projekt jest wspierany przez takie firmy jak Apple, Google, Microsoft, Mozilla i Opera. 
Na obrazku przedstawiony jest schemat działania WebRTC:

<img src="https://cdn.ttgtmedia.com/rms/onlineimages/how_webrtc_works-f_mobile.png" width="600" />

## HTTP (ang. Hypertext Transfer Protocol)
Protokół przesyłania dokumentów hipertekstowych to protokół sieci WWW (ang. World Wide Web). Obecną definicję HTTP stanowi RFC 2616.
Za pomocą protokołu HTTP przesyła się żądania udostępnienia dokumentów WWW i informacje o kliknięciu odnośnika oraz informacje z formularzy.
Zadaniem stron WWW jest publikowanie informacji – natomiast protokół HTTP właśnie to umożliwia.
Protokół HTTP jest użyteczny, ponieważ udostępnia znormalizowany sposób komunikowania się komputerów ze sobą.
Określa on formę żądań klienta (tj. np. przeglądarki www) dotyczących danych oraz formę odpowiedzi serwera na te żądania.
Protokół http nazywany jest bezstanowym. Oznacza to, że nie przechowuje on żadnych danych.
Zaletą jest fakt, że nie przeciąża tym samym serwerów, jednak stanowi mniejsze bezpieczeństwo.
Najczęstszym rozwiązaniem tego problemu jest wprowadzenie mechanizmu ciasteczek.
HTTP standardowo korzysta z portu nr 80 (TCP).

Rozwinięciem protokołu HTTP jest wariant rozszerzony o ochrone przy pomocy szyfrowania protokołu **TLS (dawniej SSL)**.
Taki protokół nazywamy **HTTPS (ang. Hypertext Transfer Protocol Secure)**.
Szyfrowanie komunikacji ma zapobiegać jej przechwytywaniu między klientem i serwerem czy wręcz modyfikacji przesyłanych danych, zanim dotrą do celu.
W przeciwieństwie do niezabezpieczonego HTTP, którego serwery nasłuchują na porcie 80, serwery obsługujące HTTPS nasłuchują domyślnie na porcie 443 protokołu TCP.
Adresy URL protokołu zaczynają się od https://, podczas gdy adresy niezabezpieczonego HTTP od http://.

## TLS (ang. Transport Layer Security)
TLS to protokół kryptograficzny, który zapewnia kompleksowe bezpieczeństwo danych przesyłanych między aplikacjami przez Internet.
Protokół ten przyjęto jako standardowe rozwinięcie protokołu SSL. TLS jest znany użytkownikom w formie ikony kłódki wyświetlanej w przeglądarkach 
internetowych po ustanowieniu bezpiecznej sesji. Certyfikat TSL może być również wykorzystywany do innych aplikacji, takich jak poczta email,
przesyłanie plików, prowadzenia konferencji, komunikatorów internetowych i VoIP, a także do usług internetowych, takich jak DNS i NTP.
Na obrazku poniżej przedstawiona jest zasada działania najnowszej wersji protokołu TLS 1.3:

<img src="https://cdn.ttgtmedia.com/rms/onlineimages/security-tls_1.3_handshake-h.png" width="400" />

# Protokół TURN
To protokół, który pomaga w przechodzeniu przez translatory adresów sieciowych (NAT) lub zapory sieciowe dla aplikacji multimedialnych.
Może być używany z protokołem kontroli transmisji (TCP) i protokołem datagramów użytkownika (UDP). 
Jest to najbardziej przydatne dla klientów w sieciach zamaskowanych przez symetryczne urządzenia NAT.
TURN nie pomaga w uruchamianiu serwerów na dobrze znanych portach w sieci prywatnej przez NAT;
obsługuje połączenie użytkownika za NAT tylko z jednym peerem, jak na przykład w telefonii.
