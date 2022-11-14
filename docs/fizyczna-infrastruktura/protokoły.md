---
title: Wykorzystywane protokoły
---
# **Protokoły szyfrowania używane w Matrixie**

## ED25519
To system klucza publicznego oparty na krzywej eliptycznej, powszechnie używany do uwierzytelniania SSH.
Wcześniej klienci EC2 mogli używać kluczy opartych na RSA do uwierzytelniania w instancjach EC2,
gdy potrzebowali nawiązać bezpieczne połączenia w celu wdrożenia instancji w EC2 i zarządzania nimi.

## Curve25519 identity key pair
To system kryptograficzny z kluczem publicznym, który można wykorzystać do ustanowienia wspólnego sekretu.
W systemie Matrix każde urządzenie ma długowieczny klucz tożsamości Curve25519, który jest używany do nawiązywania sesji Olm z tym urządzeniem.
Klucz prywatny nigdy nie powinien opuszczać urządzenia, ale część publiczna jest podpisana kluczem linii papilarnych Ed25519 i opublikowana w sieci.

## Curve25519 one-time keys
Oprócz klucza tożsamości każde urządzenie tworzy pewną liczbę par kluczy Curve25519, które są również używane do ustanawiania sesji Olm, ale mogą być użyte tylko raz.
Po raz kolejny część prywatna pozostaje na urządzeniu. Podczas uruchamiania Alice tworzy pewną liczbę jednorazowych par kluczy i publikuje je na swoim serwerze domowym.
Jeśli Bob chce nawiązać sesję Olma z Alicją, musi odebrać jeden z kluczy jednorazowych Alicji i utworzyć nowy własny.
Te dwa klucze, wraz z kluczami tożsamości Alicji i Boba, są używane do ustanowienia sesji Olm między Alicją i Bobem.

## Megolm encryption keys 
Klucz Megolm służy do szyfrowania wiadomości grupowych (w rzeczywistości służy do uzyskiwania klucza AES-256 i klucza HMAC-SHA-256).
Jest inicjowany losowymi danymi. Za każdym razem, gdy wiadomość jest wysyłana, na kluczu Megolm wykonywane jest obliczenie skrótu,
aby uzyskać klucz dla następnej wiadomości. W związku z tym możliwe jest udostępnienie bieżącego stanu klucza Megolm użytkownikowi,
co pozwala mu odszyfrować przyszłe wiadomości, ale nie przeszłe wiadomości.

## Ed25519 Megolm signing key pair 
Kiedy nadawca tworzy sesję Megolm, tworzy również inną parę kluczy podpisujących Ed25519.
Służy do podpisywania wiadomości wysyłanych za pośrednictwem tej sesji Megolm w celu uwierzytelnienia nadawcy.
Po raz kolejny prywatna część klucza pozostaje na urządzeniu. Część publiczna jest współdzielona z innymi urządzeniami w pokoju wraz z kluczem szyfrującym

# **Inne protokoły wykorzystywane w Matrixie**
## WebRTC (Web Real-Time Communication)
Wolny i otwartoźródłowy projekt, część standardu HTML5 zapewniająca przeglądarkom internetowym oraz aplikacjom mobilnym możliwość komunikacji w czasie rzeczywistym
poprzez zestaw prostych interfejsów programowania (API). Podstawowym celem projektu jest umożliwienie komunikacji audio/video na stronach internetowych poprzez
bezpośrednią komunikację typu peer-to-peer, eliminując w ten sposób potrzebę instalacji wtyczek czy ściągania natywnych aplikacji.
Projekt jest wspierany przez takie firmy jak Apple, Google, Microsoft, Mozilla i Opera.

Główne komponenty WebRTC opierają się. o kilka JavaScript’owych API:

### getUserMedia
Pozyskuje media typu audio i wideo (np. uzyskując dostęp do kamery i mikrofonu urządzenia).
### RTCPeerConnection
Umożliwia komunikację audio i wideo pomiędzy klientami. Obsługuje przetwarzanie sygnału, kodeki, komunikację peer-to-peer, odpowiada za bezpieczeństwo i przepustowość.
### RTCDataChannel 
Umożliwia dwukierunkową komunikację dowolnych danych pomiędzy peerami. Używa tego samego interfejsu API, co WebSocket i ma bardzo niski opóźnienie.
### getStats 
Umożliwia aplikacji internetowej pobieranie zestawu statystyk dotyczących sesji WebRTC. 

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

# **Protokół TURN**
To protokół, który pomaga w przechodzeniu przez translatory adresów sieciowych (NAT) lub zapory sieciowe dla aplikacji multimedialnych.
Może być używany z protokołem kontroli transmisji (TCP) i protokołem datagramów użytkownika (UDP). 
Jest to najbardziej przydatne dla klientów w sieciach zamaskowanych przez symetryczne urządzenia NAT.
TURN nie pomaga w uruchamianiu serwerów na dobrze znanych portach w sieci prywatnej przez NAT;
obsługuje połączenie użytkownika za NAT tylko z jednym peerem, jak na przykład w telefonii.
