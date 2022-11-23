---
title: Matrix
---
![Wizualizacja protokołu](https://yuhu.ddns.net/images/service_matrix_network.png)

Matrix to otwarty standard i protokół komunikacyjny. Ma na celu umożliwienie bezproblemowej komunikacji w czasie rzeczywistym między różnymi dostawcami usług, w taki sam sposób, w jaki standardowa poczta e-mail (**S**imple **M**ail **T**ransfer **P**rotocol) obecnie działa w przypadku usługi przechowywania i przesyłania poczty e-mail, umożliwiając użytkownikom posiadającym konta u jednego dostawcy usług komunikacyjnych komunikowanie się z użytkownikami innego dostawcy usług za pośrednictwem czatu online, Voice over IP i wideotelefonii. Służy zatem podobnemu celowi jak protokoły takie jak XMPP, ale nie jest oparty na żadnym istniejącym protokole komunikacyjnym.

Z technicznego punktu widzenia jest to protokół komunikacyjny warstwy aplikacji do sfederowanej komunikacji w czasie rzeczywistym. Zapewnia interfejsy API HTTP i implementacje referencyjne typu open source do bezpiecznej dystrybucji i utrwalania wiadomości w formacie JSON za pośrednictwem otwartej federacji serwerów. Może integrować się ze standardowymi usługami internetowymi za pośrednictwem WebRTC, ułatwiając aplikacje między przeglądarkami.
<!--
# Protokoły szyfrowania używane przez Matrix

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
-->
