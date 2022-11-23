---
title: OAuth 2.0
---
OAuth 2.0 jest otwartym protokołem pozwalającym na budowanie bezpiecznych mechanizmów autoryzacyjnych z wykorzystaniem różnych platform, np. aplikacji mobilnych lub WWW, ale również klasycznego oprogramowania. Lepiej oddający realia jest jednak tytuł dokumentu `RFC 6749` zawierającego specyfikację omawianego standardu. Znajduje się tam informacja, że OAuth 2.0 to framework autoryzacyjny („The OAuth 2.0 Authorization Framework”). Słowo „framework” ma tutaj kluczowe znaczenie. W przeciwieństwie do strony projektu nie pojawia się tam stwierdzenie „protokół”. 
Jaka jest różnica? W przypadku protokołu wymagane jest ścisłe trzymanie się zasad określonych w specyfikacji. Podczas studiowania dokumentacji dotyczącej OAuth można zauważyć jednak, że w wielu miejscach specyfikacja luźno narzuca kwestię implementacji danych elementów standardu. Pozostawia to pole do interpretacji, czasem nadmiernej.

Docelowo OAuth 2.0 ma służyć delegacji autoryzacji do zasobów. Właściciel określonego zasobu może udzielić na określony czas oraz w zdefiniowanym z góry zakresie dostępu innemu podmiotowi. Przechodząc od opisów teoretycznych do praktycznego przykładu, można przytoczyć sytuację, w której udzielamy zewnętrznej aplikacji praw do odczytu danych z profilu Google, Facebooka lub Linkedin. Klasyczny scenariusz składa się z następujących kroków:

1. Aplikacja chce uzyskać dane użytkownika, pobierając je z bazy dostawcy tożsamości, w tym celu wykonywane jest przekierowanie do serwera autoryzującego.
2. Serwer autoryzujący przedstawia formularz z informacją o tym, że aplikacja chce uzyskać dostęp do określonych elementów profilu (np. pobrać podstawowe dane personalne oraz adres e-mail).
3. Użytkownik w zależności od tego, czy akceptuje wymagania aplikacji, wydaje jej autoryzację lub nie.
4. W przypadku udzielenia autoryzacji serwer wykonuje przekierowanie z powrotem do aplikacji, a ta otrzymuje specjalny token, za pomocą którego może pobrać wybrane dane z profilu użytkownika.

Głównym celem całego opisanego procesu jest uzyskanie wspomnianego tokenu będącego w większości przypadków wygenerowanym losowo ciągiem znaków o określonej długości. Token przesyłany jest następnie do serwera zasobów. Serwer ten z kolei odbiera go i sprawdza, czy podmiot, który go przedstawia, ma autoryzację do zasobów oraz operacji, które chce wykonać.
