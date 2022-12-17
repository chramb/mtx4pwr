---
title: Opis Technologii
---
# Matrix
<img src="https://yuhu.ddns.net/images/service_matrix_network.png" alt="Wizualizacja Protokołu">

Matrix to otwarty standard i protokół komunikacyjny. Ma na celu umożliwienie bezproblemowej komunikacji w czasie rzeczywistym między różnymi dostawcami usług, w taki sam sposób, w jaki standardowa poczta e-mail (**S**imple **M**ail **T**ransfer **P**rotocol) obecnie działa w przypadku usługi przechowywania i przesyłania poczty e-mail, umożliwiając użytkownikom posiadającym konta u jednego dostawcy usług komunikacyjnych komunikowanie się z użytkownikami innego dostawcy usług za pośrednictwem czatu online, Voice over IP i wideotelefonii. Służy zatem podobnemu celowi jak protokoły takie jak XMPP, ale nie jest oparty na żadnym istniejącym protokole komunikacyjnym.

Z technicznego punktu widzenia jest to protokół komunikacyjny warstwy aplikacji do sfederowanej komunikacji w czasie rzeczywistym. Zapewnia interfejsy API HTTP i implementacje referencyjne typu open source do bezpiecznej dystrybucji i utrwalania wiadomości w formacie JSON za pośrednictwem otwartej federacji serwerów. Może integrować się ze standardowymi usługami internetowymi za pośrednictwem WebRTC, ułatwiając aplikacje między przeglądarkami.


# LDAP
**Protokół LDAP (Lightweight Directory Access Protocol)** definiuje standardową metodę dostępu do informacji i ich aktualizacji w katalogu (bazie danych) lokalnym lub zdalnym w przypadku modelu klient/serwer.

Protokół jest zoptymalizowany pod kątem czytania, przeglądania i wyszukiwania katalogów. Został on początkowo zaprojektowany jako niewymagający protokół dla X.500 Directory Access Protocol. Metoda LDAP jest używana przez klaster hostów w celu umożliwienia scentralizowanego uwierzytelniania oraz dostępu do informacji o użytkownikach i grupach. Ta funkcja jest przeznaczona do użycia w środowisku klastrowym w celu przechowywania informacji o uwierzytelnianiu, użytkownikach i grupach, wspólnych w obrębie klastra.
Obiekty w protokole LDAP są zapisane w hierarchicznej strukturze, znanej jako drzewo informacji katalogu (Directory Information Tree - DIT). Dobry katalog jest uruchamiany ze strukturalnym układem drzewa DIT. Drzewo DIT powinno być starannie zaprojektowane przed zaimplementowaniem protokołu LDAP jako narzędzia uwierzytelniania.


# OAuth 2.0
OAuth 2.0 jest otwartym protokołem pozwalającym na budowanie bezpiecznych mechanizmów autoryzacyjnych z wykorzystaniem różnych platform, np. aplikacji mobilnych lub WWW, ale również klasycznego oprogramowania. Lepiej oddający realia jest jednak tytuł dokumentu `RFC 6749` zawierającego specyfikację omawianego standardu. Znajduje się tam informacja, że OAuth 2.0 to framework autoryzacyjny („The OAuth 2.0 Authorization Framework”). Słowo „framework” ma tutaj kluczowe znaczenie. W przeciwieństwie do strony projektu nie pojawia się tam stwierdzenie „protokół”. 
Jaka jest różnica? W przypadku protokołu wymagane jest ścisłe trzymanie się zasad określonych w specyfikacji. Podczas studiowania dokumentacji dotyczącej OAuth można zauważyć jednak, że w wielu miejscach specyfikacja luźno narzuca kwestię implementacji danych elementów standardu. Pozostawia to pole do interpretacji, czasem nadmiernej.

Docelowo OAuth 2.0 ma służyć delegacji autoryzacji do zasobów. Właściciel określonego zasobu może udzielić na określony czas oraz w zdefiniowanym z góry zakresie dostępu innemu podmiotowi. Przechodząc od opisów teoretycznych do praktycznego przykładu, można przytoczyć sytuację, w której udzielamy zewnętrznej aplikacji praw do odczytu danych z profilu Google, Facebooka lub Linkedin. Klasyczny scenariusz składa się z następujących kroków:

