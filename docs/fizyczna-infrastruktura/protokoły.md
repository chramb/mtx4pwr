---
title: Wykorzystywane protokoły
---
# **1. Matrix**
![Wizualizacja protokołu](https://yuhu.ddns.net/images/service_matrix_network.png)

Matrix to otwarty standard i protokół komunikacyjny. Ma na celu umożliwienie bezproblemowej komunikacji w czasie rzeczywistym między różnymi dostawcami usług, w taki sam sposób, w jaki standardowa poczta e-mail (**S**imple **M**ail **T**ransfer **P**rotocol) obecnie działa w przypadku usługi przechowywania i przesyłania poczty e-mail, umożliwiając użytkownikom posiadającym konta u jednego dostawcy usług komunikacyjnych komunikowanie się z użytkownikami innego dostawcy usług za pośrednictwem czatu online, Voice over IP i wideotelefonii. Służy zatem podobnemu celowi jak protokoły takie jak XMPP, ale nie jest oparty na żadnym istniejącym protokole komunikacyjnym.

Z technicznego punktu widzenia jest to protokół komunikacyjny warstwy aplikacji do sfederowanej komunikacji w czasie rzeczywistym. Zapewnia interfejsy API HTTP i implementacje referencyjne typu open source do bezpiecznej dystrybucji i utrwalania wiadomości w formacie JSON za pośrednictwem otwartej federacji serwerów. Może integrować się ze standardowymi usługami internetowymi za pośrednictwem WebRTC, ułatwiając aplikacje między przeglądarkami.

# **2. LDAP**
**Protokół LDAP (Lightweight Directory Access Protocol)** definiuje standardową metodę dostępu do informacji i ich aktualizacji w katalogu (bazie danych) lokalnym lub zdalnym w przypadku modelu klient/serwer.

Protokół jest zoptymalizowany pod kątem czytania, przeglądania i wyszukiwania katalogów. Został on początkowo zaprojektowany jako niewymagający protokół dla X.500 Directory Access Protocol. Metoda LDAP jest używana przez klaster hostów w celu umożliwienia scentralizowanego uwierzytelniania oraz dostępu do informacji o użytkownikach i grupach. Ta funkcja jest przeznaczona do użycia w środowisku klastrowym w celu przechowywania informacji o uwierzytelnianiu, użytkownikach i grupach, wspólnych w obrębie klastra.
Obiekty w protokole LDAP są zapisane w hierarchicznej strukturze, znanej jako drzewo informacji katalogu (Directory Information Tree - DIT). Dobry katalog jest uruchamiany ze strukturalnym układem drzewa DIT. Drzewo DIT powinno być starannie zaprojektowane przed zaimplementowaniem protokołu LDAP jako narzędzia uwierzytelniania.

# **3. OAuth 2.0**
OAuth 2.0 jest otwartym protokołem pozwalającym na budowanie bezpiecznych mechanizmów autoryzacyjnych z wykorzystaniem różnych platform, np. aplikacji mobilnych lub WWW, ale również klasycznego oprogramowania. Lepiej oddający realia jest jednak tytuł dokumentu `RFC 6749` zawierającego specyfikację omawianego standardu. Znajduje się tam informacja, że OAuth 2.0 to framework autoryzacyjny („The OAuth 2.0 Authorization Framework”). Słowo „framework” ma tutaj kluczowe znaczenie. W przeciwieństwie do strony projektu nie pojawia się tam stwierdzenie „protokół”. 
Jaka jest różnica? W przypadku protokołu wymagane jest ścisłe trzymanie się zasad określonych w specyfikacji. Podczas studiowania dokumentacji dotyczącej OAuth można zauważyć jednak, że w wielu miejscach specyfikacja luźno narzuca kwestię implementacji danych elementów standardu. Pozostawia to pole do interpretacji, czasem nadmiernej.

Docelowo OAuth 2.0 ma służyć delegacji autoryzacji do zasobów. Właściciel określonego zasobu może udzielić na określony czas oraz w zdefiniowanym z góry zakresie dostępu innemu podmiotowi. Przechodząc od opisów teoretycznych do praktycznego przykładu, można przytoczyć sytuację, w której udzielamy zewnętrznej aplikacji praw do odczytu danych z profilu Google, Facebooka lub Linkedin. Klasyczny scenariusz składa się z następujących kroków:

1. Aplikacja chce uzyskać dane użytkownika, pobierając je z bazy dostawcy tożsamości, w tym celu wykonywane jest przekierowanie do serwera autoryzującego.
2. Serwer autoryzujący przedstawia formularz z informacją o tym, że aplikacja chce uzyskać dostęp do określonych elementów profilu (np. pobrać podstawowe dane personalne oraz adres e-mail).
3. Użytkownik w zależności od tego, czy akceptuje wymagania aplikacji, wydaje jej autoryzację lub nie.
4. W przypadku udzielenia autoryzacji serwer wykonuje przekierowanie z powrotem do aplikacji, a ta otrzymuje specjalny token, za pomocą którego może pobrać wybrane dane z profilu użytkownika.

Głównym celem całego opisanego procesu jest uzyskanie wspomnianego tokenu będącego w większości przypadków wygenerowanym losowo ciągiem znaków o określonej długości. Token przesyłany jest następnie do serwera zasobów. Serwer ten z kolei odbiera go i sprawdza, czy podmiot, który go przedstawia, ma autoryzację do zasobów oraz operacji, które chce wykonać.

# **4. Protokoły szyfrowania używane w Matrixie**

## a) ED25519
To system klucza publicznego oparty na krzywej eliptycznej, powszechnie używany do uwierzytelniania SSH.
Wcześniej klienci EC2 mogli używać kluczy opartych na RSA do uwierzytelniania w instancjach EC2,
gdy potrzebowali nawiązać bezpieczne połączenia w celu wdrożenia instancji w EC2 i zarządzania nimi.

## b) Curve25519 identity key pair
To system kryptograficzny z kluczem publicznym, który można wykorzystać do ustanowienia wspólnego sekretu.
W systemie Matrix każde urządzenie ma długowieczny klucz tożsamości Curve25519, który jest używany do nawiązywania sesji Olm z tym urządzeniem.
Klucz prywatny nigdy nie powinien opuszczać urządzenia, ale część publiczna jest podpisana kluczem linii papilarnych Ed25519 i opublikowana w sieci.

## c) Curve25519 one-time keys
Oprócz klucza tożsamości każde urządzenie tworzy pewną liczbę par kluczy Curve25519, które są również używane do ustanawiania sesji Olm, ale mogą być użyte tylko raz.
Po raz kolejny część prywatna pozostaje na urządzeniu. Podczas uruchamiania Alice tworzy pewną liczbę jednorazowych par kluczy i publikuje je na swoim serwerze domowym.
Jeśli Bob chce nawiązać sesję Olma z Alicją, musi odebrać jeden z kluczy jednorazowych Alicji i utworzyć nowy własny.
Te dwa klucze, wraz z kluczami tożsamości Alicji i Boba, są używane do ustanowienia sesji Olm między Alicją i Bobem.

## d) Megolm encryption keys 
Klucz Megolm służy do szyfrowania wiadomości grupowych (w rzeczywistości służy do uzyskiwania klucza AES-256 i klucza HMAC-SHA-256).
Jest inicjowany losowymi danymi. Za każdym razem, gdy wiadomość jest wysyłana, na kluczu Megolm wykonywane jest obliczenie skrótu,
aby uzyskać klucz dla następnej wiadomości. W związku z tym możliwe jest udostępnienie bieżącego stanu klucza Megolm użytkownikowi,
co pozwala mu odszyfrować przyszłe wiadomości, ale nie przeszłe wiadomości.

## e) Ed25519 Megolm signing key pair 
Kiedy nadawca tworzy sesję Megolm, tworzy również inną parę kluczy podpisujących Ed25519.
Służy do podpisywania wiadomości wysyłanych za pośrednictwem tej sesji Megolm w celu uwierzytelnienia nadawcy.
Po raz kolejny prywatna część klucza pozostaje na urządzeniu. Część publiczna jest współdzielona z innymi urządzeniami w pokoju wraz z kluczem szyfrującym

# **5. Inne protokoły wykorzystywane w Matrixie**
## A) WebRTC (Web Real-Time Communication)
Wolny i otwartoźródłowy projekt, część standardu HTML5 zapewniająca przeglądarkom internetowym oraz aplikacjom mobilnym możliwość komunikacji w czasie rzeczywistym
poprzez zestaw prostych interfejsów programowania (API). Podstawowym celem projektu jest umożliwienie komunikacji audio/video na stronach internetowych poprzez
bezpośrednią komunikację typu peer-to-peer, eliminując w ten sposób potrzebę instalacji wtyczek czy ściągania natywnych aplikacji.
Projekt jest wspierany przez takie firmy jak Apple, Google, Microsoft, Mozilla i Opera. 
Na obrazku przedstawiony jest schemat działania WebRTC:
![WeBRTC](https://cdn.ttgtmedia.com/rms/onlineimages/how_webrtc_works-f_mobile.png)

## B) HTTP (ang. Hypertext Transfer Protocol)
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

## C) TLS (ang. Transport Layer Security)
TLS to protokół kryptograficzny, który zapewnia kompleksowe bezpieczeństwo danych przesyłanych między aplikacjami przez Internet.
Protokół ten przyjęto jako standardowe rozwinięcie protokołu SSL. TLS jest znany użytkownikom w formie ikony kłódki wyświetlanej w przeglądarkach 
internetowych po ustanowieniu bezpiecznej sesji. Certyfikat TSL może być również wykorzystywany do innych aplikacji, takich jak poczta email,
przesyłanie plików, prowadzenia konferencji, komunikatorów internetowych i VoIP, a także do usług internetowych, takich jak DNS i NTP.
Na obrazku poniżej przedstawiona jest zasada działania najnowszej wersji protokołu TLS 1.3.
![TLS 1.3](https://cdn.ttgtmedia.com/rms/onlineimages/security-tls_1.3_handshake-h.png)

# **6. Protokół TURN**
To protokół, który pomaga w przechodzeniu przez translatory adresów sieciowych (NAT) lub zapory sieciowe dla aplikacji multimedialnych.
Może być używany z protokołem kontroli transmisji (TCP) i protokołem datagramów użytkownika (UDP). 
Jest to najbardziej przydatne dla klientów w sieciach zamaskowanych przez symetryczne urządzenia NAT.
TURN nie pomaga w uruchamianiu serwerów na dobrze znanych portach w sieci prywatnej przez NAT;
obsługuje połączenie użytkownika za NAT tylko z jednym peerem, jak na przykład w telefonii.
