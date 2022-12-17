---
title: Środowisko Symulacyjne
---
Jako środowisko symulacyjne obraliśmy chmurę *Oracle Cloud* ze względu na ich hojną darmową ofertę.
System operacyjny obrany na owej chmurze to `Ubuntu Linux 22.04.1 LTS aarch64` (architektura arm64)
<!--
TODO:

- Oracle Cloud -> Firewall/Ingress
- Nie ma możliwości rejestracji/logowanie ponieważ zintegrowane a ze względów bezpieczeństwa wyłączona
- Konfiguracja aplikowana i trzymana przez ansible
- Środowisko symulacyjne - Docker - takie jak oficjanle (kontenery ale np kubernetes albo openstack)
-->

Głównym narzędziem konfiguracji natomiast zostało ansible ze względu na gotowe skrypty (tzw. playbooki) do konfiguracji serwera domowego Synapse. 
Natomiast same elementy infrastruktury (m.in baza danych, serwer TURN, synapse, klient webowy) będą hostowane z pomocą oprogramowania kontenerazycyjnego Docker. Pomaga ono na izolacje poszczególnych elementów od siebie nawzajem jak i systemu operacyjnego na którym jest stawiany.

Zdecydowaliśmy również na hostowanie Serwera Synapse w monolitycznej konfiguracji ze względu na ograniczoną ilość użytkowników z jakimi będziemy testować.

## Docker

Narzędzie do konteneryzacji które pomaga uniezależnić wersje oraz biblioteki programu od systemu operacyjnego. Wykorzystanie go również niesie za sobą zaletę możliwości korzystania z oficjalnych obrazów twórców serwera synapse.

## Ansible

Narzędzie do automatyzacji konfiguracji które pozwala na szybkie i automatyczne skonfigurowanie oraz utworzenie i aktualizację aplikacji.

Społeczność Matrixa stworzyła również gotowego tzw. *"playbooka"* czyli kolekcję skryptów która ma za zadanie pomóc i jeszcze bardziej ułatwić konfiguracje serwera.

## Oracle Cloud
Oracle jako firma nie jest znane z przystępności dla konsumenta jednak ich tzw. *"Always Free Tier"* jest największy spośród konkurencji więc postanowiliśmy wykorzystać go do naszych testów symulacyjnych. 

Konto które wykorzystano znajduje się w serwerowni we Frankfurcie.

- **Availability domain:** AD-2
- **Fault domain:** FD-2
- **Region:** eu-frankfurt-1

### Maszyna Wirtualna
Za "kształt" maszyny wirtualnej obrano tzw. `VM.Standard.A1.Flex` Znaczy to iż jest ona skalowalna, oraz wykorzystuje procesor z serii Ampere (architektura Arm).

Liczba procesorów wirtualnych oracle (OCPU) wyniosła: 2

Pamięci ze względu na duże cache'owanie serwera synapse oraz baz danych zarazerwowano: 12 GB

Wraz z tą konfiguracją otrzymano przepustowość równą: 2 Gbps

### System Operacyjny
System operacyjny wybrany do testowania to `Ubuntu Linux 22.04.1 LTS aarch64` zainstalowany z obrazu `Canonical-Ubuntu-22.04-Minimal-aarch64-2022.08.16-0.iso`. Wybrano go ze względu na:

- Dobre wsparcie dockera i innych technologii konteneryzacji
- Wsparcie dla architektury arm
- Długi okres wsparcia tej wersji (nawet do 10 lat)
- Najnowsze dostępne pakiety i biblioteki
- Ponieważ był jedną z niewielu dostępnych za darmo opcji w chmurze oracle
