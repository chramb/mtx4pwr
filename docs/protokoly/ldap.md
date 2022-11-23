---
title: LDAP
---
**Protokół LDAP (Lightweight Directory Access Protocol)** definiuje standardową metodę dostępu do informacji i ich aktualizacji w katalogu (bazie danych) lokalnym lub zdalnym w przypadku modelu klient/serwer.

Protokół jest zoptymalizowany pod kątem czytania, przeglądania i wyszukiwania katalogów. Został on początkowo zaprojektowany jako niewymagający protokół dla X.500 Directory Access Protocol. Metoda LDAP jest używana przez klaster hostów w celu umożliwienia scentralizowanego uwierzytelniania oraz dostępu do informacji o użytkownikach i grupach. Ta funkcja jest przeznaczona do użycia w środowisku klastrowym w celu przechowywania informacji o uwierzytelnianiu, użytkownikach i grupach, wspólnych w obrębie klastra.
Obiekty w protokole LDAP są zapisane w hierarchicznej strukturze, znanej jako drzewo informacji katalogu (Directory Information Tree - DIT). Dobry katalog jest uruchamiany ze strukturalnym układem drzewa DIT. Drzewo DIT powinno być starannie zaprojektowane przed zaimplementowaniem protokołu LDAP jako narzędzia uwierzytelniania.
