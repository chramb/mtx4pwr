---
title: Produkt Końcowy
---
Usługa internetowa dostępna dla studentów i pracowników Politechniki Wrocławskiej oparta na chmurze zdalnej lub lokalnej, komunikacji z wykorzystaniem różnych multimediów tj. obrazy, wiadomości głosowe, filmy video, czat, lub nawet możliwości rozmów głosowych z pomocą protokołu WebRTC.

Zintegrowany z jak największą ilością usług już dostępnych na politechnice.

# Serwer/-y Matrix (Synapse)
Hostowany na politechnice jeden lub więcej serwerów *(ze względu na zdecentralizowaną naturę protokołu możliwym byłoby stworzenie instancji dla każdego wydziału osobno, jednak w celu uproszczenia implementacji ten projekt tego nie obejmie)* Synapse, które pozwolą użytkownikom na połączenie się i komunikowanie z wykorzystaniem protokołu Matrix na politechnice jak i z serwerami poza nią.

# Klient (Riot/Element)
Flagowa implementacja klienta protokołu zostanie hostowana w celu ułatwienia studentom i pracownikom korzystanie z komunikatora bez potrzeby instalacji aplikacjo

# Bridge
Mosty między aktualnie wykorzystywanymi usługami, a protokołem i komunikatorem. W zależności od czasu i zasobów zostanie zintegrowana jak największa ilość.

# Autentykacja Użytkowników
Wykorzystany zostanie protokół LDAP lub OAuth2 w zależności od ograniczeń i zabezpieczeń nałożonych na konta politechniki. Pozwoliło by to na wykorzystanie aktualnie istniejących kont użytkowników oraz jeszcze mocniejszą integrację z istniejącymi usługami
