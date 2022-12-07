---
title: Architektura Infrastruktury
---
# Wstęp
Tematem projektu jest wprowadzenie nowego systemu komunikacji na Politechnice Wrocławskiej, 
jest to duża instytucja (Na głównej stronie widnieje informacja o 23 817 studentach oraz 2 198 nauczycielach akademickich) więc implementacja musi być skalowalna. 

Poniżej poszeżono temat oraz zaproponowano najbardziej obiecujące propozycje pomagające wdrożyć protokół matrix na tak dużą skalę w stabilny sposób. 

(Propozycje te obejmują konfiguracje samego programu opisane szczegółowo w [2.5.1 Opis technologii](studium-wykonalnosci/projekt-uslug/opis-technologii.md) oraz [4.4 Wykorzystywane protokoły](protokoly/matrix/index.md), opis konfiguracji serwerów/serera fizycznego opisany jest w [późniejszych częściach](modele-infrastruktury.md).

# Problem
## Synapse: Monolityczny Proces
Referencyjna i najbardziej rozwijana implementacja serwera matrix o nazwie matrix rozpoczęła swoje życie w 2014 jako monolityczna aplikacja napisana w języku Python. Głównym sposobem na zwiększanie jej wydajności stało się cache'owanie informacji w pamięci aby zminimalizować ilość zapytań do bazy danych.

Poniżej można zaobserwować graficzną reprezentację serwera działającego jako monolityczny proces:

<!--![Monolityczny Matrix](synapse-monolith.png)-->
<!-- ![Monolityczny Matrix](https://matrix.org/blog/img/2020-11-03-synapse1.png){ width="450" } -->
<img src="https://matrix.org/blog/img/2020-11-03-synapse1.png" width="400">
# Rozwiązania
## [Dendrite](https://matrix-org.github.io/dendrite/): Alternatywna implementacja serwera
Serwer Domowy Matrix drugiej-generacji napisany w Go. Zbudowany bazując na architekturze mikroserwisów. Zaprojektowany aby działać **wydajnie**, **niezawodnie** oraz **skalowanie**.

Niesty implementacja ta nadal występuje jedynie w fazie beta. Pomimo pozytywnych opinii użytkowników nie chcemy ryzykować stabilności komunikatora więc opcja ta zostanie pominięta na ten czas i może ponownie zostać wzięta pod uwagę gdy wyjdzie ze stanu beta, oraz zostanie przetestowana w większych środowiskach.

## Synapse: Worker Processes
Główny proces pythona jest ograniczony do jednego rdzenia procesora co bardzo ogranicza wydajność procesu, w celu przezwyciężenia tego problemu zdecydowano rodzielić sam serwer na większą ilość procesów (worker'ów). Aby zachować integralność danych funkcjonalność odpowiedzialna za wpisy do bazy danych (postgres) najpierw komunikuje się z cache'ującą bazą (redis) dzięki czemu możliwe jest ograniczenie ciągłych wpisów do bazy danych na dysku oraz zsychronizowanie wpisów z wielu procesów, co pozwala na wyeliminowanie problemów związanych z dwoma procesami chcącymi edytować dane jednocześnie. 

<!-- Poniżej można zaobserwować rozwinięty zbiór usług oraz ich interakcje, dzięki którym można usprawnić skalowalność serwera synapse. -->

<img src="https://matrix.org/blog/img/2020-11-03-synapse3.png" width="400">
<!-- ![Synaplse Pub/Sub Model](https://matrix.org/blog/img/2020-11-03-synapse3.png){ width="450" } -->
<!-- TODO: Naprawić żeby ładnie wyglądało w PDFie
## Duże zużycie zasobów

Warto zaznaczyć, że federacja z większymi serwerami łączy się ze znacznym zwiększeniem zasobów.

Jednym z sgerowanych rozwiązań jest ograniczenie federacji jedynie do wewnętrznych usług lub w przypadku implementacji monolitycznej wyłączenia jej całkowicie
-->
**Materiały referencyjne:**

- [Fakty i Liczby | Politechnika Wrocławska - pwr.edu.pl](https://pwr.edu.pl/uczelnia/informacje-ogolne/fakty-i-liczby)
- [Blog Matrix.org: How we fixed Synapse's scalability!](https://matrix.org/blog/2020/11/03/how-we-fixed-synapses-scalability)
