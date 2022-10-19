---
title: Analiza Ryzyka
---
# Wybór oprogramowania
aktualnie protokół matrix implementowany jest przez 3 różne oprogramowania:
- synapse (python)
- dendrite (golang)
- conduit (rust)

Najbardziej dojrzałym z tych projektów jest serwer synapse, jest on implementowany i rekomendowany jako flagowa implementacja protokołu.

Nie jest on jednak zoptymalizowany pod względem użycia zasobów (duże ilości ramu zostają zużyte jako cache), planowane jest wstępne wprowadzenie samych usług czatowych, a następnie zaimplementowanie usług głosowych w zależności od wyników testów (Zadanie - testowanie usługi)


# Adaptacja Technologii

Protokół Matrix nie jest publicznie znanym protokołem, jednak jest on już zaadoptowany przez wielkie organizacje które wymagają stabilności i przede wszystkim bezpieczeństwa:

- [Blog: Matrix bazą Francuzkiego Rządowego Komunikatora](https://matrix.org/blog/2018/04/26/matrix-and-riot-confirmed-as-the-basis-for-frances-secure-instant-messenger-app)
- [Blog: Niemiecki system opieki zdrowotnej wykorzystuje Matrix'a](https://matrix.org/blog/2021/07/21/germanys-national-healthcare-system-adopts-matrix)

Jego open-source’owa natura sprawia, iż już istneieje więcej niż jedna implementacja na każdą ze spodziewanych platform. 

Brak chęci adaptacji ze strony niektórych platform lub użytkowników może zostać rozwiązany również z pomocą bridge-y które pozwolą na korzystanie ze starszych wcześniej wykorzystywanych technologii lub pozwolą na wykorzystywanie nowych alternatywnych rozwiązań.

Jeśli implementacja protokołu matrix na Politechnice zakończy się sukcesem, ze względu na jego  zdecentralizowaną naturę możliwe byłoby w przyszłości wprowadzenie tych samych technologii na innych uczelniach co pozwoliłoby na bezpieczniejszą i łatwiejszą komunikację między uczelniami

Sam protokół jest wciąż prężnie rozwijany a alternatywne implementacje serwerów wyglądają bardzo obiecująco. Nie uważamy ich za wystarczająco stabilne aby teraz je wykorzystać jednak w przyszłości administrowanie i korzystanie z usług bazujących na nich będzie szybsze i łatwiejsze.

