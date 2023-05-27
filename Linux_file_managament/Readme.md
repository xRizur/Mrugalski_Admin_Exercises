Kontenery	Dockera
1. Uruchom kontener z serwerem webowym Nginx w taki sposób, aby domyślna
strona startowa podawana była z katalogu /tmp/strona/ (wrzuć tam plik
index.html z dowolnym tekstem). Spraw także, aby kontener został
automatycznie usunięty po jego wyłączeniu i aby nasłuchiwał na porcie 80 i
przyznaj mu maksymalnie 256MB pamięci. Wykonaj to zadanie z linii poleceń,
korzystając z tylko jednego polecenia startowego.
Podpowiedź: musisz posłużyć się  opcjami do montowania katalogów,
wystawiania portów (tutaj być może wystarczy samo -P zamiast -p)

2. Wykonaj backup oryginalnego obrazu kontenera z poprzedniego zadanie w taki
sposób, aby uzyskać plik TGZ, a następnie postaraj się odtworzyć ten backup.
Podpowiedź: poczytaj o opcjach ‘save’ i ‘load’

3. Wykonaj zadanie numer 1 z użyciem pliku Dockerfile.
Podpowiedź: poczytaj w jaki sposób tworzy się taki plik

4. Korzystając z Docker-Compose postaw działającego Wordpressa, składającego
się z serwera Apache z obsługą PHP (znajdź gotowy obraz) i serwera MySQL
(lub MariaDB jeśli lubisz). Zadbaj, aby w przypadku restartu któregoś z serwerów
nie utracić danych należących do Wordpressa.
Podpowiedź: poczytaj o Docker Compose

5. Sprawdź jakie pliki zostały zmienione w kontenerze z MySQL od chwili jego
uruchomienia.
Podpowiedź: użyteczne będzie polecenie ‘diff’

6. Stwórz obraz kontenera uruchamiający skompilowaną aplikację “Hello World”
napisaną w GO na kontenerze bazującym na dystrybucji Alpine, na której nie ma
kompilatora wspomnianego języka. Postaraj się, aby docelowy obraz miał
możliwie niewielki rozmiar. Idealnie byłoby, aby poza czystą dystrybucją znalazła
się tam tylko skompilowana aplikacja.
Podpowiedź: wykorzystaj tzw. multistage-build. W pierwszym kontenerze zbuduj
aplikację, a następnie efekt builda przerzuć  (polecenie COPY wraz z
odpowiednim ‘from’ do kontenera docelowego)

7. Postaw kontener z Apache2 oraz jeden z Nginx. Następnie obok nich uruchom
kontener z ‘Nginx Proxy Manager’. Wykorzystując swoją prawdziwą domenę
spraw, aby pod subdomeną ‘apache’ ładowała się  zawartość pierwszego
kontenera, a pod subdomeną ‘nginx’ tego drugiego. Zadbaj, aby każda ze stron
działała po HTTPS. Spraw, aby oba serwery webowe mogły się komunikować po
prywatnej sieci z Proxy Managerem
Podpowiedź: musisz nauczyć  się jak konfigurować proxy managera. Poczytaj
także jak tworzy się sieć pomiędzy serwerami w Dockerze. Kwestię certyfikatów
SSL proxy manager powinien ogarnąć automatycznie.

8. Wrzuć do działającego kontenera (może to być np. uruchomiony Nginx) plik
‘test.txt’ o dowolnej zawartości, a następnie uruchom powłokę bash/sh/ash na
tym samym kontenerze i za pomocą polecenia ‘cat’ podglądnij zawartość
wrzuconego pliku
Podpowiedź: skorzystaj z poleceń dockera ‘cp’ oraz exec. Przy tym drugim
pamiętaj o alokacji interaktywnego terminala, aby widzieć wpisywane polecenia.

9. Przygotuj własny obraz kontenera z Apache, obsługującym język PHP. Możesz
wykorzystać dowolny obraz czystego systemu jako bazowy (najlepiej Alpine, ale
równie dobrze może to być  Debian, czy Ubuntu jeśli nie zależy Ci na
optymalizacji rozmiaru). Następnie wyślij ten obraz na DockerHuba.
Podpowiedź: musisz założyć konto na DockerHub (darmowe), zalogować  się
tam przez dockera, zbudować  własny obraz, otagować  go i wysłać  (push) na
Huba.

10. Poznaj podstawy korzystania z API Dockera. Używając narzędzia NetCat (apt
install nc) pobierz listę obrazów dostępnych na Twoim serwerze. Zwróć ją w
formacie JSON.
Podpowiedź: komunikację rozpoczniesz poleceniem ‘nc -U /var/run/
docker.sock’. Poczytaj jak korzysta się  z API. Jeśli wolisz, to zamiast NetCata
możesz wykorzystać CURLa z parametrem ‘—unix-socket’.

11. Przygotuj sobie dwie wirtualne maszyny (VPSy) z zainstalowanym dockerem. Na
pierwszym z nich uruchom konfigurację z zadania numer 4. Następnie spróbuj tę
konfigurację  przenieść  na drugi serwer metodą zatrzymania kontenerów,
synchronizacji plików i podniesienia kontenerów na drugim serwerze. Ważne jest,
aby nie utracić żadnych danych należących do Wordpressa (pliki + DB).
Podpowiedź: wykorzystaj polecenia start/stop oraz narzędzie rsync. Ewentualna
trudność polega tutaj na zlokalizowaniu, gdzie fizycznie znajdują  się dane
Dockera, jego kontenery i obrazy.