1. Aplikacja chce uzyskać dane użytkownika, pobierając je z bazy dostawcy tożsamości, w tym celu wykonywane jest przekierowanie do serwera autoryzującego.
2. Serwer autoryzujący przedstawia formularz z informacją o tym, że aplikacja chce uzyskać dostęp do określonych elementów profilu (np. pobrać podstawowe dane personalne oraz adres e-mail).
3. Użytkownik w zależności od tego, czy akceptuje wymagania aplikacji, wydaje jej autoryzację lub nie.
4. W przypadku udzielenia autoryzacji serwer wykonuje przekierowanie z powrotem do aplikacji, a ta otrzymuje specjalny token, za pomocą którego może pobrać wybrane dane z profilu użytkownika.

Głównym celem całego opisanego procesu jest uzyskanie wspomnianego tokenu będącego w większości przypadków wygenerowanym losowo ciągiem znaków o określonej długości. Token przesyłany jest następnie do serwera zasobów. Serwer ten z kolei odbiera go i sprawdza, czy podmiot, który go przedstawia, ma autoryzację do zasobów oraz operacji, które chce wykonać.

# Szyfrowaniu End-to-End 
Jest to proces dążący przede wszystkim do jednego – szyfrowanie danych w taki sposób, aby były możliwe do odczytu tylko dla końcowych użytkowników. Wszystko odbywa się przy wykorzystaniu generowanych kluczy. Po tym odbywa się łączenie z danymi przed momentem przesłania przez sieć, która nie jest zabezpieczona.
W szyfrowaniu END-TO-END można wymienić trzy typy szyfrowania:

- **kryptografia asymetryczna** – wykorzystywane są dwa klucze: publiczny (do szyfrowania) oraz prywatny (do odszyfrowywania). 
- **kryptografia symetryczna** – w tym przypadku wykorzystywane są również dwa klucze publiczny i prywatny. Dzięki temu dane użytkownika są kodowane i dekodowane. 
- **kryptografia hybrydowa** – pozwala na połączeniu zalet obu systemów, czyli kryptografii symetrycznej i asymetrycznej.

Szyfrowanie end-to-end ma na celu zapobieganie odczytywaniu lub modyfikacji danych przez osoby inne niż przez prawdziwego nadawcę i odbiorcę. Wiadomości są szyfrowane przez nadawcę, ale strona trzecia nie ma możliwości ich odszyfrowania i przechowuje je w postaci zaszyfrowanej. Odbiorcy pobierają zaszyfrowane dane i odszyfrowują je samodzielnie.
Ponieważ żadna osoba trzecia nie może odszyfrować przekazywanych lub przechowywanych danych, firmy stosujące takie szyfrowanie nie są w stanie przekazać władzom treści wiadomości swoich klientów.
W sposobie szyfrowania END-TO-END można zaleźć sporo zalet:

- zapewnia bezpieczeństwo oraz prywatność danych,
- masz pewność, że tylko Ty i osoba z drugiej strony możecie przeczytać wysyłane przez Was treści, 
- pełne szyfrowanie to problem dla przechwytywania przez osoby trzecie twoich wiadomości,
- jeśli osoba trzecia włamie się do systemu i ukradnie Twoje dane, nie będzie w stanie ich odczytać – na danych jest warstwa szyfrowania, która stanowi dodatkowe,
ważne informacje są prywatne i bezpieczne,
- szyfrowanie END-TO-END jest ochroną przed niektórymi cyberatakami (man-in-the-middle, oszustwa phisingowe) – brak możliwości manipulowania wiadomościami.

# Cel w projekcie
Planowane jest wykorzystanie jednego lub więcej powyższych standardów w celu integracji z istniejącymi usługami politechniki (konta wykorzystywane przez [oauth.pwr.edu.pl/](oauth.pwr.edu.pl/) i/lub Google)

