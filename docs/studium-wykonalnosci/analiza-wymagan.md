---
title: Analiza Wymagań
---
# Biznesowe
Politechnika Wrocławska oczekuje stabilnego, bezpiecznego i wygodnego systemu komunikacji na uczelni.
Który aktualnie spełniany jest głównie przez usługę Emil dostarczaną przez firmę Google. Jednak nie jest on jedynym, zajęcia i komunikacja prowadzone są również na platformach:

- [MS Teams](https://www.microsoft.com/pl-pl/microsoft-teams/group-chat-software)
- [Zoom](https://pwr-edu.zoom.us/)
- [Eportal](https://eportal.pwr.edu.pl/)
- [JSOS](https://jsos.pwr.edu.pl)
- [USOS](https://usos.pwr.edu.pl)
- [edukacja.cl](https://edukacja.pwr.wroc.pl)
- [Mattermost](https://mattermost.com)

Proponowana alternatywa umożliwiała by integrację z częścią, a w przyszłości możliwe że i z wszystkimi z używanych usług. Wykorzystując tzw. [*Bridge*](https://matrix.org/bridges/) oraz zapewniając wyższy standard bezpieczeństwa i prywatności.

Wprowadzenie protokołu Matrix pozwoliłoby na zwiększenie bezpieczeństwa oraz komfortu komunikacji na uczelni oraz pozwoliłoby na stopniowe skonsolidowanie lub całkowite zastąpienie aktualnie używanych rozwiązań.

Protokół ten był już wykorzystywany w projektach na dużą skalę. Oraz ma wielu proponentów w sferze Open Source co powoduje prężny rozwój aplikacji z nim związanych jak i technologii usprawniających automatyzację oraz zarządzanie samymi usługami.

# Użytkowe
<!-- Żeby się łatwo używało i było wygodniejsze -->
Aktualny sposób komunikacji na Politechnice pozostawia wiele do życzenia. Poczynając od informowania użytkowników przez jedną platformę że dostali powiadomienie na innej. A kończąc na zmuszanie studentów do pobierania i korzystania z wielu nieraz nieintuicyjnych aplikacji (jeśli takowe w ogóle istnieją na daną platformę).

Proponowana technologia pozwoliłaby na korzystanie z wielu [istniejących już komunikatorów](https://matrix.org/clients/) na wszystkie oczekiwane platformy (Web, Android, IOS, MacOS, Windows, Linux). Ponadto pozwoliłaby na tworzenie grup studenckich i zniwelowała potrzebę korzystania z zewnętrznych platform np. Discord, Slack, Facebook Messenger

# Techniczne

Od strony technicznej projekt będzie wymagał lokalnego serwera lub usług chmurowych ze stałym połączeniem internetowym pozwalającym na hostowanie:

- Cache danych - Redis
- Bazy danych - Postgresql
- Serwera Matrix - Synapse, Dendrite, Conduit

Ponadto potrzebne mogą być dostępy do takich usług Politechniki jak:

- Serwer LDAP
- Domeny Politechniki (`pwr.edu.pl` lub innej)
- OAuth/OpenID
